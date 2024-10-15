---
hidden: true
---

# Integrating $IOTX on Your Exchange

This guide will walk you through the process of integrating the IoTeX token (`$IOTX`) on your exchange. Since IoTeX is fully **Ethereum-compatible**, most integration steps will resemble those of any EVM blockchain. Below are the detailed steps, requirements, and resources necessary for seamless integration.

If you require further assistance, please don’t hesitate to [reach out to our support team](./#id-8.-support-and-contact).

## 1. Overview of IoTeX and $IOTX Token

IoTeX is a leading decentralized **layer-1 blockchain,** focused on enabling decentralized physical infrastructure networks (DePIN). The IoTeX native token, `$IOTX`, powers the IoTeX ecosystem by facilitating blockchain transactions, staking, governance, as well as data computing and identities management for DePINs.

• **Token Name:** IoTeX

• **Ticker Symbol**: IOTX

• **Blockchain**: IoTeX Mainnet

• **Standard**: Native Protocol Token

## 2. Blockchain Basics and Compatibility

### IoTeX Mainnet Information

• **Network Name**: IoTeX Mainnet

• **Chain ID**: 4689

• **Symbol**: IOTX

**• RPC URL**: https://babel-api.mainnet.iotex.io (see [more endpoints](../../../builders/web3-development/rpc-endpoints.md#iotex-mainnet))&#x20;

• **Explorer URL**: [https://iotexscan.io](https://iotexscan.io)

### IoTeX Testnet Information

**• Network Name**: IoTeX Testnet

**• Chain ID**: 4690

• **Symbol**: IOTX

**• RPC URL**: https://babel-api.testnet.iotex.io (see [more endpoints](../../../builders/web3-development/rpc-endpoints.md#iotex-testnet))

• **Explorer URL**: [https://testnet.iotexscan.io](https://testnet.iotexscan.io)

{% hint style="success" %}
Since IoTeX is **fully compatible with Ethereum’s virtual machine (EVM)**, exchanges can use familiar Ethereum tools and libraries (such as Web3.js, Ethers.js, and Truffle) for `$IOTX` integration.
{% endhint %}

## 3. Wallet Integration

To support deposits and withdrawals for `$IOTX`, exchanges need to implement **wallet integration**. As IoTeX is fully Ethereum-compatible, most Ethereum-compatible wallets (such as MetaMask, Trust Wallet, and hardware wallets like Ledger) will work seamlessly for managing `$IOTX` tokens.

{% hint style="info" %}
Metamask-compatible wallets can also be automatically configured on the [IoTeX Developer Portal](https://developers.iotex.io).
{% endhint %}

### To integrate $IOTX into your platform’s wallet

• Use Ethereum-compatible libraries like Web3.js or Ethers.js to interact with the IoTeX blockchain.

• Set the correct RPC endpoint to ensure interaction with the IoTeX blockchain.

#### Example:

```javascript
const Web3 = require('web3');
const web3 = new Web3('https://babel-api.mainnet.iotex.io');

// Query the balance of an address
web3.eth.getBalance('0x4d8a5c5b52f45fcfd2ce7eea58390b214909ef24').then(console.log);
```

## 4. Node Setup and API Endpoints

Exchanges can either use public RPC endpoints for convenience, or set up their own IoTeX nodes **for higher reliability and security**.

{% hint style="warning" %}
Running your own node ensures maximum control over latency, security, and performance.
{% endhint %}

### Full Node Setup

If you prefer to run your own full node, you can follow the [IoTeX full node setup guide](https://github.com/iotexproject/iotex-bootstrap#release-status).&#x20;

### Public RPC Endpoints

• **IoTeX Mainnet:**  https://babel-api.mainnet.iotex.io (see [more endpoints](../../../builders/web3-development/rpc-endpoints.md#iotex-mainnet))&#x20;

• **IoTeX Testnet**: https://babel-api.testnet.iotex.io (see [more endpoints](../../../builders/web3-development/rpc-endpoints.md#iotex-testnet))

## 5. Deposits and Withdrawal

### Deposit Flow

<details>

<summary>If this is the first integration of the IoTeX blockchain</summary>

To integrate `$IOTX` deposits:

1. Generate a `0x` deposit address for your user using any Web3 tool
2. Since IoTeX used to have its own `io1`  address format in the past and a few users still use it, compute the corresponding `io1` address (see [how to convert a 0x address to the corresponding io1 address](../../../builders/reference-docs/native-iotex-development/address-conversion.md)). Both addresses share the same private key and represent the same account on the IoTeX blockchain.
3. Provide the `0x` address first, and the `io1` address as an alternative option.&#x20;
4. Monitor the IoTeX blockchain for incoming transactions using the [IoTeXscan API](https://index.iotexscan.io/doc/ui) or direct RPC queries to a full node.
5. Confirm transactions after a specific number of block confirmations according to your policies (notice that IoTeX transactions are final **on the first block**).

</details>

<details>

<summary>If your exchange is already integrated using the IoTeX native API</summary>

* If your Exchange supports $IOTX-ERC20 deposits on other chains, make sure your deposit flow allows the user to select the network for deposit . This flow applies when the used selects the IoTeX Blockchain as the network
* Since your exchange already supports the io1 native format for IoTeX addresses, compute the corresponding `0x` address from the same private key (see [how to convert a 0x address to the corresponding io1 address](../../../builders/reference-docs/native-iotex-development/address-conversion.md)). Since both addresses share the same private key and represent the same account on the IoTeX blockchain.

<!---->

* Provide the `0x` address first, and the `io1` address as an alternative option.&#x20;

<!---->

* Monitor the IoTeX blockchain for incoming transactions using the [IoTeXscan API](https://index.iotexscan.io/doc/ui) or direct RPC queries to a full node.

<!---->

* Confirm transactions after a specific number of block confirmations according to your policies (notice that IoTeX transactions are final **on the first block**).

</details>

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Example UI for $IOTX deposit flow on the IoTeX Blockchain</p></figcaption></figure>

### Withdrawal Flow

To integrate $IOTX withdrawals:

If your exchange is already integrated with the IoTeX blockchain and supports withdrawals of the IOTX token on multiple networks, **make sure the user can select the IoTeX Native blockchain.** This flow applies to withdrawals on the IoTeX Blockchain.

1. Allow the user to input the recipient address in both `0x` and `io1` formats for withdrawals. You can generate and send transactions using the Ethereum-compatible `eth_sendTransaction` API. If you already&#x20;
2.

Make sure to:

• Use the correct gas price and gas limit based on IoTeX network conditions.

• Sign transactions with the private key of your exchange’s withdrawal wallet.

#### Example transaction code (using Web3.js):

```javascript
const Tx = require('ethereumjs-tx').Transaction;
const privateKey = Buffer.from('your_private_key', 'hex');

const txData = {
  nonce: web3.utils.toHex(txCount),
  gasLimit: web3.utils.toHex(21000),
  gasPrice: web3.utils.toHex(web3.utils.toWei('10', 'gwei')),
  to: 'recipient_address',
  value: web3.utils.toHex(web3.utils.toWei('1', 'ether')),
  chainId: 4689, // IoTeX Mainnet Chain ID
};

const tx = new Tx(txData);
tx.sign(privateKey);

const serializedTx = tx.serialize();
const rawTx = '0x' + serializedTx.toString('hex');
web3.eth.sendSignedTransaction(rawTx)
  .on('receipt', console.log);
```



## 6. Trading and Smart Contract Integration

### Smart Contract Compatibility

Since IoTeX is EVM-compatible, it supports all Ethereum smart contracts, including those written in Solidity. If your exchange supports Ethereum-based trading, you can use the same mechanisms to enable `$IOTX` trading.

## 7. Listing $IOTX

To list `$IOTX`, use the following token details:

• **Symbol**: IOTX

• **Decimals**: 18

## 8. Security Considerations

• **Private Key Management**: Ensure private keys are stored securely (e.g., using HSMs, cold storage, or other secure key management systems).

• **Multi-Sig Wallets**: Implement multi-signature wallets for withdrawals to minimize the risk of unauthorized transactions.

• **Monitoring and Alerts:** Set up monitoring for large transactions, unusual activity, and sudden spikes in gas fees.

## 8. Support and Contact

For any issues or further questions regarding the `$IOTX` integration, feel free to contact the IoTeX team:

• **Email**: developers@iotex.io

• **Official Documentation**: [https://docs.iotex.io](https://docs.iotex.io)

• **Developer Resources**: [IoTeX Developer Portal](https://dev.iotex.io)
