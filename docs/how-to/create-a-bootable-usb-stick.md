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
Startup Disk Creator is intended for Ubuntu images and images of other distributions based on Ubuntu, such as flavors like Kubuntu or Xubuntu, or derived distributions. It might not work correctly with other Linux distributions and different operating systems.
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

### Using the Linux command line

The `dd` image writer is available on all Linux systems. You can use it even on minimal systems without any graphical environment.

1. Insert your USB stick.

1. Make sure that the USB stick is large enough for the Ubuntu image. If it's too small, the image writer might silently fail.

1. List storage devices on your system:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: lsblk --scsi

    NAME
        HCTL       TYPE VENDOR   MODEL          REV SERIAL               TRAN
    sda 0:0:0:0    disk SanDisk  Ultra USB 3.0 1.00 4C530000010118116183 usb
    ```

    In this example, one USB stick is connected. Note down its device name at the start of the line, such as `sda` here.

1. Unmount all file systems on the USB stick:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo umount /dev/sda*
    ```

    Replace `sda` with the USB device name.

1. Write the Ubuntu image to the USB stick:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo dd if=Downloads/ubuntu-24.04.3-desktop-amd64.iso of=/dev/sda bs=4M conv=fsync status=progress
    ```

    Double-check the file paths in this command:

    * The `if` argument specifies the "input file", or the path to the **Ubuntu image**.

    * The `of` argument specifies the "output file", or the path to the **USB device**. Make sure that this is the correct device.

    The remaining arguments are optional: `bs=4M` increases the write performance, `conv=fsync` ensures that all data is written when the command finishes, and `status=progress` shows progress information.

1. The `dd` tool reports when the writing is finished:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo dd if=Downloads/ubuntu-24.04.3-desktop-amd64.iso of=/dev/sda bs=4M conv=fsync status=progress

    6337593344 bytes (6.3 GB, 5.9 GiB) copied, 143 s, 44.3 MB/s6345887744 bytes (6.3 GB, 5.9 GiB) copied, 143.302 s, 44.3 MB/s

    1512+1 records in
    1512+1 records out
    6345887744 bytes (6.3 GB, 5.9 GiB) copied, 286.923 s, 22.1 MB/s
    ```

1. Inform your running system of the changes on the USB stick if you want to examine the Ubuntu media:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo partprobe /dev/sda
    ```


## On Windows

On Microsoft Windows, you have to install a third-party application for writing images to USB sticks.

<!--
Note: The built-in Disc Image Burner tool can only burn images to optical discs. It can't write to USB sticks.
-->

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

### Using the macOS command line

If you feel confident using the macOS command line, you can follow a more manual approach.

<!--
Migrated from a page in the Community Help Wiki:
https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick
-->

1. Open the Terminal app.

1. Convert the downloaded ISO image file to the UDRW format:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: hdiutil convert Downloads/ubuntu-24.04.3-desktop-amd64.iso -format UDRW -o ubuntu.img
    ```

    :::{tip}
    Drag and drop the image file from Finder to Terminal to paste the full path. This way, you prevent potential errors when typing the path.
    :::

1. List the current devices:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: diskutil list
    ```

1. Insert your USB stick.

1. List the current devices again. Determine the device name assigned to your USB stick, such as `/dev/disk2`:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: diskutil list
    ```

1. Unmount the USB stick:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: diskutil unmountDisk /dev/disk<N>
    ```

    Replace `<N>` with the disk number from the last command, such as `2`.

    You might see this error: "Unmount of disk<N> failed: at least one volume could not be unmounted". Open the Disk Utility and unmount the volume (don't eject).

1. Write the Ubuntu image to the USB stick:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo dd if=ubuntu.img of=/dev/rdisk<N> bs=4m
    ```

    :::{note}
    We're using the `/dev/rdisk<N>` device here rather than `/dev/disk<N>`. This refers to a "raw device" interface to the same disk, which is faster.
    :::

    You might encounter these errors:

    `dd: Invalid number '4m'`
    : You're using GNU `dd`. Use the same command but replace `bs=4m` with `bs=4M`.

    `dd: /dev/disk<N>: Resource busy`
    : Make sure that the disk is not in use. Open the Disk Utility and unmount the volume (don't eject).

1. Unmount the USB stick:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: diskutil eject /dev/disk<N>
    ```

1. Remove the USB stick when the previous command completes.


## Other options

[Ventoy](https://www.ventoy.net/) is an open-source tool that you install on your USB. You can then copy image files to the USB storage using your normal file browser. When you boot the system with the USB stick inserted, Ventoy lets you choose among all the image files stored on the USB.

For instructions, see the Ventoy documentation: [Start to use Ventoy](https://www.ventoy.net/en/doc_start.html).

Ventoy is available for Linux and Microsoft Windows.


## Next steps

Congratulations! You now have Ubuntu on a USB stick, bootable and ready to go.

To use it you need to insert the stick into your target PC or laptop and reboot the device. It should recognize the installation media automatically during startup but you may need to hold down a specific key (usually {kbd}`F12`) to bring up the boot menu and choose to boot from USB.

For a full walkthrough of installing Ubuntu, take a look at our {ref}`install-ubuntu-desktop` tutorial.


## Finding help

If you get stuck, help is always at hand:

-  [Ubuntu Discourse](https://discourse.ubuntu.com/)
-  [Ask Ubuntu](https://askubuntu.com/)
-  [IRC-based support](https://wiki.ubuntu.com/IRC/ChannelList)
