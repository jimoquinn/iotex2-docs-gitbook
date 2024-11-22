# ioID Step by Step Tutorial

This tutorial demonstrates how to integrate ioID into your DePIN project and is divided into two parts:

1\. **Project Registration** on the IoTeX blockchain, explained in this page.

2\. **Device Registration**, which varies based on the scenario and may involve integrating ioID either directly on the device or in the cloud. Both cases are described in the next pages.

<details>

<summary>Prerequisites</summary>

Before you begin working with the IoTeX blockchain and related tools, follow these preliminary steps to set up your development environment.

### Tools

Ensure you have the following tools installed:

* [ioctl](https://docs.iotex.io/builders/reference-docs/ioctl-client#install-latest-release-build): For interacting with the IoTeX blockchain.
* [curl](https://curl.se/): For sending messages to the API node.
* [jq](https://jqlang.github.io/jq/): Optional, to format JSON output.

### Create and fund a Developer wallet

Start by creating an IoTeX developer wallet and funding it with test tokens.

```bash
ioctl account createadd devaccount
```

Note the `0x` wallet address provided.&#x20;

Set ioctl on the IoTeX testnet:

```bash
ioctl config set endpoint api.testnet.iotex.one:443
```

### **Claim test IOTX**

You can claim test IOTX tokens on the IoTeX Developer portal at [https://developers.iotex.io/faucet](https://developers.iotex.io/faucet).

**Configure Metamask**: if you need to configure Metamask with IoTeX for convenience, you can do so on the&#x20;

Check the balance of your wallet with:

```bash
ioctl account balance devaccount
```

If needed, export the private key with:

```
ioctl account export devaccount
```

</details>

## 1. DePIN Project Registration on IoTeX

### Device NFT Contract

Ensure you deployed an ERC721 NFT contract to "tokenize" your devices

{% hint style="success" %}
See how to deploy an NFT Token on IoTeX using Hardhat: [deploy-an-nft-token.md](../../defi/deploy-tokens/deploy-an-nft-token.md "mention")
{% endhint %}

**and note the deployed contract address.**

For a quicker option, you can deploy a standard NFT contract using its bytecode with the following ioctl command:

```bash
ioctl contract deploy bytecode $(curl -s https://gist.githubusercontent.com/simonerom/fd7427cd821408a5e49f4c4e81b16fb9/raw/device-nft-bytecode.hex)
```

Check the transaction link to find the address of the contract just deployed.

We will refer to this contract as the "_Device NFT_" from now on. Let's also export the contract address for convenience:

```bash
export DEVICE_NFT=0x...
```

### Register your project on IoTeX

```bash
ioctl ioid register "MY_COOL_DEPIN_PROJECT_NAME"
```

Take note of your `Project ID` and set it as an environment variable:

```bash
export PROJECT_ID=YOUR_PROJECT_ID
```

Bind the Device NFT to your Project ID

```
ioctl ioid device $DEVICE_NFT -p $PROJECT_ID
```

## 2. Device registration

Depending on the development stage of a DePIN project, there are multiple ways it can integrate ioID for device registration. In the next pages, we share different flows tailored to various use cases.

* [A fully decentralized approach ->](a-fully-decentralized-approach.md)
* [A "proxy contract" approach ->](a-proxy-contract-approach.md)&#x20;
