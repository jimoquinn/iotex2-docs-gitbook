# DePIN Incentives Contract

{% hint style="info" %}
This documentation is being updated.
{% endhint %}

Welcome back to our series on building a Decentralized WiFi network. In previous tutorials, we covered how to create the device firmware and how to write and deploy the W3bstream prover logic. In this tutorial, we will take the next step by creating a smart contract that implements basic DePIN incentives for the owners of devices in a DePIN network.

## **Assumptions**

1. **Device Types:** The devices in this tutorial are WiFi access points.
2. **Identity Registration:** Both the devices and their owners have their identities registered in the IoTeX [ioid-depin-identities](../../../depin-infra-modules-dim/ioid-depin-identities/ "mention")module.
3. **Device Messages:** These devices send messages about their online status and the number of clients they have served. These messages are processed by a Risc0 ZK prover using W3bstream to determine the amount of rewards to be distributed per device.
4. A DePIN ERC20 token to be used for incentivising device owners is already deployed.
5. **Proof Verification and Reward Distribution:** The processed results and their ZK proofs are sent to our smart contract, which will verify the proof, lookup device owners in the ioID registry, and distribute the rewards as verifiably computed by W3bstream.

## The code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

// We must interact with the Risc0 verifier contract on IoTeX to verify
//  the proof that rewards computation was performed by our logic. 
import {IRiscZeroVerifier} from "./IRiscZeroVerifier.sol";

// We use this utility library to parse the Risc0 journal containing an object
// where each name is a device id and each value is the reward. E.g.:
// {"0":45,"3":24,"2":53,"1":62}. 
// Refer to https://github.com/machinefi/iotex-dewi-demo/tree/main/blockchain/contracts/lib
import "./lib/JournalParser.sol";

// We must interact with our tokenized devices to find their ioID identity.
// In fact, we assume that the W3bstream output returns a custom device id
// and not it's DID, for gas efficiency reason.
import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

// We must interact with the ioID registry to find out the ioID identity 
// assocciated to a given device NFT
import "./interfaces/IioIDRegistry.sol";

// We must interact with the ioID contract to look up device owner accounts
import "./interfaces/IioID.sol";

// We need to interact with our ERC20 token and distribute the incentives
import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

// Let's make our contract ownable
import "@openzeppelin/contracts/access/Ownable.sol";

contract DePINDappContract is Ownable {
    // This will hold the reference to the Risc0 Verifier contract
    IRiscZeroVerifier private verifier;
    // This will hold the reference to the ioID NFT identity contract
    IioID public ioID;
    // This will hold the reference to the ioID registry contract
    IioIDRegistry public ioIDRegistry;
    // This will hold the reference to our DePIN token to distribute rewards
    IERC20 private token;
    
    
    event ProofVerified(address sender, bytes32 imageId, bytes32 postStateDigest);
    event RewardsDistributed(address receiver, uint256 amount);
    
    constructor(address _verifierAddress, address _tokenAddress, address ioIDAddress,
      address _ioIDRegistryAddress) {
        verifier = IRiscZeroVerifier(_verifierAddress);
        ioID = IioID(_ioIDAddress);
        ioIDRegistry = IioIDRegistry(_ioIDRegistryAddress);
        token = IERC20(_tokenAddress);
    }
    
    function verifyAndExecute(
        bytes calldata seal,
        bytes32 imageId,
        bytes32 postStateDigest,
        bytes memory journal
    ) external {
        // First verify the W3bstream proof
        require(verifier.verifySnark(seal, imageId, postStateDigest, journal), "Proof verification failed.");
        emit ProofVerified(msg.sender, imageId, postStateDigest);
        // NExt, extract the deviceID-rewards mapping from the computation output
        address[] memory recipients = _decodeJournal(journal);
        // start the rewards distribution
        _distributeRewards(recipients);
    }
    
    function _distributeRewards(address[] memory recipients) internal {
        // Assuming reward is 1 token, with 18 decimals
        uint256 rewardAmount = 1 * 10 ** 18; 
        
        for (uint256 i = 0; i < recipients.length; i++) {
            require(token.transfer(recipients[i], rewardAmount), "Token transfer failed");
            emit RewardsDistributed(recipients[i], rewardAmount);
        }
    }
    
    function _decodeJournal(bytes memory journal) internal pure returns (address[] memory) {
        // Assuming the journal contains addresses encoded as 20-byte sequences.
        uint256 numRecipients = journal.length / 20;
        address[] memory recipients = new address[](numRecipients);
        for (uint256 i = 0; i < numRecipients; i++) {
            address recipient;
            assembly {
                recipient := mload(add(add(journal, 20), mul(i, 20)))
            }
            recipients[i] = recipient;
        }
        return recipients;
    }
    
    function updateVerifierAddress(address newVerifierAddress) external onlyOwner {
        verifier = IRiscZeroVerifier(newVerifierAddress);
    }
    
    function updateTokenAddress(address newTokenAddress) external onlyOwner {
        token = IERC20(newTokenAddress);
    }
}
```
