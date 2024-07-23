# 👨‍💻 Build with W3bstream

By leveraging W3bstream, developers can efficiently process and validate device data before committing proofs of physical work to the blockchain, ensuring integrity of data processing and reducing on-chain computation costs.&#x20;

This guide outlines the steps necessary to integrate W3bstream into your DePIN project, from setting up a local development environment to deploying your configuration on the IoTeX blockchain. To use W3bstream as the off-chain compute layer in a DePIN project, developers should follow these steps:

1. **Run a local W3bstream node**: Set up and run a W3bstream node on your local machine to facilitate the development and testing process.
2. **Build the prover logic**: Develop the logic that processes and verifies device data, ensuring it meets the necessary criteria before being sent to the blockchain.
3. **Create a W3bstream configuration file**: Compile a configuration file that includes your prover code, specifying how W3bstream should handle and process incoming data.
4. **Test the W3bstream prover locally**: Validate your prover logic and configuration file by running tests locally to ensure everything functions correctly.
5. **Deploy the W3bstream configuration to the IoTeX blockchain**: Once testing is complete, deploy your configuration to the IoTeX blockchain, enabling your DePIN project to leverage W3bstream's off-chain compute capabilities in a live environment.

## **Prerequisites**

{% hint style="info" %}
1. **ioctl CLI**

Ensure that you have [installed the IoTeX ioctl client](../../../builders/reference-docs/ioctl-client/) before proceeding:

```
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh
```
{% endhint %}

{% hint style="info" %}
2. **Testnet endpoint**

ioID is currently on testnet. Ensure you have configured ioctl with the IoTeX testnet endpoint:

`ioctl config set endpoint api.testnet.iotex.one:443`

[->See more IoTeX RPC Endpoints](../../../builders/web3-development/rpc-endpoints.md)
{% endhint %}

{% hint style="info" %}
3. **Test Tokens**

Ensure you have some IOTX test tokens in your wallet balance

[→ Claim your test tokens on the Developer Portal](https://developers.iotex.io)
{% endhint %}
