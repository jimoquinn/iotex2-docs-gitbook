---
description: A "Proxy Contract" Approach
hidden: true
---

# Integrate ioID in your cloud

In scenarios where a DePIN project cannot integrate ioID directly into their device’s firmware, this approach enables the project’s cloud to manage ioID registration and message signing on behalf of the devices. In this setup, a “Proxy ioID Contract” serves as an intermediary between the project’s cloud and ioID contracts. The cloud acts as a “trusted entity” within the proxy contract, authorizing on-chain ioID registrations and binding them to the actual device owner.

{% hint style="warning" %}
* Ensure you followed the initial steps to [register your Project on the IoTeX chain](./#id-1.-register-your-depin-project-on-iotex).
* Ensure you have git and have nodejs installed
{% endhint %}

## 1. Deploy the ioID Proxy Contract

```bash
git clone https://github.com/iotexproject/ioID-contracts
cd ioID-contracts && npm install
```

Export your private key and contract addresses to initialize the proxy contract

```bash
export PROJECT_REGISTRY=0x060581AA1A4e0cC92FBd74d251913238De2F13cd 
export IOI_DSTORE=0x60cac5CE11cb2F98bF179BE5fd3D801C3D5DBfF2

export PRIVATE_KEY=0x
```

Deploy the proxy contract with:

```bash
npx hardhat run scripts/deploy-proxy.ts --network testnet
```



