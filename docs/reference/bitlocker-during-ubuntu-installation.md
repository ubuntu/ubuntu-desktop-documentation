---
relatedlinks: "[BitLocker &#32; overview &#32; by &#32; Microsoft](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/)"
---

(bitlocker-during-ubuntu-installation)=
# BitLocker during Ubuntu installation

During the installation type step, the Ubuntu installer might inform you that you can't proceed without first deactivating Windows BitLocker.

![The BitLocker is enabled page](/images/installer/bitlocker-is-enabled.png) 


## BitLocker

BitLocker Drive Encryption is a data protection feature that integrates with the Windows operating system. When activated, it will encrypt the contents of the hard drives in Windows, making the data inaccessible without the correct decryption key. It is designed to minimize the risk of data theft or exposure from lost or stolen computers.

When a user starts their computer and properly authenticates with the correct credentials, BitLocker decrypts the data and allows seamless usage of the hard drive and the data that it contains. Without the correct credentials, the encrypted hard drive data looks like random noise.

## BitLocker and Ubuntu installation

If you plan to install Ubuntu side by side with Windows, you need to take into consideration the operational setup on your computer.

* If you are not using BitLocker, Ubuntu can see the correct hard drive structure, including any partitions and data stored on it. The guided installer can correctly map the data and safely install Ubuntu alongside Windows.

* If you are using BitLocker, the hard drive content isn't accessible, and it appears as random noise. The Ubuntu installer can't correctly map data, and can't install alongside Windows without data loss.

    Additionally, some manufacturers ship systems with BitLocker enabled but the hard drive content not yet encrypted. In this case, the Ubuntu installer also can't correctly map data.

## What you can do

* Cancel the installation of Ubuntu and continue using Windows only.

* Decide that the data stored in Windows is not important, and that you are willing to overwrite the data contents.

    The Ubuntu installer can then erase the entire contents of the hard drive and create its own structure (partitions and data).

    This is a destructive operation, with no option to recover any Windows data.

* Decide to turn BitLocker off.

    This will turn off the encryption feature. The hard drive and its data will be visible and accessible from the Ubuntu installer, allowing it to safely set up a side-by-side configuration.

    For details, see {ref}`turn-off-bitlocker-in-windows`.

    :::{warning}
    Certain versions of Windows will no longer allow you to re-enable BitLocker after disabling it.

    If you wish to re-encrypt your Windows partition after installing Ubuntu alongside it, check that your version of Windows supports this.
    :::

