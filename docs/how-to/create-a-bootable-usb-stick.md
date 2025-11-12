(create-a-bootable-usb-stick)=
# Create a bootable USB stick

With a bootable Ubuntu USB stick, you can:

-   Install or upgrade Ubuntu
-   Test out the Ubuntu desktop experience without touching your PC configuration
-   Boot into Ubuntu on a borrowed machine or from an internet cafe
-   Use tools installed by default on the USB stick to repair or fix a broken configuration

## Using Rufus

<!--
Originally a Tutorial: https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-with-rufus-on-windows/14020
| Summary | How to write a USB stick with Windows. |
| Author |  <oliversmith@canonical.com> |
-->

This tutorial will show you how to create a bootable USB stick on Microsoft Windows using [Rufus](https://rufus.ie/).

Alternatively, we also have tutorials to help you create a bootable USB stick from both [Ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu) and [Apple macOS](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos).

![image](upload://23LTbqL4OqxptcHcnBQTbZXLWI8.jpeg)

### Requirements

You will need:

-   A 4GB or larger USB stick/flash drive
-   Microsoft Windows XP or later
-   [Rufus](https://rufus.ie/), a free and open source USB stick writing tool
-   An Ubuntu ISO file. See [Get Ubuntu](https://www.ubuntu.com/download) for download links

![ubuntu-download-18_04_1|690x467](upload://sfpe0p9WfvuNEfaEvSeHPucDFaW.png)

> ⓘ  Take note of where your browser saves downloads: this is normally a directory called 'Downloads' on your Windows PC. Don't download the ISO image directly to the USB stick! If using Windows XP or Vista, download version 2.18 of Rufus.

### USB selection

Perform the following to configure your USB device in Rufus:

1.  Launch Rufus
2.  Insert your USB stick
3.  Rufus will update to set the device within the **Device** field
4.  If the **Device** selected is incorrect (perhaps you have multiple USB storage devices), select the correct one from the device field's drop-down menu

![ubuntu-rufus-00|690x774, 75%](upload://A6jo79NUolk8AGkE95MoVzIk73Z.png)

> ⓘ  You can avoid the hassle of selecting from a list of USB devices by ensuring no other devices are connected.

### Select the Ubuntu ISO file

To select the Ubuntu ISO file you downloaded previously, click the **SELECT** to the right of "Boot selection". If this is the only ISO file present in the Downloads folder you will only see one file listed.

Select the appropriate ISO file and click on **Open**.

![ubuntu-rufus-01|690x615](upload://5R3GkC8jEnY4GPwnoB6B1Xm1qdw.png)

### Write the ISO

The *Volume label* will be updated to reflect the ISO selected.

Leave all other parameters with their default values and click **START** to initiate the write process.

![ubuntu-rufus-02|690x840, 75%](upload://j5WXWjEMSFYmiZRhpYokkTUkc6d.png)

### Additional downloads

You may be alerted that Rufus requires additional files to complete writing the ISO. If this dialog box appears, select **Yes** to continue.

![windows-rufus3-additional-downloads|431x317](upload://1Ox7sTVYswXpFrhjr13zNKAzsLJ.png)

### Write warnings

You will then be alerted that Rufus has detected that the Ubuntu ISO is an *ISOHybrid image*. This means the same image file can be used as the source for both a DVD and a USB stick without requiring conversion.

Keep *Write in ISO Image mode* selected and click on **OK** to continue.

![ubuntu-rufus-03|690x781, 75%](upload://eFmBBlIG00Ya0NAq5g3i6k4rtcp.png)

Rufus will also warn you that all data on your selected USB device is about to be destroyed. This is a good moment to double check you've selected the correct device before clicking **OK** when you're confident you have.

![ubuntu-rufus-04|690x291, 75%](upload://xuLUsADTPpYEJvmUK3l0VfV3ys9.png)

> ⓘ  If your USB stick contains multiple partitions Rufus will warn you in a separate pane that these will also be destroyed.

### Writing the ISO

The ISO will now be written to your USB stick, and the progress bar in Rufus will give you some indication of where you are in the process. With a reasonably modern machine, this should take around 10 minutes. Total elapsed time is shown in the lower right corner of the Rufus window.

![ubuntu-rufus-05|690x840, 75%](upload://c68j4YKTZgTa4z7ZPKEEuxfvQ1x.png)

### Installation complete

When Rufus has finished writing the USB device, the Status bar will be filled green and the word **READY** will appear in the center. Select **CLOSE** to complete the write process.

![ubuntu-rufus-06|690x840, 75%](upload://knXatxQrupES6JFo9CDed96qf8p.png)

Congratulations! You now have Ubuntu on a USB stick, bootable and ready to go.

To use it you need to insert the stick into your target PC or laptop and reboot the device. It should recognise the installation media automatically during startup but you may need to hold down a specific key (usually F12) to bring up the boot menu and choose to boot from USB.

For a full walkthrough of installing Ubuntu, take a look at our [install Ubuntu desktop tutorial](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview).


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
