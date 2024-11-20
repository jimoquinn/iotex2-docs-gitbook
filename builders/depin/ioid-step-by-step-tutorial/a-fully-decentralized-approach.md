# A fully decentralized approach

This tutorial demonstrates a fully decentralized approach to managing the lifecycle of device identity and ownership in DePINs using ioID. This method aligns perfectly with the principles of a true Web3 project, enabling device owners to independently initiate and complete the registration process without relying on centralized cloud services.

The document offers a practical, hands-on guide featuring an ESP32 board, with instructions that can be easily adapted to a variety of other “machines,” including Linux-based boards, smartphones, and desktop computers.

{% hint style="info" %}
[-> Source code on GitHub.](https://github.com/iotexproject/depin-tutorials/tree/main/esp32-device-registration)
{% endhint %}

## 1. Initial setup

Ensure you have completed the steps in the [prerequisites section](./) to fund an IoTeX developer account.

## 2. Device NFT Contract

Ensure you deployed an ERC721 NFT contract to "tokenize" your devices

{% hint style="success" %}
See how to deploy an NFT Token on IoTeX using Hardhat: [deploy-an-nft-token.md](../../defi/deploy-tokens/deploy-an-nft-token.md "mention")
{% endhint %}

**and note the deployed contract address.**

For a quicker option, you can deploy a standard NFT contract using its bytecode with the following ioctl command:

```bash
ioctl contract deploy bytecode $(curl -s https://gist.githubusercontent.com/simonerom/fd7427cd821408a5e49f4c4e81b16fb9/raw/device-nft-bytecode.hex)
```

We will refer to this contract as the "_Device NFT_" from now on. Let's also export the contract address for convenience:

```bash
export $DEVICE_NFT=0x...
```

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
ioctl ioid device $DEVICE_NFT -p $PROJECT_ID
```

## Integrate ioId-SDK in your device

In this step, we will use the popular ESP32 board as our DePIN device and create a simple firmware that enables the device to be registered on-chain by the device owner. This demonstrates the integration of ioID-SDK with minimal setup, making it a practical and efficient way to securely connect your DePIN devices to your Dapp on the IoTeX blockchain.

{% hint style="info" %}
Below is a flowchart illustrating the basic flow common to most use cases. The process ensures proper device registration at boot and, during normal operation, the device utilizes its DID key to sign messages securely.
{% endhint %}



<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>Basic firmware flow for ioID integration</p></figcaption></figure>

### Prerequisite

Before proceeding, ensure you have an [ESP32 toolchain correctly configured](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/index.html) on your system. This is essential for building the code and deploying it to your ESP32 board. A [VS Code extension](https://github.com/espressif/vscode-esp-idf-extension/tree/master) is also available.

### Get the ioID-SDK example

Clone ioID-SDK and enter the ESP32 examples folder:

```bash
git clone https://github.com/iotexproject/ioID-SDK && cd ioID-SDK/example/esp32
```

Clone the tutorial:

```
git clone https://github.com/iotexproject/ioid-tutorial && cd tutorial
```

### Build the demo

```bash
# make sure your ESP-IDF is configured 
get_idf
# Set the target chip according to your board
idf.py set-target esp32
# Clean
idf.py fullclean
# Configure SSID & Password in Example Configuration
idf.py menuconfig
# Build
idf.py build
# Connect your board and flash (replace the correct serial port)
idf.py -p /dev/tty.usbserial-110 flash monitor
```

