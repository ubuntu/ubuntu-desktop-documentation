---
relatedlinks: "[Intel &#32; RST &#32; documentation](https://www.intel.com/content/dam/support/us/en/documents/chipsets/imsm/sb/irst_user_guide.pdf), [Support &#32; for &#32; Intel® &#32; Rapid &#32; Storage &#32; Technology &#32; (Intel® &#32; RST)](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm/)"
---

```{tags} Installation, Windows
```

(intel-rst-during-ubuntu-installation)=
# Intel RST during Ubuntu installation

Intel Rapid Storage Technology (RST) is a solution built into a range of Intel chipsets. On platforms that have RST support built and enabled in the firmware (BIOS or UEFI), RST enables users to group and manage multiple disks as a single volume. This functionality is known as the Redundant Array of Independent Disks (RAID).

RAID offers various advantages over the use of several independent disks. RAID supports multiple configurations (*levels*) which focus on performance and redundancy.


## RST with Ubuntu and Windows

If you want to install Ubuntu on a computer that uses RST, you might have to make adjustments to your setup first.

The Ubuntu installer can detect certain RAID configurations, but it might not be able to access the disks grouped in them.

If the Ubuntu installer can't detect the disks that you need, you must turn off RST in the computer’s firmware before you can install Ubuntu. The terminology and steps to access and manage RST in the firmware depend on the implementation by the platform vendor. For instance, Dell, Lenovo and HP computers all have different settings.

Furthermore, Windows might be already installed on the computer that uses RST. If you disable RST in the firmware or change the RST configuration, Windows might become unable to start because it's no longer able to find the disks.


## Possible installation scenarios

Broadly, you might encounter the following configurations when you try to install Ubuntu on a computer that uses RST:

:::{list-table}
:header-rows: 1

* - RST state
  - Operating system state

* - RST enabled
  - No operating system installed

* - RST used and enabled
  - No operating system installed

* - RST used and enabled
  - Windows installed
:::

Based on the configuration, the following installation scenarios are possible:

### When Ubuntu can access the disks

The Ubuntu installer **correctly detects** the disks and can use them.

In this case, you can proceed with the Ubuntu installation as usual.

If Windows is installed on the system, you need to create a side-by-side configuration for Windows and Ubuntu.

### When Ubuntu can't access the disks

The Ubuntu installer **detects a conflict** with RST and notifies you that manual configuration is required.

You can resolve this problem by either one of the following changes:

* Turn off RST completely in the firmware.

* Change the storage controller protocol from RST to Advanced Host Controller Interface (AHCI).

If Windows is installed, the change will affect the Windows operating system.

To switch the Windows storage controller from RST to AHCI, see {ref}`reconfigure-windows-to-use-ahci`.

:::{caution}
Changes to storage configuration might lead to irrecoverable loss of data:

- If you break a RAID setup, your data might no longer be accessible.

- If you change the controller type from RST to AHCI, Windows might no longer be able to boot.
:::


## AHCI

AHCI is a specification that describes how computer storage is accessed and managed. It supersedes several legacy specifications.

It is designed to use advanced features of disks connected via the Serial ATA (SATA) bus. Typically, these are 2.5" or 3.5" disks, either mechanical hard drives or SSD devices.

The change from RST to AHCI might result in the loss of some of the advanced functionality that the RST module offers: for instance TRIM for SSD.

The terminology and steps to access and manage controller type in the firmware depend on the specific implementation by the platform vendor.
