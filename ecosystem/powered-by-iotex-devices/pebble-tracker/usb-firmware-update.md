# USB Firmware Update

USB Firmware update  method is ideal in the following situations:

* You don’t yet have a SIM card installed in your Pebble Tracker.
* The IoT cellular connection in your area is weak or unreliable.
* You don't have data credit or prefer to save data usage on your IoT data plan.

You can easily upgrade the firmware of your Pebble Tracker offline by following these steps:

## **Download the latest firmware file**

* Visit the official GitHub repository for your Pebble Tracker firmware, link below.
* Ensure you download the file with a `.hex` extension.

{% embed url="https://github.com/iotexproject/pebble-apps/releases" %}

## **Install and run Pebble USB Tools**

{% tabs %}
{% tab title="macOS" %}
1. Download and install the latest [VCP Drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) for macOS
2. Download, unzip, right→click and open the app file: [`PebbleUSBTool`](https://drive.google.com/file/d/1ITgxkicc5WcSFcB0Q5i42JHcPau31ZpX/view?usp=share_link)

**Note**: If you see an error message from MacOS stating that it cannot run PebbleUSBTools because of security reasons, follow the steps below:

* Open `Settings` → `Privacy & Security`
* Scroll down to the `Security` section&#x20;
* Find the "`PebbleUSBTools ws blocked to protect your Mac`" message
* Click the `Open Anyway` button and confirm the exception
* Open the PebbleUSBTools app again.
{% endtab %}

{% tab title="Windows" %}
1. Download and install the latest [VCP Driver for Windows](https://www.silabs.com/documents/public/software/CP210x_Universal_Windows_Driver.zip)
2. Unzip and run the executable file: [`PebbleUSBTools.exe`](https://drive.google.com/file/d/1Sjvz7v1rP1iHvdpBiKCUmYMPhsCp8HGW/view?usp=share_link)
{% endtab %}

{% tab title="Linux" %}
1. Download and unzip [PebbleUSBTools](https://drive.google.com/file/d/1TfuAfpNCKNKDWboF9NbrGlEEeWgp1MAW/view?usp=share_link)
2. Enter the `PebbleUSBTool` folder
3. Install `pebble-udev_1.0.1-all.deb`
4. `chmod +777 PebbleUSBTools`
5. Reboot your system
6. Inside the PebbleUSBTool folder run `./PebbleUSBTools`
{% endtab %}
{% endtabs %}

## **Flash the firmware**

* **Ensure Pebble USB Tool is running.**
* **Connect Pebble to your computer:** Use the micro-USB data cable provided with Pebble to connect the device to your computer using a USB port.
* **Press and keep pressing** the `Confirm/Power` button then, while you keep pressing it, use a pin or a SIM card tool to press the hardware reset button (it's located in the tiny hole next to the SIM card holder).
* **Wait for the red led to light** on then release the power button: Pebble is now in USB firmware update mode

{% hint style="warning" %}
Please note that will have about 20 seconds to perform the update step before the device will reboot if no action is taken.
{% endhint %}

* **Wait for Pebble Connection** In the Pebble USB Tool, watch for the status bar to confirm that your Pebble Tracker is connected. Once it indicates a successful connection, you can proceed with flashing the firmware:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/image%20(104).png" alt=""><figcaption></figcaption></figure>

* **Flash the Firmware:** click the “`Flash APP Firmware`” button and follow the flashing progress in the log area:

<figure><img src="https://github.com/iotexproject/iotex-docs-gitbook/raw/master/.gitbook/assets/image%20(84).png" alt=""><figcaption></figcaption></figure>

The device will automatically reboot once the operation is complete, loading the new firmware successfully.

{% hint style="success" %}
If you just upgraded from Pebble Software version `1.0.x` to `2.0`  please complete the migration by following the [device-registration.md](device-registration.md "mention") guide.
{% endhint %}
