# Deploy the Device NFT

To integrate a DePIN project with the IoTeX ioID module, the project owner starts by deploying "**Device NFT**" contract to tokenize each device within their project.&#x20;

{% hint style="info" %}
While the contract is required to implement the ERC-721 Non-Fungible Token standard, the ioID framework does not impose specific implementation requirements, allowing for project-specific customization.&#x20;
{% endhint %}

A user who owns a device NFT from a DePIN project is entitled to register a new ioID identity for a physical device and bind it to their blockchain wallet. When a new ioID is registered for a device, an ioID NFT is minted to the owner's wallet, and the corresponding device NFT is transferred to the ERC-6551 wallet of the ioID. This process effectively "activates" the ioID, linking the physical device to its digital identity and to its owner on the blockchain.&#x20;

Below is an example NFT contract that can be used as a Device NFT by a DePIN project:

<details>

<summary>Example Device NFT Contract</summary>

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract DeviceNFT is ERC721, Ownable {
    event MinterConfigured(address indexed minter, uint256 minterAllowedAmount);
    event MinterRemoved(address indexed minter);

    mapping(address => bool) internal minters;
    mapping(address => uint256) internal minterAllowed;
    uint256 nextId;

    constructor() ERC721("Example Device NFT", "EDN") {}

    function minterAllowance(address minter) external view returns (uint256) {
        return minterAllowed[minter];
    }

    function isMinter(address account) external view returns (bool) {
        return minters[account];
    }

    function configureMinter(address _minter, uint256 _minterAllowedAmount) external onlyOwner {
        minters[_minter] = true;
        minterAllowed[_minter] = _minterAllowedAmount;
        emit MinterConfigured(_minter, _minterAllowedAmount);
    }

    function removeMinter(address _minter) external onlyOwner {
        minters[_minter] = false;
        minterAllowed[_minter] = 0;
        emit MinterRemoved(_minter);
    }

    function mint(address _to) external returns (uint256) {
        require(_to != address(0), "zero address");

        uint256 mintingAllowedAmount = minterAllowed[msg.sender];
        require(mintingAllowedAmount > 0, "exceeds minterAllowance");
        unchecked {
            minterAllowed[msg.sender] -= 1;
        }

        uint256 _tokenId = ++nextId;
        _mint(_to, _tokenId);
        return _tokenId;
    }
}
```



</details>

{% hint style="info" %}
[Learn how to deploy an NFT token contract on IoTeX](../../../../builders/defi/deploy-tokens/deploy-an-nft-token.md)
{% endhint %}
