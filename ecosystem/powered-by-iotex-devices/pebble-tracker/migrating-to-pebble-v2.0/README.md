# Migrating to Pebble v2.0

{% hint style="warning" %}
**Note:** This document applies to Pebble Trackers that run a software version `v1.0.x`.

If your device shows version `v2.0` or higher, you are all set. Please proceed to the [quick-start.md](../quick-start.md "mention") and register your device if you haven't done so yet.
{% endhint %}

## Overview

There are several methods available to migrate your Pebble Tracker software from `v1.0.x` to `v2.0`, depending on the current registration status of your device.

Choose the method that best suits your situation and follow the corresponding instructions:

{% hint style="success" %}
**Method 1: Firmware Update over USB**

This method applies to any device.

* Follow the [usb-firmware-update.md](../usb-firmware-update.md "mention") guide to complete the firmware update process
* Proceed to [device-registration.md](../device-registration.md "mention")  guide to register your device
{% endhint %}

If you cannot perform a USB firmware update, please proceed with:

{% hint style="success" %}
**Method 2: Firmware Update Over The Internet**

* Follow the [1.0-device-registration.md](1.0-device-registration.md "mention") guide if you **haven't registered** your Pebble Tracker
* Follow the [Broken link](broken-reference "mention") guide to update the device firmware to v2.0
* Proceed to [device-registration.md](../device-registration.md "mention")  guide to register your device
{% endhint %}

## Online Firmware Update



##

## Congratulations!

Your Pebble is ready to send IoT data to IoTeX Dapps and fuel the _MachineFi_ blockchain revolution!

Here is what your Pebble screen should look like:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/pebble-display-icons.jpg" alt=""><figcaption></figcaption></figure>

By default, the factory configuration will collect all Pebble sensors data, and send one data message every 5 minutes to the IoTeX Real-world Data Oracle network.

{% hint style="info" %}
**Please notice** that the factory firmware introduces a \~500m random offset to the GPS coordinates. Depending on the installed Dapp, sensors' configurations may differ.&#x20;
{% endhint %}

You can monitor your real-time device sensors directly on the MachineFi portal by going to the [**My Data**](https://portal.machinefi.com/myData) page:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/pebble-reg4.jpg" alt=""><figcaption></figcaption></figure>



{% hint style="success" %}
Once the firmware update is complete, please move to the Device Registration
{% endhint %}

