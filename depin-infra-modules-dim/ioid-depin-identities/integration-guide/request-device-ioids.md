# Request Device ioIDs

After registering your DePIN project, you need to apply for device ioIDs.

{% hint style="info" %}
You will pay the required amount to complete the application for the number of ioID requested. The current cost on the IoTeX testnet is `0.1 IOTX` per each ioID.&#x20;
{% endhint %}

## Using the IoTeX CLI (`ioctl`)

```sh
ioctl ioid apply --project-id <your_project_id> --amount <number_of_ioIDs>
```

After the transaction, the number of requested ioIDs will be associated with your DePIN project.&#x20;

## Contract Call

**Contract:** ioIDStore

**Function Call:** `applyIoIDs(uint256 _projectId, uint256 _amount) external payable`&#x20;

**Example:**

```solidity
const tx = await ioIDStore.apply(41, 10);
```
