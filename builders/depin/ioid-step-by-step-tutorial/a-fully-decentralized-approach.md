# A fully decentralized approach

This tutorial demonstrates a fully decentralized method for managing the lifecycle of device identity and ownership using ioID. It provides a practical, hands-on guide featuring an ESP32 board but is easily adaptable to a variety of “machines,” including Linux-based boards, smartphones, and desktop computers.

## 1. Initial setup

Ensure you have completed the steps in the [prerequisites section](./).

## 2. Device NFT Contract

Ensure you deployed an ERC721 NFT contract to "tokenize" your devices

\-> [deploy-an-nft-token.md](../../defi/deploy-tokens/deploy-an-nft-token.md "mention")

**and note the deployed contract address.**

For a quicker option, you can deploy a standard NFT contract using its bytecode with the following ioctl command:

```bash
ioctl contract deploy bytecode $(curl -s https://gist.githubusercontent.com/simonerom/fd7427cd821408a5e49f4c4e81b16fb9/raw/device-nft-bytecode.hex)
```

We will refer to this contract as the "_Device NFT_".

## Register your DePIN project on IoTeX

```bash
ioctl ioid register "PROJECT_UNIQUE_NAME"
```

Take note of your `Project ID` and set it as an environment variable:

```bash
export PROJECT_ID=YOUR_PROJECT_ID
```

Bind the Device NFT to your Project ID

```
ioctl ioid device <NFT_CONTRACT_ADDRESS> -p $PROJECT_ID
```

## Integrate ioConnect in your device

In this step, we will use the popular ESP32 board as our DePIN device and create a simple firmware that enables the device to be registered on-chain by the device owner. This demonstrates the integration of ioConnect with minimal setup, making it a practical and efficient way to securely connect your DePIN devices to your Dapp on the IoTeX blockchain.

{% hint style="info" %}
Below is a flowchart illustrating the basic flow common to most use cases. The process ensures proper device registration at boot and, during normal operation, the device utilizes its DID key to sign messages securely.
{% endhint %}



<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>Basic firmware flow for ioID integration</p></figcaption></figure>

### Prerequisite

Before proceeding, ensure you have an ESP32 toolchain correctly configured on your system. This is essential for building the code and deploying it to your ESP32 board.

For a step-by-step guide on setting up the ESP32 toolchain with VS Code, refer to the tutorial available in this [DePIN demo repository](https://github.com/iotexproject/dewi-demo/tree/main/esp32#setting-up-your-environment).

### Get ioConnect examples

```bash
git clone https://github.com/iotexproject/ioConnect && ioConnect
```

