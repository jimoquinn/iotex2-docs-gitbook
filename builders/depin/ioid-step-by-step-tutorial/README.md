# ioID Step by Step Tutorial

Depending on the development stage of a DePIN project, there are multiple ways it can integrate ioID. In this section of the documentation, we share different integration flows tailored to various use cases.

1. [A fully decentralized approach](a-fully-decentralized-approach.md)
2. [A "proxy contract" approach](a-proxy-contract-approach.md)&#x20;

Before you begin working with the IoTeX blockchain and related tools, follow these preliminary steps to set up your development environment.

### Prerequisites

Ensure you have the following tools installed:

* [ioctl](https://docs.iotex.io/builders/reference-docs/ioctl-client#install-latest-release-build): For interacting with the IoTeX blockchain.
* [curl](https://curl.se/): For sending messages to the API node.
* [jq](https://jqlang.github.io/jq/): To format JSON output.

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

**Claim test IOTX**: You can claim test IOTX tokens on the IoTeX Developer portal at [https://developers.iotex.io/faucet](https://developers.iotex.io/faucet).

**Configure Metamask**: if you need to configure Metamask with IoTeX for convenience, you can do so on the&#x20;

Check the balance of your wallet with:

```bash
ioctl account balance devaccount
```

Export the private key with:

```
ioctl account export devaccount
```
