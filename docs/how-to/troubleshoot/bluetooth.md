(troubleshoot-bluetooth)=
# Bluetooth 

As the Bluetooth stack is complex, multiple reasons may cause problems with Bluetooth devices such as phones or headsets.

If you do not know why the problem is happening, first consult the [Hardware problems](https://help.ubuntu.com/stable/ubuntu-help/bluetooth.html.en#problems) section or create a [thread on the Discourse](https://discourse.ubuntu.com/c/support-and-help/306) with a detailed description of your problem.

(proprietary-firmware)=
## Proprietary firmware

Many Bluetooth adapters require proprietary firmware that may not be included in Desktop by default for licensing reasons. 
To resolve this, you need to download and install drivers for your device manually. Consult your device manufacturer's documentation to find where the drivers can be downloaded from.

Check the logs to see if the issue is caused by missing firmware:

    journalctl --dmesg | grep -i 'firmware load'

The log entry might look similar to this example:

    kernel: Bluetooth: hci0: Direct firmware load for <path>/<driver-name> failed with error -2

This error indicates what driver the kernel attempts to load and where it expect to find it. Once you have the name, you can download the driver from its manufacturer and place it in `/lib/firmware/<path>` . For example, Broadcom drivers are expected to be placed in under `/lib/firmware/brcm`.

### See also

* [Hardware problems](https://help.ubuntu.com/stable/ubuntu-help/bluetooth.html.en#problems)
* [PipeWire troubleshooting guide](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Troubleshooting#bluetooth)
