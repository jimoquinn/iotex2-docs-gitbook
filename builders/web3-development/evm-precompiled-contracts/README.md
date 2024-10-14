# EVM Precompiled Contracts

Precompiled contracts in the EVM are special contracts at fixed addresses, offering advanced functions with specific gas costs. Most precompiles don’t have a solidity wrapper (with `ecRecover` being the sole exception), therefore you’ll have to call the address directly with `addressOfPrecompile.staticcall(…)` or use assembly.

## EVM Precompiles Support in IoTeX

IoTeX supports all EVM precompiles and adds two more:&#x20;

* `secp256r1`, at address `0x8001`, is a cryptographic function for elliptic curve operations, and scryptHash, commonly used in password hashing algorithms.
* `scryptHash`, at address `0x8002`, commonly used in password hashing algorithms.

{% hint style="info" %}
For further details, developers can explore the IoTeX code at this [link to contracts.go](https://github.com/iotexproject/go-ethereum/blob/396c87ad912618b530affb6483e87e61adaba405/core/vm/contracts.go#L86), where they can see the specific addresses, gas costs, and functions associated with each precompile.
{% endhint %}
