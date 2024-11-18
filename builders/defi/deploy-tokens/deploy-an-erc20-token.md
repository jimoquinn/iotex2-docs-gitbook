# Deploy an ERC20 Token

## Example contract

Let's start with a simple ERC20 token an example contract:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract ExampleToken is ERC20, Ownable {
    constructor() ERC20("ExampleToken", "ETK") Ownable(msg.sender) {
        _mint(msg.sender, 1000);
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

Ensure you have the latest nodeJS and npm:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
nvm install 22
nvm use 22
nvm alias default 22
npm install npm --global # Upgrade npm to the latest version
```

Create a new Hardhat project:

```bash
mkdir ExampleToken && cd ExampleTokem
npm init
npm install --save-dev hardhat
npx hardhat init
```

### **Install dependencies & Hardhat plugins**

```bash
npm install @openzeppelin/contracts
npm install --save-dev @nomicfoundation/hardhat-toolbox
```

### **Update Hardhat Config**

Open `hardhat.config.js` and configure the IoTeX network:

```javascript
javascript
require("@nomicfoundation/hardhat-toolbox");

/** @type import('hardhat/config').HardhatUserConfig */
module.exports = {
  solidity: "0.8.20",
  networks: {
    testnet: {
      url: "https://babel-api.testnet.iotex.io",
      accounts: [`${TESTNET_PRIVATE_KEY}`]
    },
    mainnet: {
      url: "https://babel-api.testnet.iotex.io",
      accounts: [`${MAINNET_PRIVATE_KEY}`]
    }
  }
};
```

Replace `TESTNET_PRIVATE_KEY` with the private key of the account you want to use for deployment.

{% hint style="info" %}
[-> Configure an IoTeX Wallet](../../../depin-infra-modules-dim/iotex-l1-depin-blockchain/wallets/supported-wallet-apps/)

[→ Request test IOTX tokens ](https://developers.iotex.io/faucet)
{% endhint %}

### **Create the Contract File**

Create a new `contracts` directory and new file `contracts/ExampleToken.sol` and add the ERC20 token contract code [provided above](deploy-an-erc20-token.md#example-contract) (make sure you delete any example contracts already created in the contracts folder).

### **Write an ignition module for Deployment**

Inside the `ignition` folder add a file `ExampleToken.js` with the following content:

```javascript
const { buildModule } = require("@nomicfoundation/hardhat-ignition/modules");
const { parseUnits } = require("ethers"); // Ensure you import parseUnits from ethers

const ExampleTokenModule = buildModule("ExampleTokenModule", (m) => {

  // Deploy the ExampleToken contract with the specified initial supply
  const token = m.contract("ExampleToken");

  return { token };
});

module.exports = ExampleTokenModule;
```

### **Deploy the Contract**

```bash
npx hardhat ignition deploy ./ignition/modules/ExampleToken.js --network testnet
```

This setup should provide a comprehensive tutorial on deploying a basic ERC20 token contract on the IoTeX blockchain using HardHat.&#x20;

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
