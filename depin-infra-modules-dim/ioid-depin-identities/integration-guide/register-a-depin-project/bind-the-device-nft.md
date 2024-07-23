# Bind the Device NFT

{% hint style="warning" %}
Ensure you have already deployed a Device NFT contract for your DePIN project

[↗ Deploy the Device NFT](deploy-the-device-nft.md)&#x20;
{% endhint %}

After registering a DePIN project, the next step is to set the Device NFT contract for that project. This contract must be set before a device attempts to register an ioID for your project.

## Using IoTeX CLI (`ioctl`)

```
ioctl ioid device -p [PROJECT_ID] [DEVICE_NFT_CONTRACT_ADDRESS]
```

## Contract Call

**Contarct:** ioIDStore

**Function Call:** `setDeviceContract(uint256 _projectId, address _contract) external`

**Example:**

```solidity
let tx = await ioIDStore.setDeviceContract(41, "0x9876543210abcdef9876543210abcdef98765432");
```

