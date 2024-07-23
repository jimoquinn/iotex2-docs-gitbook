# Metamask Desktop

[MetaMask](https://metamask.io) is a popular Ethereum wallet and gateway to blockchain apps which can also be configured to work with the IoTeX network. This allows users to manage their IOTX tokens and interact with IoTeX's decentralized applications (DApps) directly through MetaMask. This document outlines the simple steps to add the IoTeX blockchain configuration to MetaMask, both manually and automatically.

## Prerequisites

* **MetaMask Wallet**: You need to have the [MetaMask extension installed](https://metamask.io/download/) on your web browser

{% hint style="success" %}
&#x20;**Install Metamask**

\-> Visit [https://metamask.io](https://metamask.io)
{% endhint %}

## Adding IoTeX to MetaMask

After MetaMask is installed in your browser, it comes pre-configured to connect to the Ethereum blockchain. However, you can easily add configurations for additional blockchains to use it across multiple networks, including IoTeX. You can do this either by entering the blockchain network configuration details manually or by using the links provided on the IoTeX Developer Portal.

### Automatic Configuration

For a simpler and error-free setup, you can automatically configure MetaMask to add the IoTeX network:

[-> Visit the IoTeX tools page](https://developers.iotex.io/dev-tools?tool=network-config)

### Manual Configuration

Follow these steps to manually add the IoTeX network to MetaMask:

1. **Open MetaMask**: Launch the MetaMask extension or app.
2. **Access Network Selection**: Click on the network dropdown menu at the top of the app (defaulted to Ethereum Mainnet).
3. **Add Network**: Select "Add Network" or "Custom RPC" at the bottom of the network list.

<figure><img src="../../../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

1. **Enter IoTeX Network Details**: Input the following network configuration details:
   * **Network Name**: IoTeX Mainnet
   * **New RPC URL**: `https://babel-api.mainnet.iotex.io`
   * **Chain ID**: `4689`
   * **Currency Symbol**: IOTX
   * **Block Explorer URL**: `https://iotexscan.io`
2. **Save**: Click "Save" to add the IoTeX network to your MetaMask wallet.

{% hint style="info" %}
Check out the [rpc-endpoints.md](../../../../builders/web3-development/rpc-endpoints.md "mention") page for updated RPC endpoints for The IoTeX Mainnet and Testnet
{% endhint %}
