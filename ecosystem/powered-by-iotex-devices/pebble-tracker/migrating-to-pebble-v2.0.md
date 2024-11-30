# Migrating to Pebble v2.0

{% hint style="warning" %}
**Note:** This document applies to Pebble Trackers that run a software version `v1.0.x`.

If your device shows version `v2.0` or above, you are all set.
{% endhint %}

## Overview

There are several methods available to migrate your Pebble Tracker software from v1.0.x to v2.0, depending on the current registration status of your device and your personal preference.

Choose the method that best suits your situation and follow the corresponding instructions:

* [#method-1-offline-firmware-update](migrating-to-pebble-v2.0.md#method-1-offline-firmware-update "mention")(works for all devices)
* [#method-2-online-firmware-update](migrating-to-pebble-v2.0.md#method-2-online-firmware-update "mention") (only for already registered Devices)
* [#method-3-device-registartion--firmware-update](migrating-to-pebble-v2.0.md#method-3-device-registartion--firmware-update "mention") (only for unregistered devices)

## Method 1: Offline Firmware Update

An easy way to upgrade your Pebble Tracker software from v1.0.x to v2.0 is by performing a firmware update via the USB port. This method works for all devices:

* **Brand new, unregistered devices, or**
* **Devices already registered on** [**MachineFi.com**](https://machinefi.com)**.**

{% hint style="success" %}
Simply follow the→ [usb-firmware-update.md](usb-firmware-update.md "mention") guide to complete the update process.
{% endhint %}

## Method 2: Online Firmware Update

You can also upgrade from v1.0.x to v2.0 by performing an OTA (_Over-The-Air_) firmware update. This method is only suitable for devices that meet the both following criteria:

* **They are already registered on** [**MachineFi.com**](https://machinefi.com)**, and**
* **They are equipped with a SIM card that has an active internet connection and data plan.**

Follow the instructions to ensure a smooth upgrade process.

### Start the OTA Firmware Update

1. Make sure your SIM card is correctly installed in the SIM card slot of the device (see [Installing the SIM card](https://app.gitbook.com/s/f2s3zCHPO4kfjqwDZ9Gw/get-started/quick-start#installing-the-sim-card "mention"))
2. Power off your Pebble Tracker by pressing the `Power/Confirm` button and keeping it pressed until the status LED flashes green
3. Press and keep pressing the `Up Arrow` button, then press and release the `Power/Confirm` button (while keeping the Up Arrow still pressed).
4. Release the up arrow once the device is powered on and you see the message “_**OTA Firmware Update. Connecting...**_” message on the display
5. Wait for the device to connect to the cellular network and the message “_P**lease choose an app from the portal**_” is displayed
6. Open [portal.machinefi.com](https://portal.machinefi.com/) in a Metamask compatible Browser, or directly inside [ioPay mobile](https://iopay.me/), and connect to the portal with your MachineFi blockchain account (you can create one by following the [get started guide](https://app.gitbook.com/s/f2s3zCHPO4kfjqwDZ9Gw/get-started/quick-start#creating-a-machinefi-account))
7. Select the “**App Store**” tab, then locate and open the “**Firmware Upgrade**” app and click the “**Install**” button
8. In the following dialog, select the device you want to upgrade (see note → ✳️ below)
9. Make sure your Pebble is still showing the “_**Please, choose an app on the portal**_” message on the display, and click the `Next` button on the portal
10. Go ahead and click `Next` on the second dialog to trigger the firmware upgrade request transaction for your device
11. Confirm the transaction in your Metamask wallet
12. Wait for the Pebble tracker to detect the request and start downloading the firmware

{% hint style="info" %}
-> ✳️ If you own multiple devices, you can identify your devices from the “**Devices**” tab on the MachineFi portal by matching the IMEI number with the one printed on the Pebble box, and the serial number printed on the box with the one printed on the back of the device
{% endhint %}

{% hint style="info" %}
The download and installation of the firmware may require some time. In some cases, the download can fail due to a network error: this is usually caused by a low cellular signal in your area, especially if your SIM card connects using the NB-IoT band. In this case, you can try again, or just try the offline firmware update method detailed below.
{% endhint %}

## Method 3: Device Registration + Firmware Update

The final method to upgrade from v1.0.x to v2.0 is by first registering your device and then performing a firmware update. This method is required for brand new devices that have never been registered:

### Turn on your Pebble Tracker

Wait for the Pebble Tracker to establish a cellular connection and begin communicating with the network. You will then be prompted to initiate the registration process, which will link the device to your IoTeX wallet as its owner.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Press the **Power/Confirm** button once, to start the registration process on the Pebble side:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/pebble-reg2.jpg" alt=""><figcaption></figcaption></figure>



## Registering your Pebble

You can now switch to the [**Devices**](https://portal.machinefi.com/device) tab of the portal, which lists all the devices you associated with your MachineFi account. For a newly created account, with no devices added yet, the page will look like the one below, just click the **Add Device** button:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/add-device.jpg" alt=""><figcaption></figcaption></figure>

select "**Pebble**" to register and add a new Pebble Tracker to your MachineFi account:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/addpebble1%20(5).jpg" alt=""><figcaption></figcaption></figure>

Follow the registration screens until you reach the "Confirm" step, where the owner address and device IMEI number are shown:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/addpebble2.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Make sure your Pebble is powered on and [prompting for device registration](migrating-to-pebble-v2.0.md#power-on).
{% endhint %}

Go ahead and press the **Next** button, confirm the transaction in your wallet, and wait for your blockchain address to be displayed on the Pebble tracker screen:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/pebble-reg3.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/pebble-reg1.jpg" alt=""><figcaption></figcaption></figure>

Finally, we complete the registration on the device side by pressing the Power/Confirm button once more, and waiting for Pebble to complete the registration:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/addpebble4.jpg" alt=""><figcaption></figcaption></figure>

The "[**Devices**](https://portal.machinefi.com/device)" page will show the Pebble Tracker you just registered, marked as a "**Confirmed**" device:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/addpebble5.jpg" alt=""><figcaption></figcaption></figure>

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

