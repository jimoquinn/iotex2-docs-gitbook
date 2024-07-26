# End-to-End DeWi Demo

{% hint style="info" %}
This documentation is being updated.&#x20;
{% endhint %}

The DeWi (Decentralized Wireless) demo showcases the implementation and capabilities of decentralized wireless networks using the IoTeX blockchain. This demo illustrates the registration, setup, and operational processes involved in deploying a DeWi network on IoTeX, highlighting the key components and steps required to bring such a project to life.

## Repository

{% embed url="https://github.com/machinefi/iotex-dewi-demo" %}

## Key Sections

1. **Project Registration and ioIDs**: The initial step involves registering your DePIN project on the IoTeX platform and requesting ioIDs, which are unique identifiers for your devices within the network.
2. **Hardware Selection**: This  step will detail the selection process for compatible hardware devices that will form the backbone of the DeWi network.
3. **Firmware Development**: The firmware development provides necessary explanations and code examples to guide developers through the programming firmware for DePIN Devices.
4. **Sequencer Creation**: A demo sequencer repository is provided, which coordinates data validation and flow.
5. **Data Availability Layer Setup**: This involves configuring Postgres as a simple DA Layer, ensuring  data storage for the sequencer and retrieval by W3bstream.
6. **DePIN Verification**: This section demonstrates the process of verifying the actual work performed by the devices within the DeWi network to ensure owners are incentivized according to the DePIN tokenomics.
7. **Incentives Contract Creation**: This crucial step involves reating a smart contract to manage DePIN incentives, ensuring that proofs for device work is verified device owner addresses are correctly rewarded.
