# DePIN Incentives Contract

{% hint style="info" %}
This documentation is work in progress.
{% endhint %}

In previous tutorials, we covered how to create the device firmware and how to write and deploy the W3bstream prover logic. In this tutorial, we will take the next step by creating a smart contract that implements basic DePIN incentives for the owners of devices in a DePIN network.

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

// Importing the Risc0 verifier contract interface to verify ZK proofs.
import {IRiscZeroVerifier} from "./IRiscZeroVerifier.sol";

// Importing the JournalParser library to decode reward data from the W3bstream output.
// We use this utility library to parse the Risc0 journal containing an object
// where each name is a device id and each value is the reward. E.g.:
// {"0":45,"3":24,"2":53,"1":62}. 
// Refer to https://github.com/machinefi/iotex-dewi-demo/tree/main/blockchain/contracts/lib
import "./lib/JournalParser.sol";

// Importing the ERC721 interface to interact with the tokenized devices.
// We must interact with our tokenized devices to find their ioID identity.
// In fact, we assume that the W3bstream output returns a custom device id
// and not its DID, for gas efficiency reasons.
import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

// Importing the ioID registry interface to look up device identities.
// We must interact with the ioID registry to find out the ioID identity 
// associated to a given device NFT.
import "./interfaces/IioIDRegistry.sol";

// Importing the ioID contract interface to find device owners.
// We must interact with the ioID contract to look up device owner accounts.
import "./interfaces/IioID.sol";

// Importing the ERC20 interface to distribute rewards in the form of tokens.
// We need to interact with our ERC20 token and distribute the incentives.
import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

// Importing the Ownable contract to manage ownership and administrative functions.
// Let's make our contract ownable.
import "@openzeppelin/contracts/access/Ownable.sol";

contract DePINDappContract is Ownable {
    // This will hold the reference to the Risc0 Verifier contract.
    IRiscZeroVerifier private verifier;
    // This will hold the reference to the ioID NFT identity contract.
    IioID public ioID;
    // This will hold the reference to the ioID registry contract.
    IioIDRegistry public ioIDRegistry;
    // This will hold the reference to our DePIN token to distribute rewards.
    IERC20 private token;

    // Event emitted when a proof is successfully verified.
    event ProofVerified(address sender, bytes32 imageId, bytes32 postStateDigest);
    // Event emitted when rewards are distributed.
    event RewardsDistributed(address receiver, uint256 amount);

    // Constructor to initialize the contract with the necessary addresses.
    constructor(
        address _verifierAddress,
        address _tokenAddress,
        address _ioIDAddress,
        address _ioIDRegistryAddress
    ) {
        verifier = IRiscZeroVerifier(_verifierAddress);
        ioID = IioID(_ioIDAddress);
        ioIDRegistry = IioIDRegistry(_ioIDRegistryAddress);
        token = IERC20(_tokenAddress);
    }

    // Function to verify the ZK proof and distribute rewards based on the journal data.
    function verifyAndExecute(
        bytes calldata seal,
        bytes32 imageId,
        bytes32 postStateDigest,
        bytes memory journal
    ) external {
        // Verify the ZK proof using the Risc0 verifier contract.
        require(verifier.verifySnark(seal, imageId, postStateDigest, journal), "Proof verification failed.");
        emit ProofVerified(msg.sender, imageId, postStateDigest);

        // Decode the deviceID-rewards mapping from the journal data.
        // (JournalParser.Device[] memory devices, uint256 devicesLen) = JournalParser.parseDeviceJson(journal);
        // JournalParser provides an example implementation of how to parse the journal
        // Refer to https://github.com/machinefi/iotex-dewi-demo/blob/main/blockchain/contracts/lib/JournalParser.sol
        (JournalParser.Device[] memory devices, uint256 devicesLen) = JournalParser.parseDeviceJson(journal);

        // Distribute rewards to the owners of the devices.
        _distributeRewards(devices, devicesLen);
    }

    // Internal function to distribute rewards to device owners.
    function _distributeRewards(JournalParser.Device[] memory devices, uint256 devicesLen) internal {
        for (uint256 i = 0; i < devicesLen; i++) {
            uint256 deviceId = devices[i].id;

            // Get the ioID token ID associated with the device ID.
            uint256 ioIDTokenId = ioIDRegistry.deviceTokenId(deviceId);

            // Get the owner of the ioID token ID.
            address owner = ioID.ownerOf(ioIDTokenId);

            // Transfer the reward amount to the device owner.
            require(token.transfer(owner, devices[i].reward), "Token transfer failed");
            emit RewardsDistributed(owner, devices[i].reward);
        }
    }

    // Function to update the verifier contract address (only callable by the owner).
    function updateVerifierAddress(address newVerifierAddress) external onlyOwner {
        verifier = IRiscZeroVerifier(newVerifierAddress);
    }

    // Function to update the token contract address (only callable by the owner).
    function updateTokenAddress(address newTokenAddress) external onlyOwner {
        token = IERC20(newTokenAddress);
    }
}

```
