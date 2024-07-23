# Overview of W3bstream

In a [modular DePIN infrastructure](../dims-overview.md), W3bstream is an implementation of the off-chain computing layer featuring multi-prover technology. As a decentralized heterogeneous prover pool, W3bstream can perform project-specific business logic on the data stored in the Data Availability (DA) layer and generate **validity proofs** (e.g., zero-knowledge proofs, attestation reports, etc.) of the computations executed. W3bstream works as a stateless computing component in a modular DePIN infrastructure and follows the high-level workflow as illustrated below:

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Workflow of an Off-Chain computing Layer of the Modular DePIN Infrastructure </p></figcaption></figure>

1. A coordinator node in the off-chain computing layer retrieves data from the data availability layer based on the configuration of a DePIN project;
2. The coordinator node feeds data to an idle prover node or a selected set of idle prover nodes in the off-chain computing layer;
3. The prover node(s) performs computation specified by the DePIN project and generates the computation result and corresponding validity proof;
4. The computation result and validity proof are returned to the coordinator node;
5. The coordinator node sends the computation result and validity proof to a smart contract for further processing.
