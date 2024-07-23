# Halo2

<details>

<summary>Prerequisites</summary>

#### WASM pack

Ensure you have `wasm-pack` installed:

```sh
curl https://rustwasm.github.io/wasm-pack/installer/init.sh -sSf | sh
```

</details>

## Build the prover

### Clone the W3bstream repository

Start by cloning the W3bstream repository, where you can start from a template example:

```sh
git clone https://github.com/iotexproject/w3bstream.git
cd examples/halo2-circuit/
```

Open the folder in a code editor and make the required modifications based on your actual data message.

### Build the circuit

```sh
wasm-pack build --target nodejs --out-dir pkg
```

{% hint style="info" %}
[-> Go to the official Halo2 documentation to learn how to build Halo2 circuits](https://zcash.github.io/halo2/user/simple-example.html)
{% endhint %}

The circuit bytecode is saved in the file  `halo2_wasm_bg.wasm` located under the `pkg` folder.

{% hint style="success" %}
[-> Go to the **Create a W3bstream Project** section to create a W3bstream configuration file based on this circuit](../deploy-to-w3bstream/)
{% endhint %}

### Build the circuit executable

The command below will create thasdfwefe circuit executable that can be used to generate and verify proofs locally, as well as generate the Solidity contract for on-chain verification of a proof:

```shell
cargo build --release
```

<table data-view="cards"><thead><tr><th></th></tr></thead><tbody><tr><td><a href="../deploy-to-w3bstream/create-the-project-file.md">-> Go to the <strong>Create a W3bstream Project</strong> section to create a W3bstream configuration file based on this prover</a></td></tr><tr><td><a href="../on-chain-integration/verify-halo2-proofs.md">→ See the <strong>On-chain Verification</strong> section to learn how to verify Risc Zero proofs</a></td></tr></tbody></table>

{% hint style="success" %}

{% endhint %}

{% hint style="success" %}

{% endhint %}
