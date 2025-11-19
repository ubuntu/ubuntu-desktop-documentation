(create-a-bootable-usb-stick)=
# Create a bootable USB stick

With a bootable Ubuntu USB stick, you can:

-   Install or upgrade Ubuntu
-   Test out the Ubuntu desktop experience without touching your PC configuration
-   Boot into Ubuntu on a borrowed machine or from an internet cafe
-   Use tools installed by default on the USB stick to repair or fix a broken configuration


## Using Startup Disk Creator

<!--
Originally a Tutorial: https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-ubuntu/14011/
| Summary | Use your Ubuntu desktop to create a bootable USB stick that can be used to run and install Ubuntu on any USB-equipped PC. |
| Author | Canonical Web Team <webteam@canonical.com> |
-->

Creating a bootable Ubuntu USB stick is very simple, especially from Ubuntu itself, and we're going to cover the process in the next few steps.

Alternatively, we also have tutorials to help you create a bootable USB stick from both [Microsoft Windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows) and [Apple macOS](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos).

### Requirements

You will need:

-   A 6GB or larger USB stick/flash drive
-   Ubuntu Desktop 18.04 or later installed
-   An Ubuntu ISO file. See [Get Ubuntu](https://www.ubuntu.com/download) for download links

![Download an Ubuntu ISO](https://assets.ubuntu.com/v1/647dd5d0-bionic-download.png)

### Launch Startup Disk Creator

We're going to use an application called 'Startup Disk Creator' to write the ISO image to your USB stick. This is installed by default on Ubuntu, and can be launched as follows:

1.  Insert your USB stick (select 'Do nothing' if prompted by Ubuntu)
2.  On Ubuntu 18.04 and later, use the bottom left icon to open 'Show Applications'
3.  In older versions of Ubuntu, use the top left icon to open the dash
4.  Use the search field to look for *Startup Disk Creator*
5.  Select **Startup Disk Creator** from the results to launch the application

![Search for Startup Disk Creator](https://assets.ubuntu.com/v1/ed29b466-bionic-search-apps.png)

In case the **Startup Disk Creator** is not installed, install it in a terminal by running:

```bash
sudo apt install usb-creator-gtk
```

### ISO and USB selection

When launched, Startup Disk Creator will look for the ISO files in your *Downloads* folder, as well as any attached USB storage it can write to.

It's likely that both your Ubuntu ISO and the correct USB device will have been detected and set as 'Source disc image' and 'Disk to use' in the application window. If not, use the 'Other' button to locate your ISO file and select the exact USB device you want to use from the list of devices.

Click **Make Startup Disk** to start the process.

![Make USB device](https://assets.ubuntu.com/v1/48c17275-bionic-make-startup-disk.png)

### Confirm USB device

Before making any permanent changes, you will be asked to confirm the USB device you've chosen is correct. This is important because any data currently stored on this device will be destroyed.

After confirming, the write process will start and a progress bar appears.

![USB write progress](https://assets.ubuntu.com/v1/af6b2c2a-bionic-usb-progress.png)

### Installation complete

That's it! You now have Ubuntu on a USB stick, bootable and ready to go.

![USB write complete](https://assets.ubuntu.com/v1/d4690a43-bionic-usb-complete.png)


## Using Rufus

<!--
Originally a Tutorial: https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-with-rufus-on-windows/14020
| Summary | How to write a USB stick with Windows. |
| Author |  <oliversmith@canonical.com> |
-->

This tutorial will show you how to create a bootable USB stick on Microsoft Windows using [Rufus](https://rufus.ie/).

Alternatively, we also have tutorials to help you create a bootable USB stick from both [Ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu) and [Apple macOS](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos).

### Requirements

You will need:

-   A 4GB or larger USB stick/flash drive
-   Microsoft Windows XP or later
-   [Rufus](https://rufus.ie/), a free and open source USB stick writing tool
-   An Ubuntu ISO file. See [Get Ubuntu](https://www.ubuntu.com/download) for download links

![Ubuntu download page](/images/rufus/ubuntu-download-18_04_1.png)

:::{note}
Take note of where your browser saves downloads: this is normally a directory called 'Downloads' on your Windows PC. Don't download the ISO image directly to the USB stick! If using Windows XP or Vista, download version 2.18 of Rufus.
:::

### USB selection

Perform the following to configure your USB device in Rufus:

1.  Launch Rufus
2.  Insert your USB stick
3.  Rufus will update to set the device within the {guilabel}`Device` field
4.  If the {guilabel}`Device` selected is incorrect (perhaps you have multiple USB storage devices), select the correct one from the device field's drop-down menu

![Selecting a USB drive in Rufus](/images/rufus/ubuntu-rufus-00.png)

:::{note}
You can avoid the hassle of selecting from a list of USB devices by ensuring no other devices are connected.
:::

### Select the Ubuntu ISO file

To select the Ubuntu ISO file you downloaded previously, click the {guilabel}`SELECT` to the right of "Boot selection". If this is the only ISO file present in the Downloads folder you will only see one file listed.

Select the appropriate ISO file and click on {guilabel}`Open`.

![Selecting the ISO file in the file browser](/images/rufus/ubuntu-rufus-01.png)

### Write the ISO

The *Volume label* will be updated to reflect the ISO selected.

Leave all other parameters with their default values and click {guilabel}`START` to initiate the write process.

![Rufus ready to start writing the ISO](/images/rufus/ubuntu-rufus-02.png)

### Additional downloads

You may be alerted that Rufus requires additional files to complete writing the ISO. If this dialog box appears, select {guilabel}`Yes` to continue.

![The "Download required" dialog](/images/rufus/windows-rufus3-additional-downloads.png)

### Write warnings

You will then be alerted that Rufus has detected that the Ubuntu ISO is an *ISOHybrid image*. This means the same image file can be used as the source for both a DVD and a USB stick without requiring conversion.

Keep *Write in ISO Image mode* selected and click on {guilabel}`OK` to continue.

!["ISOHybrid image detected" dialog](/images/rufus/ubuntu-rufus-03.png)

Rufus will also warn you that all data on your selected USB device is about to be destroyed. This is a good moment to double check you've selected the correct device before clicking {guilabel}`OK` when you're confident you have.

![Rufus warning you about data loss](/images/rufus/ubuntu-rufus-04.png)

:::{note}
If your USB stick contains multiple partitions Rufus will warn you in a separate pane that these will also be destroyed.
:::

### Writing the ISO

The ISO will now be written to your USB stick, and the progress bar in Rufus will give you some indication of where you are in the process. With a reasonably modern machine, this should take around 10 minutes. Total elapsed time is shown in the lower right corner of the Rufus window.

![Rufus copying ISO files](/images/rufus/ubuntu-rufus-05.png)

### Installation complete

When Rufus has finished writing the USB device, the Status bar will be filled green and the word {guilabel}`READY` will appear in the center. Select {guilabel}`CLOSE` to complete the write process.

![Rufus finished writing the ISO](/images/rufus/ubuntu-rufus-06.png)


## Using balenaEtcher

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
