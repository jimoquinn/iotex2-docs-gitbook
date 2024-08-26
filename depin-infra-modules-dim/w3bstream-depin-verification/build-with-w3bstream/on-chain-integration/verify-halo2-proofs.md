# Verify Halo2 Proofs

<details>

<summary>Prerequisite</summary>

You must have built an Halo2 verifier executable. [-> Learn more here.](../build-the-prover-code/halo2.md#build-the-prover)

</details>

## Generate the Verifier Contract

After the prover is built, a Solidity verifier contract can be generated with:

```sh
target/release/halo2-simple-circuit solidity -f ./verifier.sol

Generated verifier contract size: 8100
```

Just ensure you customize the `halo2-simple-circuit`  executable name with your own prover name.

## Example W3bstream Dapp (Halo2)

{% embed url="https://github.com/iotexproject/w3bstream/blob/develop/examples/halo2-circuit/contracts/Halo2Dapp.sol" %}
