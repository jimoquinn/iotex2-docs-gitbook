# IoTeXscan API

## Overview

At IoTeX, we provide a powerful block explorer, [IoTeXScan](https://iotexscan.io), which allows users and developers to easily query data on the IoTeX blockchain. To make it even easier for developers familiar with Ethereum tools, we’ve implemented the same Etherscan API on IoTeXScan.

This guide provides a quick overview of how to get started with our IoTeXScan API and the available endpoints.

## Getting Started

You can use IoTeXScan’s API just as you would use the Etherscan API. The API allows developers to retrieve blockchain data programmatically, such as transaction details, block information, account balances, and much more.

Here are the key steps to start using the API:

**Base URL**: [https://index.iotexscan.io/api](https://index.iotexscan.io/api)

**API Key:** To interact with the IoTeXScan API, no API key is required. However, queries are rate-limited to 1 request per second.

**Example endpoint:**

```
https://index.iotexscan.io/api?module=account&action=balance&address=0x139929a597b91ea89f41026b65b281611890f13b
```

## Complete API

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=contract&action=getabi" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=contract&action=getcontractcreation" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=contract&action=getsourcecode" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=contract&action=checkverifystatus" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=contract&action=verifysourcecode" method="post" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=transaction&action=getstatus" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=gastraker&action=dailyavggasprice" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=gastraker&action=dailygasused" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=gastraker&action=dailyavggaslimit" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=token&action=addresstokennftinventory" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=token&action=addresstokennftbalance" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=token&action=addresstokenbalance" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=token&action=tokeninfo" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=token&action=tokenholderlist" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=iotxdailyprice" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=dailytx" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=dailynewaddress" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=dailytxnfee" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=iotxprice" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=dailyblockrewards" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=dailyblkcount" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=stats&action=tokensupply" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=log&action=getLogs" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=block&action=getblocknobytime" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=block&action=getblockreward" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=addresstokennftinventory" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=addresstokennftbalance" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=tokenbalancehistory" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=tokensupplyhistory" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=tokenbalance" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=token1155tx" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=tokennfttx" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=tokentx" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=txlistinternal" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=txlist" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=balancemulti" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=account&action=balance" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_estimateGas" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_gasPrice" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getStorageAt" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getCode" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_call" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getTransactionReceipt" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_sendRawTransaction" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getTransactionCount" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getTransactionByBlockNumberAndIndex" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getTransactionByHash" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getBlockTransactionCountByNumber" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getUncleByBlockNumberAndIndex" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_getBlockByNumber" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=proxy&action=eth_blockNumber" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}

{% swagger src="https://index.iotexscan.io/doc/openapi.json" path="?module=transaction&action=gettxreceiptstatus" method="get" %}
[https://index.iotexscan.io/doc/openapi.json](https://index.iotexscan.io/doc/openapi.json)
{% endswagger %}



