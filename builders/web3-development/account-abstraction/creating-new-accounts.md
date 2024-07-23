# 👩‍💻 Creating new Accounts

## Creating new Accounts

In order to use account abstraction to create a new custom account, there are certain components that the dApp developer will have to create based on the needs of their application:

* `Account` contract, which implements the validation logic in the `validateUserOp` method, and any execution logic that a user operation can require.
* `AccountFactory` contract, which is in charge, as said above, of creating/deploying new custom account contracts.
* Some client code that builds the user ops that are compatible with the verification rules implemented in the `AccountFactory`.
* A **paymaster** is an optional part of the AA architecture. IoTeX provides a paymaster service for **Testnet** only at [https://paymaster.testnet.w3bstream.com](https://paymaster.testnet.w3bstream.com/). The role of the paymaster is to sponsor the gas needed to execute user operations, either sponsoring them completely or allowing users to pay for them in various tokens.
