# Register a DePIN Project

Any DePIN project intending to use ioID identities must apply for a certain number of ioIDs by paying the required amount. ioIDs can only be requested by registered DePIN projects on the IoTeX blockchain. Here’s how to register your project:

## Using the IoTeX CLI (`ioctl`)

```sh
ioctl ioid register "My DePIN Project"

Registerd ioID project id is 41
```

Once the transaction is completed you will receive a Project NFT with a certain Token ID, representing your DePIN Project ID on the IoTeX blockchain.

{% hint style="info" %}
Make sure you add the [Project NFT token address](https://github.com/machinefi/ioID-contracts/blob/75ee46b15284f5667cd500155f07f2e0d2544568/README.md?plain=1#L21) to your wallet app to see your projects and transfer them to other wallets if needed.
{% endhint %}

## Contract Call

**Contract:** ProjectRegistry

**Function Call:** `register() external payable returns (uint256)`

**Example:**

```solidity
let tx = await projectRegistry.registerProject();
```
