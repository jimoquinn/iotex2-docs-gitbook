# zkWASM

<details>

<summary>Prerequisites</summary>

#### NodeJS

[-> Ensure you have NodeJS installed.](https://nodejs.org/en/download/package-manager)

#### AssemblyScript

Ensure you have `AssemblyScript` installed:

```sh
npm install -g assemblyscript
```

</details>

## Build the prover

### Clone the W3bstream repository

Start by cloning the W3bstream repository, where you can start from a template example:

```sh
git clone https://github.com/iotexproject/w3bstream.git
```

Open the folder in a code editor and make the required modifications based on your actual data message and prover logic.

{% hint style="info" %}
[-> Go to the official ZKWASM documentation to learn more about how to develop ZKWASM circuits](https://github.com/DelphinusLab/zkWasm#overview)
{% endhint %}

### Build the Circuit

Enter the zkWASM circuit folder

```sh
cd examples/zkwasm-circuit/circuit
```

Build the prover with:

```sh
asc src/add.ts -O --noAssert -o zkwasm_demo.wasm
```

The prover binary will be saved in `zkwasm_demo.wasm.`

{% hint style="success" %}
[-> Go to the **Create a W3bstream Project** section to create a W3bstream configuration file based on this prover](../deploy-to-w3bstream/)
{% endhint %}

## Verify a Proof Locally

### Using Docker

{% hint style="info" %}
[→ Check out the Getting Started](../get-started/) to learn how to generate a local proof inside a local W3bstream node&#x20;
{% endhint %}

1. Execute the `docker run` command for local verification. Note that the directory where the proof is located needs to be mounted into the image. It's simple, just input the proof file. You can also use the help command to check how to use it.

```
docker run -v /host/zkwasm-proof.json:/zkwasm-proof.json iotexdev/zkverifier /verifier/zkwasm-circuit verify -p /zkwasm-proof.json
```

### Using the binary

{% hint style="warning" %}
Because a dependency of `zkwasm-circuit` is still under development and not yet ready for public release, it is recommended to use the Docker image method above for local verification.
{% endhint %}

#### Build the Verifier

Run the following command to build the verifier:

```bash
cargo build --release
```

After the command is successful, a `zkwasm-circuit` executable file will be generated in the `target/release` directory.

#### Verify

You can execute the binary file in the `target/release` directory. To verify a proof, simply provide the proof file as an argument. For more details on usage, you can use the help command.

```bash
target/release/zkwasm-circuit verify -p zkwasm-proof.json
```

{% hint style="info" %}
`zkwasm` currently supports single proof verification only.
{% endhint %}
