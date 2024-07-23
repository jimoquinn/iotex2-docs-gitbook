# Deterministic Deployment

**Deterministic Deployment Proxy Contracts on IoTeX:**

<table><thead><tr><th width="214">Network</th><th>DD Proxy Address</th></tr></thead><tbody><tr><td>IoTeX Mainnet</td><td><code>0x4e59b44847b379578588920ca78fbf26c0b4956c</code></td></tr><tr><td>IoTeX Testnet</td><td><code>0x4e59b44847b379578588920ca78fbf26c0b4956c</code></td></tr></tbody></table>

## What is Deterministic Deployment

"Deterministic deployment" refers to a technique used in various blockchain projects where the same bytecode can be deployed on different blockchains to produce the same contract address. This is achieved through the following two steps:

1. **Deploy the "Proxy Contract"**
   * Replay a special transaction on the target blockchain to deploy a "proxy contract."
   * The sender of this transaction must be a new address on the target blockchain, i.e., with a nonce of 0.
   * This will result in the creation of a specific address for the proxy contract.
2. **Deploy the Desired Contract**
   * Use the proxy contract to deploy the desired bytecode.
   * Inside the proxy contract, the CREATE2 opcode is used to create contracts, so the final contract address depends only on the hash of the bytecode, being independent of the nonce.
   * This ensures deterministic contract addresses on any blockchain.

## **Proxy Contract Example**

This is a popular repository for a deterministic deployer used by many projects:

{% embed url="https://github.com/Arachnid/deterministic-deployment-proxy" %}

The `test.sh` script performs 2 main steps:

1. **Deploy the proxy**
   * It deploys the proxy ("deployer") contract first, which will get the contract address `0x4e59b44847b379578588920ca78fbf26c0b4956c`.
2. **Deterministically Deploy a Contract**
   * It calls the proxy contract to deploy a demo contract, which will always get the same address regardless of when and where it's deployed (as long as it's created by calling the given proxy and with the same bytecode).

## Deterministic Deployment on IoTeX

On IoTeX, the project above has been used to deploy a publicly accessible proxy contract for deterministic deployment, whose address is `0x4e59b44847b379578588920ca78fbf26c0b4956c`, same for both testnet and mainnet.&#x20;

{% hint style="info" %}
Any IoTeX Project can call the proxy contract on IoTeX like similarly to the project's [test script](https://github.com/Arachnid/deterministic-deployment-proxy/blob/be3c5974db5028d502537209329ff2e730ed336c/scripts/test.sh#L28) above to obtain deterministic deployment on IoTeX.
{% endhint %}

This address is a popular proxy contract for deterministic deployment available on many blockchains: by checking this address on [etherscan.io](https://etherscan.io) for instance, thousands of transactions will be listed that use that contract to obtain deterministic deployment. This demonstrates the widespread adoption and reliability of this method.&#x20;
