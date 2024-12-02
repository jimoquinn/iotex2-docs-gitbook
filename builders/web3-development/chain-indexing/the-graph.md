# The Graph

The Graph, a decentralized protocol for indexing and querying blockchain data, now officially supports IoTeX. This integration allows developers to create open APIs, known as subgraphs, to efficiently access and organize data from the IoTeX blockchain. With The Graph, IoTeX developers can enhance their dapps by retrieving information seamlessly, improving functionality and user experience without relying on centralized data providers.

## Quick Start

Dapp developers can refer to the official The Graph documentation to create their Subgraphs for IoTeX:

[→ The Graph Quick Start Guide](https://thegraph.com/docs/en/quick-start/)&#x20;

Once the Subgraph is created inside The Graph Studio, it's enough to initialize it as usual with the official CLI and select ethereum as the protocol and iotex as the network:

```sh
graph init --studio <SUBGRAPH_SLUG>
```

{% hint style="info" %}
You can copy the command above directly from your subgraph page to include your specific subgraph slug.
{% endhint %}

You’ll be prompted to provide some info on your subgraph, make sure you select **`ethereum`** as the protocol, and **`iotex`** as the network:

<figure><img src="../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

Simply have your contract verified on the block explorer and the CLI will automatically obtain the ABI and set up your subgraph. The default settings will generate an entity for each event.

## Additional resources

* To explore all the ways you can optimize & customize your subgraph for a better performance, read more about [creating a subgraph here](https://thegraph.com/docs/en/developing/creating-a-subgraph/).
* For more information about querying data from your subgraph, read more [here](https://thegraph.com/docs/en/querying/querying-the-graph/).
