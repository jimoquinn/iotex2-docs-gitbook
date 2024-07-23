# Sequencer Options

{% hint style="info" %}
This documentation is currently being updated. Please check back later for the latest version.
{% endhint %}

## Overview

The default DePIN configuration provided with the W3bstream release offers the essential stack needed to stream data messages from a DePIN device and process them in W3bstream, generating a validity proof that can be written and verified on-chain.

The Sequencer service provided in this configuration is a reference implementation for a DePIN data sequencer, supporting both [ioID](../../../../builders/reference-docs/ioctl-client/ioid-identities.md) and W3bstream. While suitable for development purposes, this demo service however is best used as a reference or starting point for your own sequencer implementation.

Below, we explore some configuration options for the data sequencer that can be useful during development of your W3bstream project.

## **Data Aggregation**

In a DePIN application, the data sequencer, whether centralized or decentralized, typically authenticates devices, validates, filters, and sorts their data. Each data message processed by the Sequencer is usually appended to a _W3bstream Task_ until the expected "aggregation value" is reached. In the provided demo sequencer, the default aggregation value is set to `1`, meaning each message sent to the sequencer is immediately wrapped in a W3bstream Task, stored in the Postgres DB, and fetched by W3bstream for processing.

You can change the data aggregation amount in the Sequencer configuration of `docker-compose.yaml` like shown below:

```yaml
# ...
sequencer:
  # ...
  command: 
    - "coordinatorAddress"
    - "coordinator:9001"
    - "databaseDSN"
    - "postgres://test_user:test_passwd@postgres:5432/test?sslmode=disable"
    - "aggregationAmount"
    - "10" # Increase this value to aggregate more messages in a W3bstream Task
```
