# Deploy an NFT Token

If you’re already familiar with deploying ERC20 tokens, you’ll find that deploying NFTs is quite similar in terms of the process, but with some key differences in the contract structure.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract ExampleNFT is ERC721, Ownable {
    uint256 private _tokenIdCounter;

    constructor() ERC721("ExampleNFT", "ENFT") {
        _tokenIdCounter = 0;
    }

    function mint(address to) external onlyOwner {
        _mint(to, _tokenIdCounter);
        _tokenIdCounter++;
    }

    function totalSupply() public view returns (uint256) {
        return _tokenIdCounter;
    }
}
```

{% hint style="success" %}
#### Steps to Deploy

The steps to deploy this NFT contract are very similar to the ERC20 token deployment you’ve already seen in the previous section. For a detailed guide on setting up your environment, compiling the contract, deploying, and interacting with it, please refer to the [ERC20 Deployment Guide](deploy-an-erc20-token.md).
{% endhint %}

## Code Explanation

**Imports:**

* The contract imports the `ERC721` and `Ownable` contracts from OpenZeppelin, providing basic NFT functionality and ownership control.

**Constructor:**

* The constructor initializes the NFT with a name ("ExampleNFT") and symbol ("ENFT"). It also sets the initial token counter to 0.

**Mint Function:**

* The `mint` function allows the owner (i.e., the account that deployed the contract) to mint a new NFT. Each minted NFT gets a unique token ID, which starts from 0 and increments for each new mint.

**totalSupply Function:**

* The `totalSupply` function provides a simple way to track how many NFTs have been minted by returning the current value of `_tokenIdCounter`.

This example contract follows the basic principles of ERC721, allowing the contract owner to mint unique NFTs and track their total supply.
