# Setup an IoTeX RPC Node

## Bootstrap a Full Node

{% hint style="success" %}
[-> Refer to the bootstrap guide on GitHub for configuring a full node ](https://github.com/iotexproject/iotex-bootstrap#iotex-delegate-manual)
{% endhint %}

### Configure a Gateway <a href="#interact-with-iotex-full-nodes" id="interact-with-iotex-full-nodes"></a>

In case you want to run an IoTeX Gateway and use it as an RPC endpaint to broadcast transactions, make sure you follow the bootstrap guide linked above with the following two accortezze:

1. When downloading the snapshot file, make sure you download the file that includes database indexes:

<figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

2. When running the docker file, make sure you include the "**gateway**" argument:

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

3. Ensure that port `15014` is mapped in your docker run command and it's open in your firewall if you plan to use your node as an **Ethereum RPC gateway**. Alternatively, open port `14014` for operating the node as an IoTeX Native RPC Endpoint - though this option is considered deprecated.
