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


## Will Ubuntu work on my computer?

While Ubuntu works on a wide range of devices, it is recommended that you use a device listed on the [Ubuntu certified hardware](https://ubuntu.com/certified?q=&category=Laptop&category=Desktop&limit=20) page. These devices have been tested and confirmed to work well with Ubuntu.


## Back up your data

If you are installing Ubuntu on a PC or laptop that you have used previously, back up your data prior to installation.


## Download an Ubuntu image

Get the Ubuntu image from the [Download Ubuntu Desktop](https://ubuntu.com/download/desktop) page. Save it to a memorable location on your PC. This tutorial uses the latest Ubuntu 24.04 LTS release.

If you are installing an older version of Ubuntu, such as Ubuntu 22.04 LTS, the visual presentation of the installer will be different, but the overall flow should remain similar.

![The Download Ubuntu Desktop page](/images/download-an-ubuntu-image.png)
 

## Create a bootable USB stick

Write your downloaded ISO to a USB stick to create the installation media. This is not the same as copying the ISO and requires some special software.

This tutorial uses [balenaEtcher](https://etcher.balena.io/) because it runs on Linux, Windows and macOS.

1. Choose the version of balenaEtcher that corresponds to your current operating system.

    Download and install the tool.

    ![The Download Etcher page](/images/download-etcher.png)

1. Insert your USB flash drive.

1. Open balenaEtcher.

1. Select your downloaded ISO and your USB flash drive.

    ![The Select target step in Etcher](/images/select-iso.png)

1. Click {guilabel}`Flash!` to write your image.


## Boot from the USB flash drive

1. Insert the USB flash drive into the laptop or PC that you want to use to install Ubuntu.

1. Start or restart the device.

1. Your device should recognize the installation media and launch the Ubuntu installer.

    If not, try holding {kbd}`F12` during startup and selecting the USB device from the system-specific boot menu.

    {kbd}`F12` is the most common key for bringing up the system boot menu but {kbd}`Escape`, {kbd}`F2` and {kbd}`F10` are common alternatives. If unsure, look for a brief message when your system starts: this often informs you which key to press to access the boot menu.

1. Once the installer has initialized, choose your language.

    ![The Choose your language page](/images/installer/choose-your-language.jpeg)

1. Select any accessibility settings that your require.

    ![The Accessibility page](/images/installer/accessibility.jpeg)

1. Select your keyboard layout.

    ![The Keyboard layout page](/images/installer/keyboard-layout.jpeg)

1. Connect to your network.

    This allows Ubuntu to download updates and third party drivers, such as NVIDIA graphics drivers, during installation.

    ![The Internet connection page](/images/installer/internet-connection.jpeg)

1. You are then offered the choice to try or install Ubuntu.

    If you click {guilabel}`Try Ubuntu`, you can preview Ubuntu without making any changes to your PC. You can use the preview to tst if your hardware works correctly with Ubuntu. You can then return to the installer menu at any time by clicking the {guilabel}`Install Ubuntu` shortcut on the desktop.

    ![The Try or install Ubuntu page](/images/installer/try-or-install-ubuntu.jpeg)

    To proceed, click {guilabel}`Install Ubuntu`.

    :::{warning}
    Some PCs use Intel RST (Rapid Storage Technology), which is not supported by Ubuntu. If this is the case, you will not be able to proceed beyond this point without disabling RST in the BIOS menu of your machine.

    If you encounter this alert, see {ref}`reconfigure-windows-to-use-ahci` to resolve the issue. To learn more, see {ref}`intel-rst-during-ubuntu-installation`.
    :::

## Installation setup

1. Choose between {guilabel}`Interactive installation` and {guilabel}`Automated Installation`.

    The interactive option is the standard route for most users.

    More advanced users can use the automated installation option to import a configuration file from a web server to standardize multiple installs and add further customization. An example tutorial for Automated installation is available at [Getting started with Autoinstall on Ubuntu Desktop 24.04 LTS](https://blog.local-optimum.net/getting-started-with-autoinstall-on-ubuntu-desktop-24-04-lts-147a1defb2de).

    ![The Type of installation page](/images/installer/type-of-installation.jpeg)

    In this tutorial, we'll follow the interactive installation.

1. Choose between the {guilabel}`Default selection` and {guilabel}`Extended selection` options.

    The default installation comes with the basic essentials to get started, which you can then expand on after install using the App Center. The extended selection contains additional office tools and utilities, useful for offline situations.

    ![The Applications page](/images/installer/applications.jpeg)

1. The next screen offers to install third-party software that can improve device support and performance (for example, Nvidia graphics drivers) and support for additional media formats.

    It is recommended to check both of these boxes.

    ![The Optimise your computer page](/images/installer/optimise-your-computer.jpeg)


## Type of installation

Configure your installation:

* If you would like Ubuntu to be the only operating system on your hard drive, select {guilabel}`Erase disk and install Ubuntu`.

* If your device currently has another operating system installed, you will receive additional options to install Ubuntu alongside that OS rather than replacing it.

![The Disk setup page](/images/installer/disk-setup.jpeg)

Let’s take a moment to review all of the above options in detail.

### Installing Ubuntu alongside another operating system

If you select this option, you'll be able to select the drive where you want to install Ubuntu and the amount of disk space that you would like Ubuntu to use. The available space is limited by the existing content of the disk. Ubuntu will preserve all existing files.

This view automatically selects the largest partition on the drive. For more fine-grained control, you can switch to the {guilabel}`Manual partitioning` option that is detailed later.

![The Install Ubuntu alongside other partitions page](/images/installer/install-ubuntu-alongside-other-partitions.png) 

### Erase disk and install Ubuntu

If you select this option, Ubuntu will take up the entire disk space on the selected drive.

![The Erase disk and install Ubuntu page](/images/installer/erase-disk-and-install-ubuntu.png) 

If your PC has multiple hard drives then this option allows you to install Ubuntu alongside an existing OS as long as they each have their own drive.

:::{warning}
Ensure that you are selecting the right drive in this instance.
:::

This option also allows you to encrypt your entire drive using LVM, ZFS or using the Trusted Platform Module (TPM) on the device. To do this:

1. Open the {guilabel}`Advanced features` option.
1. Proceed to the {guilabel}`Disk setup` screen.
1. Select {guilabel}`Encrypt the new Ubuntu installation for security`.

    ![The Advanced features dialog](/images/installer/advanced-features.jpeg)

The following encryption options are available here:

LVM
: LVM stands for Logical Volume Management. By using LVM during the setup, it makes it easier to create and manage partitions post installation.

ZFS
: This advanced file system allows you to create pooled storage volumes that span multiple drives. It supports snapshots and data repair features. It is a powerful option for advanced users.

Hardware-backed full disk encryption
: TPM-backed full disk encryption is a new, highly experimental feature of Ubuntu Desktop that currently supports only the generic kernel. This means that machines that require additional drivers to support webcams or NVIDIA graphics cards will not support this setup until additional features land after release. In addition, certain hardware vendors may have BIOS options enabled that alter the chain of trust.

    :::{warning}
    Please do not select TPM unless you are comfortable debugging or re-installing in the event of an issue.
    :::

If you select either LVM or ZFS encryption, the installer asks you to create a password that you will need to enter on boot before logging in with your user credentials.

![The Disk passphrase page](/images/installer/disk-passphrase.jpeg)

If you are using TPM-based Full Disk Encryption, you will be prompted to run the following command after installing to generate a recovery key:

```bash
snap recovery --show-keys
```

:::{warning}
If you enable encryption, it is important that you do not lose your security key. Write it down and store it in a safe place outside of your local system. **You will not be able to recover your data without it.**
:::

### Manual partitioning

Manual partitioning is designed for advanced users who want to create specific configurations for their use-cases. As such, we assume that these users will be comfortable with this interface and will not go into detail during this tutorial on specific setups.

Here, users can see all existing drives and partitions and create and manage new partition tables and configurations.

![The Manual partitioning page](/images/installer/manual-partitioning.png) 

### (Alert) Windows BitLocker is enabled

If your device has Windows BitLocker Drive Encryption enabled, the installer can't access the encrypted Windows installation. Because of that, it can't install Ubuntu safely alongside Windows.

<!--
If the installer detects BitLocker, it points you to the help.ubuntu.com/bitlocker URL.

This is a redirect to the last page of the installation tutorial, which explains BitLocker.

The redirect is configured in the .htaccess file in the Help repository:
https://code.launchpad.net/~ubuntu-core-doc/help.ubuntu.com/help.ubuntu.com
-->

![The BitLocker is enabled page](/images/installer/bitlocker-is-enabled.png) 

You can either erase Windows and replace it with Ubuntu, or you can disable BitLocker and install Ubuntu alongside Windows. To disable BitLocker, see {ref}`turn-off-bitlocker-in-windows`. To learn more, see {ref}`bitlocker-during-ubuntu-installation`.

Alternatively, you can install Ubuntu to a separate, unencrypted disk if it's available on the system.


## Create your login details

On this screen, you will be prompted to enter your name and the name of your computer as it will appear on the network. Finally, you will create a username and a strong password.

You can choose to log in automatically or require a password. If you are using your device while traveling, it’s recommended to keep {guilabel}`Require my password to log in` enabled.

![The Create your account page](/images/installer/create-your-account.jpeg)


## Choose your Location

Select your location and timezone from the map screen and click {guilabel}`Continue`. This information will be detected automatically if you are connected to the internet.

![The Select your timezone page](/images/installer/select-your-timezone.jpeg)


## Ready to install

Clicking {guilabel}`Next` will take you to a summary of your installation configuration to give you a chance to confirm your setup before clicking {guilabel}`Install`.

![The Ready to install page](/images/installer/ready-to-install.jpeg)

:::{note}
If you had chosen to import an autoinstall configuration at the start of the installation process you would be taken immediately to this screen to confirm that your configuration has been installed correctly.
:::

Once you proceed, Ubuntu will begin the installation process.

## Complete the installation

Sit back and enjoy the slideshow as Ubuntu installs in the background.

![The installation slideshow](/images/installer/slideshow.jpeg)

Alternatively you can see a detailed output of the installation process by clicking the icon in the bottom right corner of the window.

Once the installation has completed, you will be prompted to restart your machine.

Click {guilabel}`Restart Now`.

![The Installation complete page](/images/installer/installation-complete.jpeg)

When you restart, you will be prompted to remove your USB flash drive from the device. Once you’ve done this, press {guilabel}`Enter`.

![The Remove the installation medium prompt](/images/installer/remove-the-installation-medium.png)


## Your new system is starting

Enter your encryption password if you created one.

![The disk passphrase prompt](/images/unlock-disk.png)

This is then followed by the login screen, where you can enter your username and password.


![The Ubuntu login screen](/images/login-screen.png)


And that’s it. Welcome to your new Ubuntu Desktop!

![The Ubuntu 24.04 desktop](/images/ubuntu-24-04-desktop.jpeg)


The welcome widget will help you with some additional setup options:

* Attaching an [Ubuntu Pro](https://ubuntu.com/pro) free personal or paid subscription to apply additional security patches to your device.

    This option is only available when using a long term support (LTS) version of Ubuntu.

* Opting into sending device information to Canonical to help improve Ubuntu.

    By default, Canonical doesn’t collect device information.

* Downloading additional apps from App Center.

![The Ubuntu welcome widget](/images/welcome-widget.jpeg)



## Don’t forget to update

It’s always good practice to ensure your system is up to date, especially after a fresh install.

The easiest way to do this is via the **Software Updater** app. Search for Software Updater via the app menu (the icon with 9 squares in the bottom corner of your window) and it will check for updates and apply them.

![The Ubuntu Software Updater](/images/software-updater.png)

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

