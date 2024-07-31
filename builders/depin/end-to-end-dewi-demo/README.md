# End-to-End DeWi Demo

{% hint style="info" %}
This documentation is being updated.&#x20;
{% endhint %}

The DeWi (Decentralized WiFi Access Network) demo showcases the implementation of a DePIN project for a community-owned decentralized WiFi network using the IoTeX blockchain. This demonstration covers the essential components of a DeWi network and how to deploy them on IoTeX.

We will guide you through the entire process, from registering your DePIN project and devices on IoTeX to managing device registration on the firmware side. The demo includes developing the DePIN verification logic and creating a DApp that distributes incentives to the owners of the WiFi routers. This comprehensive overview covers all the critical steps required to build the infrastructure.

We encourage you to build Proofs of Concept (PoCs) for mobile apps and payment mechanisms that leverage this decentralized infrastructure.[Share your apps with the community, ](https://iotex.io/devdiscord)showcase your improvements and how the DeWi network can be enhanced with engaging and functional user interfaces.

## Key Sections

1. **Project Registration and ioIDs**: The initial step involves registering your DePIN project on the IoTeX platform and requesting ioIDs, which are unique identifiers for your devices within the network.
2. **Hardware Selection**: This  step will detail the selection process for compatible hardware devices that will form the backbone of the DeWi network.
3. **Firmware Development**: The firmware development provides necessary explanations and code examples to guide developers through the programming firmware for DePIN Devices.
4. **Sequencer Creation**: A demo sequencer repository is provided, which coordinates data validation and flow.
5. **Data Availability Layer Setup**: This involves configuring Postgres as a simple DA Layer, ensuring  data storage for the sequencer and retrieval by W3bstream.
6. **DePIN Verification**: This section demonstrates the process of verifying the actual work performed by the devices within the DeWi network to ensure owners are incentivized according to the DePIN tokenomics.
7. **Incentives Contract Creation**: This crucial step involves reating a smart contract to manage DePIN incentives, ensuring that proofs for device work is verified device owner addresses are correctly rewarded.
