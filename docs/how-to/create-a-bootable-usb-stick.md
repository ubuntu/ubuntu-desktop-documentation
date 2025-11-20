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

1. Open the Disks application. You can find it in the applications menu or by searching for "Disks".

1. Insert your USB stick. It appears in the sidebar. Select it there.

    :::{warning}
    Make sure to select the USB stick and **not** the disk with your running system. Both are listed.
    :::

    ![A USB stick selected in Disks](/images/usb-in-gnome-disks.png)

1. In the window header, click {guilabel}`Drive Options` ({guilabel}`⋮`) and select {guilabel}`Restore Disk Image…`

    ![Restore Disk Image in the menu](/images/restore-disk-image-menu.png)

1. Next to {guilabel}`Image to Restore`, select the downloaded Ubuntu image file.

1. Click {guilabel}`Start Restoring…` and confirm. The application asks for your password.

    ![The Restore Disk Image dialog](/images/restore-disk-image-dialog.png)

1. A progress bar appears while Disks is writing the image.

    ![Disks writing the image to USB](/images/gnome-disks-restoring-image.png)

1. When the progress bar finishes, click {guilabel}`Eject this disk` ({guilabel}`⏏`).

    ![Writing finished. Partitions are listed on the USB](/images/gnome-disks-finished-writing.png)

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

### Using Rufus

<!--
Originally a Tutorial: https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-with-rufus-on-windows/14020
| Summary | How to write a USB stick with Windows. |
| Author |  <oliversmith@canonical.com> |
-->

This tutorial will show you how to create a bootable USB stick on Microsoft Windows using [Rufus](https://rufus.ie/).

You will need:

-   Microsoft Windows XP or later.
-   [Rufus](https://rufus.ie/), a free and open source USB stick writing tool. If using Windows XP or Vista, download version 2.18 of Rufus.

#### USB selection

Perform the following to configure your USB device in Rufus:

1.  Launch Rufus
2.  Insert your USB stick
3.  Rufus will update to set the device within the {guilabel}`Device` field
4.  If the {guilabel}`Device` selected is incorrect (perhaps you have multiple USB storage devices), select the correct one from the device field's drop-down menu

![Selecting a USB drive in Rufus](/images/rufus/ubuntu-rufus-00.png)

:::{note}
You can avoid the hassle of selecting from a list of USB devices by ensuring no other devices are connected.
:::

#### Select the Ubuntu ISO file

To select the Ubuntu ISO file you downloaded previously, click the {guilabel}`SELECT` to the right of "Boot selection". If this is the only ISO file present in the Downloads folder you will only see one file listed.

Select the appropriate ISO file and click on {guilabel}`Open`.

![Selecting the ISO file in the file browser](/images/rufus/ubuntu-rufus-01.png)

#### Write the ISO

The *Volume label* will be updated to reflect the ISO selected.

Leave all other parameters with their default values and click {guilabel}`START` to initiate the write process.

![Rufus ready to start writing the ISO](/images/rufus/ubuntu-rufus-02.png)

#### Additional downloads

You may be alerted that Rufus requires additional files to complete writing the ISO. If this dialog box appears, select {guilabel}`Yes` to continue.

![The "Download required" dialog](/images/rufus/windows-rufus3-additional-downloads.png)

#### Write warnings

You will then be alerted that Rufus has detected that the Ubuntu ISO is an *ISOHybrid image*. This means the same image file can be used as the source for both a DVD and a USB stick without requiring conversion.

Keep *Write in ISO Image mode* selected and click on {guilabel}`OK` to continue.

!["ISOHybrid image detected" dialog](/images/rufus/ubuntu-rufus-03.png)

Rufus will also warn you that all data on your selected USB device is about to be destroyed. This is a good moment to double check you've selected the correct device before clicking {guilabel}`OK` when you're confident you have.

![Rufus warning you about data loss](/images/rufus/ubuntu-rufus-04.png)

:::{note}
If your USB stick contains multiple partitions Rufus will warn you in a separate pane that these will also be destroyed.
:::

#### Writing the ISO

The ISO will now be written to your USB stick, and the progress bar in Rufus will give you some indication of where you are in the process. With a reasonably modern machine, this should take around 10 minutes. Total elapsed time is shown in the lower right corner of the Rufus window.

![Rufus copying ISO files](/images/rufus/ubuntu-rufus-05.png)

#### Installation complete

When Rufus has finished writing the USB device, the Status bar will be filled green and the word {guilabel}`READY` will appear in the center. Select {guilabel}`CLOSE` to complete the write process.

![Rufus finished writing the ISO](/images/rufus/ubuntu-rufus-06.png)


## On macOS

<!--
Originally a Tutorial: https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-macos/14016
| Summary | How to write a USB stick with macOS. |
| Author | Canonical Web Team <webteam@canonical.com> |
-->

You can use built-in tools on macOS to create an Ubuntu USB stick. The USB stick will work on **PC (Windows) hardware** and older Apple hardware based on **Intel CPUs**.

If you want to install Ubuntu on **Apple Silicon** hardware, such as recent Macs using M1 CPUs or later, refer instead to the [Ubuntu Asahi](https://ubuntuasahi.org/) community project. The hardware support might be limited and depends on your specific machine.

### Using the Disk Utility

The Disk Utility is preinstalled on macOS and you can use it to write any image to your USB stick.

1. Launch the *Disk Utility* app from {menuselection}`Applications --> Utilities` or from the Spotlight search.

1. Insert your USB stick. It appears in the sidebar. Select it there.

    You might need to enable the {menuselection}`View --> Show All Devices` option.

    :::{warning}
    Make sure to select the USB stick and **not** your internal macOS disk. Both are listed.
    :::

1. To ensure compatibility with Apple hardware, reformat the USB stick with the GUID partition table:

    Select {guilabel}`Erase` from the toolbar.

    Set the format to *MS-DOS (FAT)* and the scheme to *GUID Partition Map*.

    Check that you've chosen the correct device and click {guilabel}`Erase`.

1. Click {guilabel}`Restore` ({guilabel}`↺`) in the toolbar.

1. Click {guilabel}`Image…` and select the Ubuntu image file.

1. Click {guilabel}`Restore`.

1. Wait for the writing to finish.

1. After the write process has completed, macOS might inform you that "The disk you inserted was not readable by this computer".

    Select {guilabel}`Eject` and remove the USB device. Don't select {guilabel}`Initialize`.

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
