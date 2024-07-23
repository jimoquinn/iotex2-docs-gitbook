# Configure a ZK Prover Node

{% hint style="info" %}
Please notice that W3bstream is in the Testnet stage.
{% endhint %}

The recommended method to run a W3bstream node is using official Docker images from IoTeX.

<details>

<summary>Prerequisites</summary>

#### 1. Docker Engine Version 18.02 or higher

Check your docker installation:

```
docker version
```

[-> Install Docker](https://docs.docker.com/engine/install/)

#### 2. Docker Compose Plugin

Check your Docker Compose Plugin installation:

```
docker compose version
```

Install the Docker compose plugin with:

```
sudo apt install docker-compose-plugin
```

#### 3. A blockchain account funded with IOTX tokens

[-> Learn how to fund your IoTeX wallet](broken-reference)

</details>

## Instructions

### 1. Configure your blockchain account

To enable your node to send proofs to the blockchain, set up a funded account on the IoTeX Testnet:

```sh
export PRIVATE_KEY=<YOUR_DEV_WALLET_PRIVATE_KEY>
```

### 2. Fetch the latest W3bstream Docker images

Fetch the latest stable `docker-compose.yaml`:

<pre class="language-sh"><code class="lang-sh"><strong>export RELEASE=$(curl --silent "https://api.github.com/repos/iotexproject/w3bstream/releases/latest" | jq -r .tag_name)
</strong>curl https://raw.githubusercontent.com/iotexproject/w3bstream/$RELEASE/docker-compose.yaml > docker-compose.yaml
</code></pre>

Pull the required images:

```shell
docker compose pull
```

### 3. Optional: Configure a BONSAI API Key

To process proofs for DePIN projects based on RISC0, you need to configure a Bonsai API Key:

```
export BONSAI_KEY=${your bonsai key}
```

[-> Learn more about the BONSAI service](https://dev.risczero.com/api/generating-proofs/remote-proving)

### 4. Manage the node

{% hint style="info" %}
Make sure you run the following commands in the same directory where the W3bstream `docker-compose.yaml` file is located.
{% endhint %}

#### Start the node

To start your W3bstream node, run the following command in the same directory containing `docker-compose.yaml`:

```sh
docker compose up -d
```

#### Monitor the node log

Monitor your W3bstream instance with:

```sh
docker-compose logs -f coordinator prover
```

#### Shutdown the node

To shut down the node run the following:

```
docker-compose down
```
