---
sequential_nav: both
---

(install-ubuntu-desktop)=
# Install Ubuntu Desktop

<!--
Original source: <https://discourse.ubuntu.com/t/install-ubuntu-desktop/25312/>
Original author: Oliver Smith <oliversmith@canonical.com>
-->

In this tutorial, we'll download and install Ubuntu Desktop 24.04 LTS on your laptop or PC.

If you've never installed an operating system, don't worry: Ubuntu makes the process very easy. You'll encounter a guided installer that will ask you a couple of questions. Whenever you're not sure what to pick, you can just select the default option, which ensures that you end up with a fully usable Ubuntu installation. No deep technical knowledge is required.

What you'll need:

* A laptop or PC with at least 25GB of storage space.

* A flash drive, 8GB or above recommended.


## Will Ubuntu work on my computer?

While Ubuntu works on a wide range of devices, it's best to use a device listed on the [Ubuntu certified hardware](https://ubuntu.com/certified?q=&category=Laptop&category=Desktop&limit=20) page. These devices have been tested and confirmed to work well with Ubuntu.

If you can't see your device there, you can always just {ref}`try-ubuntu-desktop` and check if everything works as expected.

```{include} ../reuse/apple-silicon-disclaimer.txt
```


(installation-back-up-your-data)=
## Back up your data

If you're installing Ubuntu on a PC or laptop that you've used previously, back up your data before you start the installation:

* Move any **files** that you want to keep to another storage device, such as an external disk or a USB drive.

* To back up your **web browser**, connect your browser to an online account, such as a Firefox account or a Google account. After the Ubuntu installation, your browser synchronizes your data when you log into your account. Note that the Safari browser doesn't work on Ubuntu.

Back up your files from the **USB flash drive**. The drive will be erased.


<!--
The docs/reuse/boot-ubuntu-from-usb.txt file is reused between the live system tutorial and the installation tutorial.
-->
:::{include} ../reuse/boot-ubuntu-from-usb.txt
:::


## Follow the installer

The Ubuntu Desktop installer opens.

1. Choose your language.

    ![The Choose your language page](/images/installer/choose-your-language.jpeg)

1. Select any accessibility settings that your require.

    ![The Accessibility page](/images/installer/accessibility.jpeg)

1. Select your keyboard layout.

    ![The Keyboard layout page](/images/installer/keyboard-layout.jpeg)

1. Connect to your network.

    This allows Ubuntu to download updates and third party drivers, such as NVIDIA graphics drivers, during installation.

    ![The Internet connection page](/images/installer/internet-connection.jpeg)

    The network connection is optional. If you can't connect, the Ubuntu installation will still work.

1. The installer gives you the choice to try or install Ubuntu.

    If you click {guilabel}`Try Ubuntu`, you can preview Ubuntu without making any changes to your PC. You can use the preview to test if your hardware works correctly with Ubuntu. You can then return to the installer menu at any time by clicking the {guilabel}`Install Ubuntu` shortcut on the desktop.

    ![The Try or install Ubuntu page](/images/installer/try-or-install-ubuntu.jpeg)

    To proceed, click {guilabel}`Install Ubuntu`.

:::{warning}
Some PCs use Intel RST (Rapid Storage Technology), which is not supported by Ubuntu. If this is the case, you won't be able to proceed with the installation unless you disable RST on your machine.

If you encounter this alert, see {ref}`reconfigure-windows-to-use-ahci` to resolve the issue. To learn more, see {ref}`intel-rst-during-ubuntu-installation`.
:::


## Type of installation

Here, you can select how you want to be guided through the installation and what software you want to install.

1. Choose between {guilabel}`Interactive installation` and {guilabel}`Automated Installation`.

    The interactive option is the standard route for most users.

    More advanced users can use the automated installation option to import a configuration file from a web server to standardize multiple installs and add further customization. An example tutorial for Automated installation is available at [Getting started with Autoinstall on Ubuntu Desktop 24.04 LTS](https://blog.local-optimum.net/getting-started-with-autoinstall-on-ubuntu-desktop-24-04-lts-147a1defb2de).

    ![The Type of installation page](/images/installer/type-of-installation.jpeg)

    In this tutorial, we'll follow the interactive installation.

1. Choose between the {guilabel}`Default selection` and {guilabel}`Extended selection` options.

    The default installation comes with the basic essentials to get started, which you can then expand on after install using the App Center. The extended selection contains additional office tools and utilities.

    You can always install all these applications later if you have an internet connection.

    ![The Applications page](/images/installer/applications.jpeg)

1. Here, you can install third-party software. It can improve device support and performance (for example, NVIDIA graphics drivers) and adds support for additional media formats.

    We recommend that you enable both options.

    ![The Optimise your computer page](/images/installer/optimise-your-computer.jpeg)


## Disk setup

Select how Ubuntu should be installed on the disk:

* If you'd like Ubuntu to be the only operating system on your hard drive, select {guilabel}`Erase disk and install Ubuntu`. This is the easiest option.

* {guilabel}`Manual installation` is intended for expert users.

* If your device currently has another operating system installed, you also have the options to install Ubuntu alongside that system.

![The Disk setup page](/images/installer/disk-setup.jpeg)

Let’s take a moment to review all of the above options in detail.

### Erase disk and install Ubuntu

If you select this option, Ubuntu takes up the entire disk space on the selected drive.

![The Erase disk and install Ubuntu page](/images/installer/erase-disk-and-install-ubuntu.png)

If your PC has multiple hard drives, you can select where Ubuntu is installed. This option allows you to install Ubuntu alongside an existing OS as long as they each have their own drive.

:::{warning}
Ensure that you're selecting the right drive in this case.
:::

### Encrypt your data

If you want to encrypt your data, you can enable disk encryption with the {guilabel}`Erase disk and install Ubuntu` option:

<!-- Not sure where this came from in the original tutorial:
1. Select {guilabel}`Encrypt the new Ubuntu installation for security`.
-->

1. On the {guilabel}`Disk setup` screen, select {guilabel}`Erase disk and install Ubuntu`.

1. Open {guilabel}`Advanced features`.

    ![The Advanced features dialog](/images/installer/advanced-features.jpeg)

1. Select a disk encryption method. {guilabel}`Use LVM and encryption` is the recommended encryption option.

For a description of the advanced features, see {ref}`advanced-disk-setup-features`.

If you select either LVM or ZFS encryption, the installer asks you to create a passphrase that you'll need to enter during every system startup to unlock the disk.

![The Disk passphrase page](/images/installer/disk-passphrase.jpeg)

:::{warning}
Keep your passphrase safe and don't lose it. Write it down and store it in a safe place outside of your local system. **You won't be able to recover your data without the password.**
:::

### Manual partitioning

Manual partitioning is designed for **advanced users** who want to create a specific configuration for their use case. If that's you, we assume that you know what you're doing and that you're comfortable with the installer interface.

Here, you can see all existing drives and partitions. You can create and manage new partition tables and configurations.

![The Manual partitioning page](/images/installer/manual-partitioning.png)

If the interface doesn't make sense, we recommend that you pick one of the automated disk setup options instead.

### Installing Ubuntu alongside another operating system

If you select this option, you'll be able to select the drive where you want to install Ubuntu and the amount of disk space that you'd like Ubuntu to use. The available space is limited by the size that the files on the disk occupy. Ubuntu will preserve all existing files.

This view automatically selects the largest partition on the drive. For more control, you can switch to the {guilabel}`Manual partitioning` option.

![The Install Ubuntu alongside other partitions page](/images/installer/install-ubuntu-alongside-other-partitions.png)

### Alert: Windows BitLocker is enabled

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


## User and password

On this screen, enter your name and pick a name for your computer as it will appear on the network. Enter your user name and a strong password.

You can choose to log in automatically or require a password. If you use your device while traveling, it's recommended to keep {guilabel}`Require my password to log in` enabled.

![The Create your account page](/images/installer/create-your-account.jpeg)


## Select your timezone

Select your location and timezone from the map screen. Ubuntu can detect your location automatically if you're connected to the internet.

![The Select your timezone page](/images/installer/select-your-timezone.jpeg)


## Ready to install

Here, you can see a summary of your installation configuration. Review  your setup before clicking {guilabel}`Install`.

![The Ready to install page](/images/installer/ready-to-install.jpeg)

:::{note}
If you choose to import an autoinstall configuration at the start of the installation process, the installer takes you directly to this screen to confirm that your configuration is correct.
:::

Once you proceed, Ubuntu begins the installation process.


## Complete the installation

Sit back and enjoy the slideshow as Ubuntu installs in the background.

![The installation slideshow](/images/installer/slideshow.jpeg)

Alternatively, you can watch a detailed output of the installation process by clicking the icon in the lower right corner of the window.

When the installation has completed, the installer prompts you to restart your machine. Click {guilabel}`Restart Now`.

![The Installation complete page](/images/installer/installation-complete.jpeg)

When you restart, Ubuntu asks you to remove your USB flash drive from the device. Then, press {guilabel}`Enter`.

![The Remove the installation medium prompt](/images/installer/remove-the-installation-medium.png)


## Your new system is starting

Enter your disk encryption passphrase if you created one.

![The disk passphrase prompt](/images/unlock-disk.png)

At the login screen, enter your user name and password.

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



## Don't forget to update

It’s always good practice to ensure your system is up to date, especially after a fresh install.

The easiest way to do this is via the **Software Updater** app. Search for Software Updater via the app menu (the Ubuntu icon in the bottom corner of your screen). It will check for updates and apply them.

![The Ubuntu Software Updater](/images/software-updater.png)

You can also update Ubuntu using the terminal:

1. Press {kbd}`Ctrl+Alt+T` to bring up a Terminal window.

1. Type in:

    ```bash
    sudo apt update
    ```

    You will be prompted to enter your login password.

    This will check for updates and tell you if there are any that need applying.

1. To apply any updates, type:

    ```bash
    sudo apt upgrade
    ```

1. Type **Y**, then press {kbd}`Enter` to confirm to finish the update process.

For details, see [Updating the system with APT](https://documentation.ubuntu.com/server/tutorial/managing-software/#updating-the-system-with-apt) in the Ubuntu Server documentation.

## You've installed Ubuntu

We hope you enjoy your new desktop.

If you backed up your data, you can now move them back into Ubuntu. If you backed up your web browser account, log in to synchronize your data.

Check out our picks for [Top 10 apps for a fresh Linux install in 2021](https://ubuntu.com/blog/top-10-apps-for-a-fresh-linux-install-in-2021).

If you have any issues, please contact us via the [Ubuntu Discourse](https://discourse.ubuntu.com/), or visit [Ask Ubuntu](https://askubuntu.com/).

You can also read the latest news about Ubuntu Desktop on the [Ubuntu Blog](https://ubuntu.com/blog/desktop).

If you need to run both Ubuntu and Windows, you can [install Ubuntu on Windows Subsystem for Linux (WSL)](https://documentation.ubuntu.com/wsl/stable/).
