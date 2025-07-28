(install-ubuntu-desktop)=
# Install Ubuntu Desktop

<!--
Original source: <https://discourse.ubuntu.com/t/install-ubuntu-desktop/25312/>
Original author: Oliver Smith <oliversmith@canonical.com>
-->

In this tutorial, we will guide you through the steps required to install Ubuntu Desktop on your laptop or PC.

What you’ll need:

* A laptop or PC with at least 25GB of storage space.

* A flash drive (12GB or above recommended).

:::{note}
Whilst Ubuntu works on a wide range of devices, it is recommended that you use a device listed on the [Ubuntu certified hardware](https://ubuntu.com/certified?q=&limit=20&category=Desktop&category=Laptop) page. These devices have been tested and confirmed to work well with Ubuntu.
:::

:::{warning}
If you are installing Ubuntu on a PC or laptop you have used previously, it is always recommended to back up your data prior to installation.
:::

## Download an Ubuntu image

Get the Ubuntu image from the [Download Ubuntu Desktop](https://ubuntu.com/download/desktop) page. Save it to a memorable location on your PC! This tutorial uses the latest Ubuntu 24.04 LTS release (available on April 25th 2024), which features the new Ubuntu Desktop installer.

If you are installing an older version of Ubuntu, such as Ubuntu 22.04 LTS, you will find that the visual presentation of the installer is different, but the overall flow should remain similar.

![The Download Ubuntu Desktop page](/images/download-an-ubuntu-image.png)
 

## Create a bootable USB stick

To install Ubuntu Desktop, write your downloaded ISO to a USB stick to create the installation media. This is not the same as copying the ISO and requires some special software.

This tutorial uses [balenaEtcher](https://etcher.balena.io/) because it runs on Linux, Windows and macOS. Choose the version that corresponds to your current operating system, download and install the tool.

![The Download Etcher page](/images/download-etcher.png)

Select your downloaded ISO, choose your USB flash drive, and then click {guilabel}`Flash!` to write your image.

![The Select target step in Etcher](/images/select-iso.png)

## Boot from USB flash drive

Insert the USB flash drive into the laptop or PC you want to use to install Ubuntu and boot or restart the device. It should recognize the installation media automatically. If not, try holding {kbd}`F12` during startup and selecting the USB device from the system-specific boot menu.

:::{note}
{kbd}`F12` is the most common key for bringing up the system boot menu but {kbd}`Escape`, {kbd}`F2` and {kbd}`F10` are common alternatives. If unsure, look for a brief message when your system starts: this often informs you which key to press to access the boot menu.
:::

Once the installer has initialized, you are invited to choose your language.

![The Choose your language page](/images/installer/choose-your-language.jpeg)

And then presented with the option to select any accessibility settings your require.

![The Accessibility page](/images/installer/accessibility.jpeg)

Your keyboard layout.

![The Keyboard layout page](/images/installer/keyboard-layout.jpeg)

And connect to your network. This allows Ubuntu to download updates and third party drivers (such as NVIDIA graphics drivers) during installation.

![The Internet connection page](/images/installer/internet-connection.jpeg)

You are then offered the choice to try or install Ubuntu.

![The Try or install Ubuntu page](/images/installer/try-or-install-ubuntu.jpeg)

:::{note}
If you click {guilabel}`Try Ubuntu`, you can preview Ubuntu without making any changes to your PC. You can return to the installer menu at any time by clicking the {guilabel}`Install Ubuntu` shortcut on the desktop.
:::

To proceed, click {guilabel}`Install Ubuntu`.

:::{warning}
Some PCs use Intel RST (Rapid Storage Technology), which is not supported by Ubuntu. If this is the case, you will not be able to proceed beyond this point without disabling RST in the BIOS menu of your machine. If you encounter this alert, visit [help.ubuntu.com/rst](https://help.ubuntu.com/rst/) for more information.
:::

## Installation setup

You will be prompted to choose between {guilabel}`Interactive installation` and {guilabel}`Automated Installation`. The interactive option is the standard route, but more advanced users can use the automated installation option to import a configuration file from a web server to standardize multiple installs and add further customization. An example tutorial for Automated installation is available at [Getting started with Autoinstall on Ubuntu Desktop 24.04 LTS](https://blog.local-optimum.net/getting-started-with-autoinstall-on-ubuntu-desktop-24-04-lts-147a1defb2de).

![The Type of installation page](/images/installer/type-of-installation.jpeg)

In this tutorial we will remain on the primary route.

You will be prompted to choose between the {guilabel}`Default selection` and {guilabel}`Extended selection` options. The default installation comes with the basic essentials to get started which you can then expand on after install using the App Center. The extended selection contains additional office tools and utilities, useful for offline situations.

![The Applications page](/images/installer/applications.jpeg)

In the following screen you will be prompted to install third-party software that may improve device support and performance (for example, Nvidia graphics drivers) and support for additional media formats. It is recommended to check both of these boxes.

![The Optimise your computer page](/images/installer/optimise-your-computer.jpeg)


## Type of installation

This screen allows you to configure your installation. If you would like Ubuntu to be the only operating system on your hard drive, select {guilabel}`Erase disk and install Ubuntu`.

If your device currently has another operating system installed, you will receive additional options to install Ubuntu alongside that OS rather than replacing it.

![The Disk setup page](/images/installer/disk-setup.jpeg)

Let’s take a moment to review all of the above options in detail.

### Installing Ubuntu alongside another operating system

If you select this option you will be given a simple interface that allows you to select the drive you want to install Ubuntu on and a slider to determine the amount of disk space you would like Ubuntu to use. The available space is limited by the existing contents of the disk and is designed to avoid overwriting existing files.

This view automatically selects the largest partition on the drive. For more fine-grained control you can switch to the {guilabel}`Manual partitioning` option that is detailed further down.

![The Install Ubuntu alongside other partitions page](/images/installer/install-ubuntu-alongside-other-partitions.png) 

### Erase disk and install Ubuntu

If you select this option Ubuntu will take up the entire disk space on the selected drive.

![The Erase disk and install Ubuntu page](/images/installer/erase-disk-and-install-ubuntu.png) 

If your PC has multiple hard drives then this option allows you to install Ubuntu alongside an existing OS as long as they each have their own drive. Take care to ensure that you are selecting the right drive in this instance!

This option also allows you to encrypt your entire drive using LVM, ZFS or using the Trusted Platform Module on the device. To do this, open the {guilabel}`Advanced features` option before proceeding to the above screen and select {guilabel}`Encrypt the new Ubuntu installation for security`.

![The Advanced features dialog](/images/installer/advanced-features.jpeg)

:::{note}
LVM stands for Logical Volume Management. By using LVM during the setup, it makes it easier to create and manage partitions post installation.
:::

:::{note}
ZFS allows users to create pooled storage volumes that span multiple drives as well as snapshots and data repair features. It is a powerful option for advanced users.
:::

:::{warning}
TPM-backed full disk encryption is a new, highly experimental feature of Ubuntu Desktop that currently supports only the generic kernel. This means that machines that require additional drivers to support webcams or NVIDIA graphics cards will not support this setup until additional features land after release. In addition, certain hardware vendors may have BIOS options enabled that alter the chain of trust. Please do not select this option unless you are comfortable debugging or re-installing in the event of an issue.
:::

If you select either LVM or ZFS based encryption, you will be prompted to create a Security key that you will need to enter on boot before logging in with your user credentials.

![The Disk passphrase page](/images/installer/disk-passphrase.jpeg)

If you are using TPM-based Full Disk Encryption you will be prompted to run the following command after installing to generate a recovery key:

```bash
snap recovery --show-keys
```

:::{warning}
If you select encryption, it is important that you do not lose your security key. Write it down and store it in a safe place outside of your local system. **You will not be able to recover your data without it!**
:::

### Manual partitioning

Manual partitioning is designed for advanced users who want to create specific configurations for their use-cases. As such, we assume that these users will be comfortable with this interface and will not go into detail during this tutorial on specific setups.

Here, users can see all existing drives and partitions and create and manage new partition tables and configurations.

![The Manual partitioning page](/images/installer/manual-partitioning.png) 

### (Alert) Windows BitLocker is enabled

If your device has Windows BitLocker Drive Encryption enabled then Ubuntu will not be able to gather the drive information it needs to install Ubuntu safely alongside Windows.

If this is the case, you will get a prompt to disable BitLocker in Windows before restarting the Ubuntu installer.

![The BitLocker is enabled page](/images/installer/bitlocker-is-enabled.png) 

Disabling Windows BitLocker is not required when fully erasing Windows or when there is a separate, unencrypted drive available for Ubuntu. For more information, see the final section at the end of this tutorial.


## Create your login details

On this screen, you will be prompted to enter your name and the name of your computer as it will appear on the network. Finally, you will create a username and a strong password.

You can choose to log in automatically or require a password. If you are using your device while traveling, it’s recommended to keep {guilabel}`Require my password to log in` enabled.

![Screenshot from 2024-04-12 14-53-04|800x496](upload://gLbGlF0fzRrkzaqbgX7txM8wE31.jpeg)


## Choose your Location

Select your location and timezone from the map screen and click {guilabel}`Continue`. This information will be detected automatically if you are connected to the internet.

![Screenshot from 2024-04-12 14-53-11|800x496](upload://jMs9EYQ2tw9Wr9nFPqTI0nBLZte.jpeg)


## Ready to install

Clicking {guilabel}`Next` will take you to a summary of your installation configuration to give you a chance to confirm your setup before clicking {guilabel}`Install`.

![Screenshot from 2024-04-12 14-53-16|800x496](upload://gKJgczRhsaiSpA2fRzxdDgwYuxb.jpeg)

:::{note}
If you had chosen to import an autoinstall configuration at the start of the installation process you would be taken immediately to this screen to confirm that your configuration has been installed correctly.
:::

Once you proceed, Ubuntu will begin the installation process.

## Complete the installation

Sit back and enjoy the slideshow as Ubuntu installs in the background.

![Screenshot from 2024-04-12 14-53-23|800x496](upload://8BTthc9wh60tXLijM0FpreZzTFf.jpeg)

Alternatively you can see a detailed output of the installation process by clicking the icon in the bottom right corner of the window.

Once the installation has completed, you will be prompted to restart your machine.

Click {guilabel}`Restart Now`.

![Screenshot from 2024-04-12 14-59-20|800x496](upload://2cbsw060EZSPvcie1XMSGcY6SHZ.jpeg)

When you restart, you will be prompted to remove your USB flash drive from the device. Once you’ve done this, press {guilabel}`Enter`.

![Screenshot from 2024-04-12 15-01-13|800x450](upload://7dEpfpMgKf8fQ6CS2zS8qq7wGtm.png)

Enter your encryption password if you created one.

![Screenshot from 2024-04-12 15-01-26|800x450](upload://mU2tU4SPbwHQEqokqOkEiJS1pZZ.png)

This is then followed by the login screen, where you can enter your username and password.


![Screenshot from 2024-04-12 15-01-53|800x450](upload://sUz5Tq77qNcGpJ0PzYUzrbeV8HR.png)


And that’s it. Welcome to your new Ubuntu Desktop!

![Screenshot from 2024-04-12 15-05-18|800x410](upload://zBNTISkQTOXPIl8JDF7LSVw854D.jpeg)


The welcome widget will help you with some additional setup options:

* Attaching an [Ubuntu Pro](https://ubuntu.com/pro) free personal or paid subscription to apply additional security patches to your device.

    This option is only available when using a long term support (LTS) version of Ubuntu.

* Opting into sending device information to Canonical to help improve Ubuntu.

    By default, Canonical doesn’t collect device information.

* Downloading additional apps from App Center.

![Screenshot from 2024-04-12 15-03-03|800x450](upload://zJvISzS5XwtGG6vJj7dGEJuwvbN.jpeg)



## Don’t forget to update

It’s always good practice to ensure your system is up to date, especially after a fresh install.

The easiest way to do this is via the **Software Updater** app. Search for Software Updater via the app menu (the icon with 9 squares in the bottom corner of your window) and it will check for updates and apply them.

![|624x200](https://assets.ubuntu.com/v1/90b51fc1-software-updater.png)

You can also update Ubuntu using the terminal.

Press {kbd}`Ctrl+Alt+T` to bring up a Terminal window (or click the terminal icon in the sidebar).

Type in:

```bash
sudo apt update
```

You will be prompted to enter your login password.

This will check for updates and tell you if there are any that need applying. To apply any updates, type:

```bash
sudo apt upgrade
```

Type **Y**, then press {kbd}`Enter` to confirm to finish the update process.

## You’ve installed Ubuntu

We hope you enjoy your new desktop.

Check out our picks for [Top 10 apps for a fresh Linux install in 2021](https://ubuntu.com/blog/top-10-apps-for-a-fresh-linux-install-in-2021).

If you have any issues, please contact us via the [Ubuntu Discourse](https://discourse.ubuntu.com/), or visit [Ask Ubuntu](https://askubuntu.com/).

You can also read the latest news about Ubuntu Desktop on the [Ubuntu Blog](https://ubuntu.com/blog/desktop).

As a next step, why not try:

* [Installing Ubuntu Desktop on a Raspberry Pi 4](https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview)

* [Using VirtualBox to try out different Ubuntu flavours](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview)

For users who need to run both Ubuntu and Windows, you can also install Ubuntu via Windows Subsystem for Linux (WSL):

* [Install Ubuntu on Windows Subsystem for Linux (WSL)](https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-11-with-gui-support#1-overview)

To help us improve our tutorials, please let us know how you got on!

Survey:

<!--
This was a poll in the original tutorial.

#### I found this tutorial helpful

[poll name="helpful"]

* Yes

* No

[/poll]

#### I found Ubuntu easy to install

[poll name="difficulty"]

* Very Easy

* Easy

* Neutral

* Difficult

* Very Difficult

[/poll]
-->

## (Additional) Installing Ubuntu alongside Windows with BitLocker

During the installation type step, you may find that you are unable to proceed with the installation without first deactivating Windows Bitlocker.

![image|690x490](upload://f1i0zJXdSGidjJzzsCJ0o3f13kN.png) 

[BitLocker Drive Encryption](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview) is a data protection feature that integrates with the Windows operating system. When activated, it will encrypt the contents of the hard drives in Windows, making the data inaccessible without the correct decryption key. It is designed to minimize the risk of data theft or exposure from lost or stolen computers.

When a user starts their computer and properly authenticates with the correct credentials, BitLocker will decrypt the data and allow seamless usage of the hard drive and the data it contains. Without the correct credentials, the encrypted hard drive data will look like random noise.

### BitLocker & Ubuntu installation

If you plan to install Ubuntu side by side with Windows, you need to take into consideration the operational setup on your computer.

* If you are not using BitLocker, Ubuntu will be able to see the correct hard drive structure, including any partitions and data stored on it. This allows the guided wizard to correctly map the data, and safely make adjustments to accommodate the additional installation of Ubuntu alongside Windows.

* If you are using BitLocker, the hard drive contents will not be accessible, and they will appear as random noise. This means that the Ubuntu installer cannot correctly map data, and the additional installation cannot be safely performed without data loss. Additionally, some manufacturers ship systems with BitLocker enabled but the hard drive contents not yet encrypted. In this case, the Ubuntu installer will also not be able to correctly map data.

What you can do:

* Cancel the installation of Ubuntu and continue using Windows only.

* Decide that the data stored in Windows is not important, and that you are willing to overwrite the data contents. The Ubuntu installer can then erase the entire contents of the hard drive and create its own structure (partitions and data). This is a destructive operation, with no option to recover any Windows data.

* Decide to turn BitLocker off. This will turn off the encryption feature, and the hard drive and its data will be visible and accessible from the Ubuntu installer, allowing it to correctly and safely set up a side-by-side configuration. For systems with BitLocker enabled but not yet encrypted you will need to first turn BitLocker on and then turn it off.

:::{note}
Not all versions of Windows will allow you to re-enable BitLocker after disabling it. If you wish to re-encrypt your Windows partition after installing Ubuntu alongside it, please check that your version of Windows supports this.
:::

### Turn BitLocker off

If you decide to proceed with the third option, you will need to do the following:

1. Back up your data: any encryption procedure, hard drive structure change or installation of new operating systems on a hard drive that already contains data can potentially lead to a data loss. You need to make sure your personal data is safe. Even simply copying the important files to an external drive can minimize the risk of data loss.

2. Quit the Ubuntu installer and reboot the computer into Windows.

3. In Windows, open {menuselection}`Settings --> type Manage BitLocker` in the search box.

    Alternatively, open {menuselection}`Control Panel --> System and Security --> BitLocker Drive Encryption`.

    ![bitlocker-turn-off](upload://kEP4hn6LET2cuCmPMd1QdQ0UPZp)

    Windows will now inform you that it is going to decrypt the data.

    ![bitlocker-decryption-warning|440x205](upload://4NAnBO1Y3wRfZEGlPo6WxRAEfdC)

    This process can take a little bit of time:

    ![bitlocker-decrypting|442x266](upload://54E0znCrp7Qx4MlmiXGzIqIvnFS)

    ![bitlocker-decryption-complete|442x214](upload://g3JuPjDE5VVVeN2kUFpvJml3QcW)

4. Once the decryption is complete, reboot the computer.

5. Log into Windows, to make sure everything works correctly, and that all your data is intact.

6. Reboot your computer again, and launch the Ubuntu installer. At this point, you will be able to proceed with the hard disk configuration step.

