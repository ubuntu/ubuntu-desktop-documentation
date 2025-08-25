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

