# The Data API Service

The first component that we need is an API service that allows our devices to communicate the work they've completed to W3bstream. This service will implement the data streaming and sequencing layers of the [Layered DePIN Infrastructure](../../../depin-infra-modules-dim/dims-overview.md).&#x20;

For our project, we will leverage the [existing demo API](https://github.com/iotexproject/w3bstream/tree/develop/cmd/sequencer) provided with W3bstream deploying it on a Linux server in the cloud configured with Ubuntu 24. This setup is flexible and can be hosted on any VPS or equivalent cloud service.

## Step 1: Set Up Your VPS

### **SSH into Your VPS**

Use SSH to connect to your server. Replace `username` with your server username and `your_server_ip` with the actual IP address of your server.

```bash
ssh username@your_server_ip
```

### **Update and Upgrade the System**

Ensure your server is up to date with the latest security patches and updates.

```bash
sudo apt update && sudo apt upgrade -y
```

## Step 2: Install Docker and Docker Compose

### **Install Docker**

[Follow the official instructions to Install Docker](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)

Verify that the Docker Engine installation is successful by running the `hello-world` image.

```bash
sudo docker run hello-world
```

### **Install Docker Compose**

The Docker Compose plugin should be installed by default. If needed, you can [follow the official instructions to install it.](https://app.gitbook.com/s/N3toi7pZFqhzxAbCj5Uv/reference/proof-of-location-api)

### **Verify Installation**:

* Check that Docker and Docker Compose are installed correctly:

```bash
docker compose version
```

## Step 3: Configure Docker Compose

### **Fetch the latest W3bstream docker-compose.yaml**

Fetch the latest release of docker-compose.yaml from the W3bstream repository

```bash
# Fetch the latest W3bstream release number
export RELEASE=$(curl --silent "https://api.github.com/repos/iotexproject/w3bstream/releases/latest" | jq -r .tag_name)

# Download the Risc Zero demo prover
curl -L -o test/project/10000 https://raw.githubusercontent.com/iotexproject/w3bstream/$RELEASE/docker-compose.yaml
```

### Configure docker images

Edit docker-compose.yaml and apply the following changes:

1. Delete or comment out all image sections except the sequencer and Postgres images
2. Configure the Postgres database image
3. Configure the Database  settings in the sequencer image to match the Postgres configuration

