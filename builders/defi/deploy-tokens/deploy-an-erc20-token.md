# Deploy an ERC20 Token

## Example contract

Let's start with a simple ERC20 token an example contract:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract ExampleToken is ERC20, Ownable {
    constructor(uint256 initialSupply) ERC20("ExampleToken", "ETK") {
        _mint(msg.sender, initialSupply);
    }

    function mint(address to, uint256 amount) external onlyOwner {
        _mint(to, amount);
    }
}
```

## Code Explanation

**Imports**: The contract imports the `ERC20` and `Ownable` contracts from [OpenZeppelin](https://openzeppelin.com).

**Constructor**: The constructor initializes the token with a name ("ExampleToken") and symbol ("ETK"), and mints the initial supply to the contract deployer.

**Mint Function**: The `mint` function allows the owner (i.e. the account that deployed the contract) to mint additional tokens.

## Deploy using Hardhat

{% hint style="info" %}
[-> Learn more about HardHat](https://hardhat.com)
{% endhint %}

### **Set up the environment**

* [Install Node.js and npm](https://nodejs.org/en/download/package-manager).
* Create a folder for your project: `mkdir ExampleToken && cd ExampleTokem`.
* Install Hardhat: `npm install --save-dev hardhat`.
* Create a new Hardhat project: `npx hardhat`.
* Follow the prompts to set up a basic sample project.

### **Install dependencies**

```bash
npm install @openzeppelin/contracts
npm install --save-dev @nomiclabs/hardhat-ethers ethers
```

### **Update Hardhat Config**

Open `hardhat.config.js` and configure the IoTeX network:

```javascript
require("@nomiclabs/hardhat-ethers");

module.exports = {
  solidity: "0.8.0",
  networks: {
    iotex: {
      url: "https://babel-api.mainnet.iotex.io",
      accounts: [`0x${YOUR_PRIVATE_KEY}`]
    }
  }
};
```

Replace `YOUR_PRIVATE_KEY` with the private key of the account you want to use for deployment.

{% hint style="info" %}
[-> Configure an IoTeX Wallet](../../../depin-infra-modules-dim/iotex-l1-depin-blockchain/wallets/supported-wallet-apps/)

[-> Claim Test IOTX](broken-reference)
{% endhint %}

### **Create the Contract File**

Create a new `contracts` directory and new file `contracts/ExampleToken.sol` and add the ERC20 token contract code [provided above](deploy-an-erc20-token.md#example-contract).

### **Write a Deployment Script**

Create a new directory `scripts` and add a file `deploy.js` with the following content:

```javascript
async function main() {
    const [deployer] = await ethers.getSigners();
    console.log("Deploying contracts with the account:", deployer.address);

    const initialSupply = ethers.utils.parseUnits("1000", 18); // 1000 tokens with 18 decimals
    const Token = await ethers.getContractFactory("ExampleToken");
    const token = await Token.deploy(initialSupply);

    console.log("Token deployed to:", token.address);
}

main()
  .then(() => process.exit(0))
  .catch((error) => {
    console.error(error);
    process.exit(1);
  });
```

### **Deploy the Contract**:

```bash
npx hardhat run scripts/deploy.js --network iotex
```

This setup should provide a comprehensive tutorial on deploying a basic ERC20 token contract on the IoTeX blockchain using HardHat. Make sure to replace `YOUR_PRIVATE_KEY` with your actual development account's private key.&#x20;

## Deploy using Foundry

This quick start guide will help you deploy smart contracts on the IoTeX blockchain using the Foundry suite. Foundry is a fast, portable, and modular toolkit for Ethereum application development written in Rust.

{% hint style="info" %}
[-> Learn more about Foundry](https://getfoundry.sh/)
{% endhint %}

### Setup the Environment

If you haven't installed Foundry, use the following command:

```sh
curl -L https://foundry.paradigm.xyz | bash foundryup
```

### Set Up Your Project

Create a new project directory and navigate into it:

```sh
mkdir ExampleToken && cd ExampleToken
```

Initialize a new Foundry project:

```sh
forge init
```

### Write Your Smart Contract

Navigate to the `src` directory and create a new Solidity file  `ExampleToken.sol` and add the ERC20 token contract code [provided above](deploy-an-erc20-token.md#example-contract).

### Compile Your Smart Contract

Compile the smart contract using Foundry:

```sh
forge build
```

### Configure a Deployment Script

Foundry uses `cast` to interact with the blockchain. Create a `.env` file to store your private key securely:

```sh
echo "PRIVATE_KEY=your_private_key_here" > .env
```

Load the environment variables:

```sh
source .env
```

### Deploy Your Smart Contract

Use the `cast send` command to deploy your contract to the IoTeX testnet. Replace `MyContract` with the name of your compiled contract and adjust the RPC URL if needed.

```sh
cast send --rpc-url https://babel-api.testnet.iotex.io \
  --private-key $PRIVATE_KEY --legacy --create \
  $(cat out/MyContract.sol/MyContract.json | jq -r .bytecode.object)
```

### Verify the Deployment

Once deployed, you will receive a transaction hash. Use this hash to verify the deployment on the IoTeX testnet explorer.

### Example Contract Interaction

After deployment, you can interact with your contract. For example, to call the `setMessage` function:

```sh
cast send --rpc-url https://babel-api.testnet.iotex.io \
  --private-key $PRIVATE_KEY --legacy \
  <contract_address> "setMessage(string)" "Hello, IoTeX!"
```

#### Conclusion

By following this quick start guide, you have successfully deployed a smart contract on the IoTeX blockchain using the Foundry suite. Foundry’s powerful tools make it easy to develop, deploy, and interact with smart contracts on IoTeX. For more advanced features and configurations, refer to the [Foundry documentation](https://book.getfoundry.sh/).

If you have any questions or run into issues, feel free to ask [our community on Discord](https://iotex.io/devdiscord)!
