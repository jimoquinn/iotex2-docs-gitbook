# Create the Project File

## A closer Look at the W3bstream Project File

The W3bstream project file includes all the necessary code and configurations for a W3bstream node to correctly serve your DePIN project with data computation and on-chain proof submission. When deploying a W3bstream project you are in fact deploying a project file and linking it to your Project ID in the W3bstream contracts.

Below is an example of a W3bstream project file:

```javascript
{
  "defaultVersion": "0.1",
  "versions": [
    {
      "vmType": "risc0",
      "output": {
        "type": "stdout",
        "ethereum": {
          "chainEndpoint": "https://babel-api.testnet.iotex.io",
          "contractAddress": "0xDea7f9b692cb90a2DF1860189BcAc428500c44f1",
          "receiverContract": "0x22D5B41b28E7f9739a3D0C984737174cC7e554dF",
          "contractMethod": "submitProof",
          "contractAbiJSON": "[{\"inputs\":[{\"internalType\":\"bytes\",\"name\":\"seal\",\"type\":\"bytes\"},{\"internalType\":\"bytes32\",\"name\":\"imageId\",\"type\":\"bytes32\"},{\"internalType\":\"bytes32\",\"name\":\"postStateDigest\",\"type\":\"bytes32\"},{\"internalType\":\"bytes\",\"name\":\"journal\",\"type\":\"bytes\"}],\"name\":\"submitProof\",\"outputs\":[],\"stateMutability\":\"nonpayable\",\"type\":\"function\"}]"
        }
      },
      "version": "0.1",
      "code": "789cecb3bc5acda85509c609e9..."
    }
  ]
}

```

### Explanation

The W3bstream project file is in fact an array of configurations. Each configuration in the array allows you to define different settings for various provers and outputs, enabling flexibility in how W3bstream handles proofs and integrates with other components.

* **defaultVersion**: The default version of the configuration to be used.
* **versions**: An array of all available W3bstream configurations for the project. Each configuration includes:
  * **vmType**: The type of prover (e.g., halo2, risc0, zkwasm, with more types in the future).
  * **output**: Defines where the proof should be written.
  * **version**: The version number of this configuration.
  * **code**: The actual code of the prover if it's a ZK prover. Zlib compressed and hex encoded.

## Create a configuration for your project

A W3bstream project file with a valid configuration can be easily generated using the ioctl CLI for various types of provers. After generation, the configuration can be manually finalized by adding receiver contract details, version numbers, and other necessary information.

### Risc Zero provers

To generate a W3bstream project file for a Risc Zero prover using a Postgres database as the Data Availability (DA) Layer, use the following ioctl command:

```sh
ioctl ws project config \
    -t "risc0" \
    -s "postgres://test_user:test_passwd@localhost:5432/test?sslmode=disable" \
    -i "methods.rs" \
    -o "20000" \
    -e "{\"image_id\":\"RANGE_ID\", \"elf\":\"RANGE_ELF\"}"
```

Make sure to:

* **Configure DA Layer Credentials**: Ensure the Postgres database credentials are correct.
* **Customize File Paths**: Set the path to your `methods.rs` file [appropriately](../build-the-prover-code/risc-zero.md#build-the-prover).
* **Customize Project File Name**: Change the project file name (e.g., `10001`) as needed.
* **Match `image_id` and `elf` Fields**: Ensure the `image_id` and `elf` fields in the command match the values in your `methods.rs` file.

### Halo2 Provers

For a Halo2 prover, use the command below:

```sh
ioctl ws project config \
    -t "halo2" \
    -s "postgres://test_user:test_passwd@localhost:5432/test?sslmode=disable" \
    -i "pkg/halo2_simple_circuit_bg.wasm" \
    -c "20001"
```

### zkWASM Provers

For a zkWASM prover, use the command below:

<pre class="language-sh"><code class="lang-sh"><strong>ioctl ws project config \
</strong>    -t "zkwasm" \
    -s "postgres://test_user:test_passwd@localhost:5432/test?sslmode=disable" \
    -i "zkwasm_demo.wasm" \
    -c "20002"
</code></pre>

