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

### Using KDE ISO Image Writer

KDE ISO Image Writer is part of the KDE Plasma desktop environment. You can use it on distributions like Kubuntu. It's available for Ubuntu and Kubuntu 25.04, 25.10, 26.04 LTS and later.

1. Go to the [releases.ubuntu.com](https://releases.ubuntu.com/) website and find the Ubuntu release that you're writing on your USB stick, such as [Ubuntu 24.04 (Noble Numbat)](https://releases.ubuntu.com/noble/).

1. Download the `SHA256SUMS` and `SHA256SUMS.gpg` checksum files. In the file selector, make sure not to attach the `.txt` suffix to the `SHA256SUMS` file. Place the files in the same directory as the Ubuntu image.

    KDE ISO Image Writer uses these files to verify the Ubuntu image.

1. Install KDE ISO Image Writer in the Discover app store or on the command line:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo apt install isoimagewriter
    ```

1. Open KDE ISO Image Writer.

1. In the {guilabel}`ISO image` field, select the downloaded Ubuntu image. KDE ISO Image Writer starts verifying the image according to the checksum files.

1. In the {guilabel}`USB drive` field, make sure that the correct USB stick is selected.

    ![KDE ISO Image Writer with a selected USB drive and a verified ISO image. It says "The ISO image is valid"](/images/kde-iso-image-writer.png)

1. Click {guilabel}`Create` to start writing the Ubuntu image to USB. Confirm with your password.

1. When KDE ISO Image Writer finishes writing, click {guilabel}`Close`.

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

You can create a bootable USB stick using [Rufus](https://rufus.ie/), a free and open source USB stick writing tool.

<!--
The docs/reuse/usb-using-rufus.txt file is reused between the live system tutorial, the installation tutorial and the bootable USB how-to guide.
-->
```{include} ../reuse/usb-using-rufus.txt
```


## On macOS

On macOS, you have to install a third-party application for writing images to USB sticks. Alternatively, you can use the built-in `dd` tool on the command line.

The USB stick will work on **PC (Windows) hardware** and older Apple hardware based on **Intel CPUs**.

```{include} ../reuse/apple-silicon-disclaimer.txt
```

<!--
Unfortunately, Disk Utility doesn't seem to be able to write arbitrary images, only macOS disk images. Saving for future reference and reevaluation.

### Using the Disk Utility

The Disk Utility is preinstalled on macOS and you can use it to write any image to your USB stick.

1. Launch the *Disk Utility* app from {menuselection}`Applications -> Utilities` or from the Spotlight search.

1. Insert your USB stick. It appears in the sidebar. Select it there.

    You might need to enable the {menuselection}`View -> Show All Devices` option.

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
-->

### Using balenaEtcher

You can create a bootable USB stick using [balenaEtcher](https://etcher.balena.io/), a free and open source USB stick writing tool.

<!--
The docs/reuse/usb-using-balena-etcher-on-macos.txt file is reused between the live system tutorial, the installation tutorial and the bootable USB how-to guide.
-->
```{include} ../reuse/usb-using-balena-etcher-on-macos.txt
```

### Using the macOS command line

If you feel confident using the macOS command line, you can follow a more manual approach.

<!--
Migrated from a page in the Community Help Wiki:
https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick
-->

1. Open the Terminal app.

<!--
This is no longer necessary, and in fact it produces an unusable image:

1. Convert the downloaded ISO image file to the UDRW format:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: hdiutil convert Downloads/ubuntu-24.04.3-desktop-amd64.iso -format UDRW -o ubuntu.dmg
    ```
-->

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

      /dev/disk0 (internal, physical):
       […]
      /dev/disk2
       #: TYPE NAME SIZE IDENTIFY
       0: FDisk_partition_scheme *4.0 GB disk2
       1: DOS_FAT_32 USB CLE 4.0 GB disk2s1
    ```

1. Make sure that the USB stick is large enough for the Ubuntu image. If it's too small, the image writer might silently fail.

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
    :input: sudo dd if=Downloads/ubuntu-24.04.3-desktop-amd64.iso of=/dev/rdisk<N> bs=4m
    ```

    :::{tip}
    Drag and drop the image file from Finder to Terminal to paste the full path. This way, you prevent potential errors when typing the path.
    :::

    Double-check the file paths in this command:

    * The `if` argument specifies the "input file", or the path to the **Ubuntu image**.

    * The `of` argument specifies the "output file", or the path to the **USB device**. Make sure that this is the correct device.

        We're using the `/dev/rdisk<N>` device here rather than `/dev/disk<N>`. This refers to a "raw device" interface to the same disk, which is faster.

    The `bs=4m` option increases the write performance and it's optional.

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


## On multiple platforms

If the previous applications didn't work or you have a special use case, we also suggest the following multi-platform image writers.

### Ventoy

[Ventoy](https://www.ventoy.net/) is an open-source tool that you install on your USB. You can then copy image files to the USB storage using your normal file browser. When you boot the system with the USB stick inserted, Ventoy lets you choose among all the image files stored on the USB.

For instructions, see the Ventoy documentation: [Start to use Ventoy](https://www.ventoy.net/en/doc_start.html).

Ventoy is available for Linux and Microsoft Windows.

### balenaEtcher

[balenaEtcher](https://etcher.balena.io/) is a simple open-source USB stick writing tool. It's available for Windows, macOS and Linux.

See the documentation at [etcher-docs.balena.io](https://etcher-docs.balena.io/).

### WonderISO

[WonderISO](https://www.sysgeeker.com/iso-burner.html) is a versatile and easy-to-use tool that can write images to USB. WonderISO is available for Microsoft Windows and macOS as a proprietary (closed-source) application.

For instructions, see the [WonderISO product manual](https://www.sysgeeker.com/online-help/wonderiso.html).


## Next steps

Congratulations! You now have Ubuntu on a USB stick, bootable and ready to go.

To use it you need to insert the stick into your target PC or laptop and reboot the device. It should recognize the installation media automatically during startup but you may need to hold down a specific key (usually {kbd}`F12`) to bring up the boot menu and choose to boot from USB.

For a full walkthrough of installing Ubuntu, take a look at our {ref}`install-ubuntu-desktop` tutorial.


## Finding help

If you get stuck, help is always at hand:

* [Get support](https://ubuntu.com/support/community-support)
* [Join our Discourse forum](https://discourse.ubuntu.com/c/project/desktop/)
* [Join our online chat on Matrix](https://matrix.to/#/#desktop-dev:ubuntu.com)
