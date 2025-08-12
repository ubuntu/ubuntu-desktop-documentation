---
relatedlinks: "[Intel &#32; RST &#32; documentation](https://www.intel.com/content/dam/support/us/en/documents/chipsets/imsm/sb/irst_user_guide.pdf)"
---


(intel-rst-during-ubuntu-installation)=
# Intel RST during Ubuntu installation

Intel Rapid Storage Technology (RST) is a solution built into a range of Intel chipsets. On platforms that have RST support built and enabled in the computer’s BIOS, it allows users to group and manage multiple hard disks as single volumes. This functionality is known as the Redundant Array of Independent Disks (RAID).

In some usage scenarios, RAID offers various advantages over the use of several disks independently. RAID offers multiple configurations (*levels*) which focus on performance and redundancy.


## RST & Ubuntu installation

If you intend to install Ubuntu on a computer that supports RST functionality, you may need to make operational adjustments to your setup before you can proceed.

By default, the Ubuntu installer can detect certain RAID configurations, but it may not necessarily be able to access and use the hard disks grouped in them.

If the Ubuntu installer cannot detect the hard disks you need, then before you can install Ubuntu, you will need to turn off RST in the computer’s BIOS. The exact terminology and steps required to access and manage RST in BIOS often depend on the specific implementation by the platform vendor. For instance, Dell computers may have different settings from Lenovo or HP computers.

Furthermore, you may already have Windows installed on the computer that uses RST. If you disable RST in the BIOS or change the RST configuration, Windows may become unbootable, as it may no longer be able to find and use the hard disks.


## Possible installation scenarios

Broadly, there are two main configurations you may encounter when you try to install Ubuntu on a computer that supports and uses RST:

* RST used and enabled, no operating system installed.

* RST used and enabled, Windows installed.

* RST enabled, no operating system installed.

Again, there are two possible scenarios here:

* The Ubuntu installer correctly detects the hard disks and can use them. In this case, you can proceed normally.

* The Ubuntu installer detects a conflict with RST and will notify the user that RST configuration is required.

The latter scenario can be resolved by either one of the two changes:

* Turning RST off completely in BIOS.

* Changing the storage controller protocol from RST to Advanced Host Controller Interface (AHCI).

AHCI is a relatively new specification that describes how computer storage is accessed and managed, and it supersedes several older specifications. It is primarily designed to utilize advanced features of hard drives connected via the Serial ATA (SATA) bus. Typically, these will be 2.5-in and 3.5-in hard disks, including both mechanical and SSD devices. The change from RST to AHCI may result in the loss of some of the advanced functionality that the RST module offers (for instance TRIM for SSD).

The exact terminology and steps required to access and manage controller type in BIOS often depend on the specific implementation by the platform vendor.

### RST enabled, Windows installed

Similarly, there are two possible scenarios available:

* The Ubuntu installer correctly detects the hard disks and can use them. In this case, you can proceed normally. You will need to create a side-by-side configuration for Windows and Ubuntu.

* The Ubuntu installer detects a conflict with RST and will notify the user that RST configuration change is required. In this case, the change will affect the installed Windows operating system.

:::{caution}
Please note that changes to storage configuration can be destructible and lead to irrecoverable loss of data. If you break a RAID setup, your data may no longer be accessible. Likewise, if you change the controller type from RST to AHCI, Windows may no longer be able to boot.
:::

