(create-a-bootable-usb-stick)=
# Create a bootable USB stick

With a bootable Ubuntu USB stick, you can:

-   Install or upgrade Ubuntu
-   Test out the Ubuntu desktop experience without touching your PC configuration
-   Boot into Ubuntu on a borrowed machine or from an internet cafe
-   Use tools installed by default on the USB stick to repair or fix a broken configuration

You will need:

-   A 8GB or larger USB stick (flash drive)
-   An Ubuntu ISO file. See [Get Ubuntu](https://www.ubuntu.com/download) for download links

![Download an Ubuntu ISO](https://assets.ubuntu.com/v1/647dd5d0-bionic-download.png)

![Ubuntu download page](/images/rufus/ubuntu-download-18_04_1.png)

:::{note}
Take note of where your browser saves downloads: this is normally a directory called 'Downloads' on your Windows PC. Don't download the ISO image directly to the USB stick!
:::


## On Ubuntu and other Linux

### Using Disks

1. Insert your USB flash drive.

1. Open the Disks application.

1. In the side bar, select your USB stick.

1. In the window header, click {guilabel}`Drive Options` ({guilabel}`⋮`).

1. Select {guilabel}`Restore Disk Image…`

1. Select the downloaded Ubuntu image file.

1. Click {guilabel}`Start Restoring…`

### Using Startup Disk Creator

<!--
Originally a Tutorial: https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-ubuntu/14011/
| Summary | Use your Ubuntu desktop to create a bootable USB stick that can be used to run and install Ubuntu on any USB-equipped PC. |
| Author | Canonical Web Team <webteam@canonical.com> |
-->

Creating a bootable Ubuntu USB stick is very simple, especially from Ubuntu itself, and we're going to cover the process in the next few steps.

#### Launch Startup Disk Creator

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

#### ISO and USB selection

When launched, Startup Disk Creator will look for the ISO files in your *Downloads* folder, as well as any attached USB storage it can write to.

It's likely that both your Ubuntu ISO and the correct USB device will have been detected and set as 'Source disc image' and 'Disk to use' in the application window. If not, use the 'Other' button to locate your ISO file and select the exact USB device you want to use from the list of devices.

Click **Make Startup Disk** to start the process.

![Make USB device](https://assets.ubuntu.com/v1/48c17275-bionic-make-startup-disk.png)

#### Confirm USB device

Before making any permanent changes, you will be asked to confirm the USB device you've chosen is correct. This is important because any data currently stored on this device will be destroyed.

After confirming, the write process will start and a progress bar appears.

![USB write progress](https://assets.ubuntu.com/v1/af6b2c2a-bionic-usb-progress.png)

#### Installation complete

That's it! You now have Ubuntu on a USB stick, bootable and ready to go.

![USB write complete](https://assets.ubuntu.com/v1/d4690a43-bionic-usb-complete.png)


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

Creating a bootable USB stick is very simple, especially if you're going to use the USB stick with a generic Windows or Linux PC. We're going to cover the process in the next few steps.

### Apple hardware considerations

There are a few additional considerations when booting the USB stick on Apple hardware. This is because Apple's 'Startup Manager', summoned by holding the {kbd}`Option` or {kbd}`Alt` ({kbd}`⌥`) key when booting, won't detect the USB stick without a specific partition table and layout. We'll cover this in a later step.

### Prepare the USB stick

To ensure maximum compatibility with Apple hardware, we're going to first blank and reformat the USB stick using Apple's 'Disk Utility'. But this step can be skipped if you intend to use the USB stick with only generic PC hardware.

1. Launch *Disk Utility* from {menuselection}`Applications --> Utilities` or from the Spotlight search.
1. Insert your USB stick and observe the new device added to Disk Utility.
1. Select the USB stick device. You might need to enable the option {menuselection}`View --> Show All Devices`.
1. Select {guilabel}`Erase` from the tool bar or right-click menu.
1. Set the format to {guilabel}`MS-DOS (FAT)` and the scheme to {guilabel}`GUID Partition Map`.
1. Check that you've chosen the correct device.
1. Click {guilabel}`Erase`.

![The fialog in Disk Utility to erase the USB drive](https://assets.ubuntu.com/v1/22cad904-prepare-usb-stick.png)

:::{warning}
Disk Utility needs to be used with caution as selecting the wrong device or partition can result in data loss.
:::

### Install and run Etcher

To write the ISO file to the USB stick, we're going to use a free and open source application called [Etcher](https://etcher.balena.io/). After downloading this and clicking to mount the package, Etcher can either be run in-place or dragged into your Applications folder.

By default, recent versions of macOS block the running of applications from unidentified developers. To side-step this issue, enable 'App Store and identified developers' in the 'Security & Privacy' pane of System Preferences. If you are still warned against running the application, click 'Open Anyway' in the same pane.

![screenshot](upload://lUpv9mKzalQWNWwN2itWQzXGQsI.jpeg)

### Etcher configuration

Etcher will configure and write to your USB device in three stages:

1. **Select image** will open a file requester from which should navigate to and select the ISO file downloaded previously. By default, the ISO file will be in your *Downloads* folder.

1. **Select drive**, replaced by the name of your USB device if one is already attached, lets you select your target device. You will be warned if the storage space is too small for your selected ISO.

1. **Flash!** will activate when both the image and the drive have been selected. As with Disk Utility, Etcher needs low-level access to your storage hardware and will ask for your password after selection.

![screenshot](upload://pM1UmUK5i54SyL7MvmyAei0nJqM.jpeg)

### Write to device

After entering your password, Etcher will start writing the ISO file to your USB device.

The *Flash* stage of the process will show progress, writing speed and an estimated duration until completion. This will be followed by a validation stage that will ensure the contents of the USB device are identical to the source image.

When everything has finished, Etcher will declare the process a success.

Congratulations! You now have Ubuntu on a USB stick, bootable and ready to go.

![screenshot](upload://lzHQa67pws8dxNB4iZQO6xGrMqG.jpeg)

:::{warning}
After the write process has completed, macOS might inform you that "The disk you inserted was not readable by this computer". Select {guilabel}`Eject` and remove the USB device. Don't select {guilabel}`Initialize`.
:::

### Boot your Mac

If you want to use your USB stick with an Apple Mac, restart or power-on the Mac with the USB stick inserted **while** the {kbd}`Option` or {kbd}`Alt` ({kbd}`⌥`) key is pressed.

This launches Apple's 'Startup Manager' which shows bootable devices connected to the machine. Your USB stick should appear as gold or yellow and be labeled 'EFI Boot'. Selecting this will lead you to the standard Ubuntu boot menu.

![Boot device selection](/images/macos-usb-efi-boot.png)

### Alternative resources

If you feel confident using the macOS command line, see the community documentation on [How to install Ubuntu on MacBook using USB Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) for a more manual approach.


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
