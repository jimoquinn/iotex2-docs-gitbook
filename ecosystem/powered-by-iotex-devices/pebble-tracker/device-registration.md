# Device Registration

The device registration process is about linking your Pebble to your wallet address as the device owner.&#x20;

{% hint style="warning" %}
Please ensure your Pebble Tracker version in 2.0 or higher: [#check-the-software-version](quick-start.md#check-the-software-version "mention")
{% endhint %}

## 1. Start Pebble In _Device Register_ Mode&#x20;

1. Power off the device
2. Press and keep pressing the arrow down
3. Press the power button once
4. Use the arrow keys to select the "_Device Register_" menu
5. Press the Power button to confirm

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## 2. Run the Pebble Registration Tool

{% hint style="info" %}
Ensure your Pebble Tracker is in **Device Registration** mode and it's **connected** to the USB port of your PC.
{% endhint %}

{% tabs %}
{% tab title="Windows" %}
* [Download PebbleDeviceRegister for Windows](https://drive.google.com/file/d/1sC726mMJXKq8kbwfD7ssYHnEQuCcq-Gi/view?usp=sharing)
* Extract and run `DeviceRegister.exe`
* The tool requires access to the serial ports confirm the request when needed
{% endtab %}

{% tab title="Linux" %}
* [Download PebbleDeviceRegister for Linux](https://drive.google.com/file/d/1l-T_rEHnGG0VyKh3Ss6a-3iIGJaIXt9U/view?usp=sharing)
* Ensure the file is executable (right-click→properties)
* Run `DeviceRegister_Linux.AppImage` (the tool requires access to the serial port, please run as administrator if needed)
{% endtab %}
{% endtabs %}

In Pebble Device Registartion Tool, Select the Serial port corresponding to Pebble and click "Open". Click the `DID` and `DIDdoc` buttons to retrieve the DID info from your Pebble Tracker. If needed, you can disconnect/reconnect Pebble and use the `Refresh` button to update the serial posrts list:

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## 3. Open the IoTeX Hub Portal

{% hint style="info" %}
Ensure your Pebble Tracker is connected and the Registration Tool is running.

See the previous[#id-2.-run-the-pebble-registration-tool](device-registration.md#id-2.-run-the-pebble-registration-tool "mention") section.
{% endhint %}

* Open the new [Pebble Tracker Registration](https://hub.iotex.io/device-registration) portal on IoTex Hub portal in your browser
* Connect your Metamask Wallet
* Ensure IoTeX Mainnet is selected
* Look for your device in the list
* Click the `Register` button

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption><p>hub.iotex.io/device-registration</p></figcaption></figure>

{% hint style="success" %}
## Congrats!

Your Pebble Tracker is now successfully registered on the IoTeX blockchain and linked to your wallet as the device owner.
{% endhint %}

Your Pebble is now ready to send trusted IoT data to IoTeX DApps and support the creation of verifiable DePIN (Decentralized Physical Infrastructure) projects, leveraging user data contribution like location, weather data, movement, light, etc!

Here is what your Pebble screen should look like:

<figure><img src="../../../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>

By default, the factory configuration will collect all Pebble sensors data, and send one data message every 5 minutes to IoTeX Dapps.

{% hint style="success" %}
Stay tuned for upcoming updates and new Pebble Tracker features on the IoTeX Hub Portal!
{% endhint %}
