# Node Operators

If you're aiming to set up an RPC endpoint on the IoTeX blockchain or become a block producer, this document provides the necessary instructions for running an IoTeX full-node and sync it with the Mainnet. It covers everything from initial setup, to ongoing management.

The IoTeX full node holds the complete blockchain state, similar to an "**Archive Node**" in Ethereum terminology. Any IoTeX full-node has the capability to receive new blocks from peer nodes ("sync") and broadcast them to other full nodes needing to sync with the chain.  When configured as a "**Gateway**", a full node can act as an IoTeX RPC endpoint, accepting new blockchain transactions and broadcasting them throughout the network.
