# Layered Architecture

As illustrated in the figure below, the ioId-SDK adopts a layered design and consists of five layers from top to bottom, namely the DIDComm messaging layer, the identity and credential service layer, the cryptographic service layer, the cryptographic primitive layer, and the root of trust layer. It is worth noting that each layer is composed of multiple components, allowing developers to customize the SDK to meet hardware limitations and application requirements.

<figure><img src="https://iotex.larksuite.com/space/api/box/stream/download/asynccode/?code=NmYzMDMxNDZhZGExNjgwNDQ3OGIzYjZmODk2ZDZiMDJfNGg5T2RXbmxjd0ZVeUExUmRPSHM5d01vWFNmNEhiU3JfVG9rZW46QklBc2JkOU8wb3RlTmN4WURDYnVKd1l0czc4XzE3MTY1NTg5MTY6MTcxNjU2MjUxNl9WNA" alt=""><figcaption></figcaption></figure>

The arrows on the right side of the architecture diagram represent two development directions defined by the SDK.&#x20;

In the future, the SDK will continue to evolve and provide other application components related to Web3 and blockchain domains for developers to use.

#### The Southern part

The **southern** part forms the core framework of the entire SDK, which is based on the cryptographic suite developed in compliance with Arm’s Platform Security Architecture (PSA) architecture and aims to provide unified, standardized cryptographic suite application programming interfaces (APIs) for northbound component developers or other application developers. Through highly abstracted driver interfaces, cryptographic suites suitable for various development platforms, and an optimized SDK configuration system, the underlying southern layer not only applies to a wide range of embedded system platforms but also greatly reduces the learning curve for developers using the SDK.

#### The Northern part

The **northern** part is composed of self-sovereign identity (SSI) components built upon the core framework mentioned above. The **DIDs, VCs and DIDComm** messaging represent the three key pillars of SSI, which aim to move control of digital identity from conventional identity providers to individuals and lay down the foundation for people, organizations and things establishing rich digital relationships. **DIDs** are a new type of globally unique identifier (URI) that enables verifiable, self-sovereign digital identity, whereas **VCs** are able to attest identity attributes of subjects and the exchange of VCs builds up trust among DID-identified peers. Both DIDs and VCs are the proposed recommendations of the World Wide Web Consortium (W3C). **DIDComm**, as specified by the Decentralized Identity Foundation (DIF), provides utility for people, organizations and IoT devices interacting with machine-readable messages and creating DIDbased relationships.&#x20;

**DIDComm messages** are exchanged between software agents of entities for implementing a variety of security protocols. The modular design methodology allows developers to easily configure the SDK to adapt to their project needs. For instance, developers can build hardware wallets or blockchain embedded clients based on the southbound core framework, and create machine-to-machine (M2M) communications, identity wallets, metaverse applications, etc., based on the northbound SSI components.&#x20;
