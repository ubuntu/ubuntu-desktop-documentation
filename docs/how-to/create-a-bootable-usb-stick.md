(create-a-bootable-usb-stick)=
# Create a bootable USB stick

You can convert your USB stick (USB flash drive) into Ubuntu installation media. This is different from copying a file to the USB stick. Instead, use a specialized application to rewrite your USB stick with Ubuntu. Select an application depending on the system that you're currently using.

With a bootable Ubuntu USB stick, you can:

-   Install or upgrade Ubuntu.
-   Test out the Ubuntu Desktop experience without touching your PC configuration.
-   Boot into Ubuntu on a borrowed machine.
-   Use tools from the USB stick to repair or fix a broken configuration.

You need:

-   An 8GB USB stick or larger.
-   An Ubuntu image file. See [Download Ubuntu Desktop](https://ubuntu.com/download/desktop).

:::{note}
Take note of where your browser saves the downloaded file. This is normally a directory called *Downloads*.

Don't download the ISO image directly to the USB stick.
:::

## On Ubuntu and other Linux distributions

Ubuntu Desktop comes with the Disks application by default, which you can use to write the image. Other Linux distributions provide a wide range of different image writer applications. Choose the first one that's available on your system.

### Using Disks

The Disks application is installed by default on Ubuntu Desktop and on most Linux distributions that use the GNOME desktop environment. We recommend choosing it if it's available on your system.

Disks can also write images of any other operating system, including Linux distributions or Microsoft Windows.

<!--
The docs/reuse/usb-using-gnome-disks.txt file is reused between the live system tutorial, the installation tutorial and the bootable USB how-to guide.
-->
```{include} ../reuse/usb-using-gnome-disks.txt
```

### Using Startup Disk Creator

<!--
Originally a Tutorial: https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-ubuntu/14011/
| Summary | Use your Ubuntu desktop to create a bootable USB stick that can be used to run and install Ubuntu on any USB-equipped PC. |
| Author | Canonical Web Team <webteam@canonical.com> |
-->

The Startup Disk Creator application is part of the extended Ubuntu Desktop installation. You can use it to write an Ubuntu image to a USB stick.

:::{warning}
Startup Disk Creator also works with images of other distributions based on Ubuntu, such as flavors like Kubuntu or Xubuntu, or derived distributions. It might not work correctly with other Linux distributions and different operating systems.
:::

1. Insert your USB stick.

    <!--
    If Ubuntu asks you what to do with it, select {guilabel}`Do nothing`.
    -->

1. Search your applications for *Startup Disk Creator*.

    ![Launch Startup Disk Creator](/images/launch-startup-disk-creator.png)

1. If the application isn't available, install it in the App Center.

    Alternatively, you can install it on the command line:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo apt install usb-creator-gtk
    ```

1. Open Startup Disk Creator.

1. Check the {guilabel}`Source disc image` and {guilabel}`Disk to use` fields.

    It's likely that your Ubuntu image and the correct USB device have been detected. If not, use the {guilabel}`Other` button to locate your image file and select the USB device that you want to use from the list of devices.

    ![The Make Startup Disk window with Ubuntu 24.04 and a USB drive](/images/startup-disk-creator.png)

1. Click {guilabel}`Make Startup Disk` and confirm that this is the correct USB device.

    Any data currently stored on this device will be **destroyed**.

1. The write process starts and a progress bar appears.

    When finished, the application announces "Installation Complete".

That's it! You now have Ubuntu on a USB stick.


## On Windows

On Microsoft Windows, you have to install a third-party application for writing images to USB sticks.

### Using Rufus

You can create a bootable USB stick using [Rufus](https://rufus.ie/), a free and open source USB stick writing tool. You need Microsoft Windows XP or later.

<!--
The docs/reuse/usb-using-rufus.txt file is reused between the live system tutorial, the installation tutorial and the bootable USB how-to guide.
-->
```{include} ../reuse/usb-using-rufus.txt
```


## On macOS

You can use built-in tools on macOS to create an Ubuntu USB stick. The USB stick will work on **PC (Windows) hardware** and older Apple hardware based on **Intel CPUs**.

If you want to install Ubuntu on **Apple Silicon** hardware, such as recent Macs using M1 CPUs or later, refer instead to the [Ubuntu Asahi](https://ubuntuasahi.org/) community project. The hardware support might be limited and depends on your specific machine.

### Using the Disk Utility

The Disk Utility is preinstalled on macOS and you can use it to write any image to your USB stick.

<!--
The docs/reuse/usb-using-macos-disk-utility.txt file is reused between the live system tutorial, the installation tutorial and the bootable USB how-to guide.
-->
```{include} ../reuse/usb-using-macos-disk-utility.txt
```

### Using the command line

If you feel confident using the macOS command line, see the community documentation on [How to install Ubuntu on MacBook using USB Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) for a more manual approach.

<!--
TODO: Convert this wiki page into product documentation.
-->


## On any platform

### Using balenaEtcher

:::{note}
balenaEtcher is an open-source application but it isn't developed by the Ubuntu community. Recently, we've [learned](https://tails.net/news/rufus/) that it shares some information about your usage with the Balena company. If this a concern, consider using an alternative application: Startup Disk Creator or GNOME Disks on Linux, Rufus on Windows or Raspberry Pi Imager on any platform.
:::

1. At the [balenaEtcher website](https://etcher.balena.io/), choose the version that corresponds to your current operating system.

1. Download and install the tool.

    ![The Download Etcher page](/images/download-etcher.png)

1. Insert your USB flash drive.

1. Open balenaEtcher.

1. Select the downloaded Ubuntu image and your USB flash drive.

    ![The Select target step in Etcher](/images/select-iso.png)

1. Click {guilabel}`Flash!` to write the image.


## Next steps

Congratulations! You now have Ubuntu on a USB stick, bootable and ready to go.

To use it you need to insert the stick into your target PC or laptop and reboot the device. It should recognize the installation media automatically during startup but you may need to hold down a specific key (usually {kbd}`F12`) to bring up the boot menu and choose to boot from USB.

For a full walkthrough of installing Ubuntu, take a look at our {ref}`install-ubuntu-desktop` tutorial.


## Finding help

If you get stuck, help is always at hand:

-  [Ubuntu Discourse](https://discourse.ubuntu.com/)
-  [Ask Ubuntu](https://askubuntu.com/)
-  [IRC-based support](https://wiki.ubuntu.com/IRC/ChannelList)
