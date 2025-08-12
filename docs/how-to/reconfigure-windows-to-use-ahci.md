(reconfigure-windows-to-use-ahci)=
# Reconfigure Windows to use AHCI

How to safely re-configure Windows to use AHCI

If the Ubuntu installer detects RST, and you have Windows installed on your system, there are several steps you need to do to allow Ubuntu to install side by side with Windows, without any loss of data and functionality.

## Back up your data

Any hard drive structure or configuration change, or installation of new operating systems on a hard drive that already contains data can potentially lead to a data loss. You need to make sure your personal data is safe.

Even simply copying the important files to an external drive can minimize the risk of data loss.

## Change the controller mode

1. Verify which controller mode is in use in Windows. You can do this through the Device Manager.

1. If the controller mode is set to anything other than “Standard SATA AHCI Controller”, then you will need to make a change that allows Windows to boot safely in AHCI mode. This can be done using the Registry Editor.

1. Start Registry Editor, and navigate to:

    ```text
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\iaStorV\
    ```

    ![Regedit](/images/windows-ahci/Regedit.png)

1. In the right column, double-click on the Start key, and change its value to 0.

1. Double-click on the iaStorV entry in the left column to expand it, select the StartOverride entry, and then in the right column, change the value of the key 0 to 0.

    ![Regedit override](/images/windows-ahci/Regedit-override-dword.png)

1. Repeat this set of changes for the following path in the Registry Editor:

    ```text
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\storahci\
    ```

1. Reboot Windows and start your computer’s BIOS.

    Normally, BIOS is accessed by hitting the F2 or Del key during the early boot sequence. In the BIOS menu, change the hard disk controller type to AHCI. The exact terminology and steps required to access and manage controller type in BIOS often depend on the specific implementation by the platform vendor.

1. Exit BIOS, and let the system boot. Windows should load normally, and you can check the controller mode in the Device Manager. It should read: Standard SATA AHCI Controller.

    ![Regedit override](/images/windows-ahci/Regedit-override.png)


## Troubleshooting boot problems

After making the necessary changes to allow Ubuntu to install side by side with Windows, you may encounter a situation where Windows no longer boots. For instance, this could happen if you made the BIOS change without making the registry changes in Windows. In this case, you will need to recover your Windows.

Regedit override

You will most likely see a blue screen with a Stop code: INACCESSIBLE BOOT DEVICE.

Windows will attempt to restart and automatically diagnose and repair the boot-related problems, but it will most likely not be able to complete the task itself, and you will need to manually launch the command prompt from the recovery screen, and fix the issue.

System boot

### Open the command prompt

Automatic repair

On the screen that gives you the result of the Automatic Repair, click on Advanced Options. Under Choose an option, select Troubleshoot. Next, selected Advanced Options again. Finally, select Command Prompt.

Automatic repair did not work

Choose an option

Troubleshoot

### Diagnose the problem

This will launch the Windows command prompt, where you can run commands to diagnose and repair problems, including boot-related issues. The first step is to run the disk partition tool to see and understand the disk layout.

Command prompt

1. From the command prompt, start the `diskpart` utility:

    ```text
    diskpart
    ```

1. Display the list of volumes:

    ```text
    list volume
    ```

    Make sure the volume that contains Windows is correctly assigned the letter `C:`.

1. If the Windows volume isn't `C:`, you need to change this using the following commands:

    ```text
    select volume [number]
    ```

    ```text
    assign letter=[letter]
    ```

    For example, a "wrong" volume may be assigned the letter `C:`. Select it first, assign it a different letter (e.g. `F:` or `H:`), select the volume that contains Windows, and then assign it the letter `C:`.

1. Activate the `C:` volume:

    ```text
    activate
    ```

1. Exit the `diskpart` utility:

    ```text
    exit
    ```

### Repair the problem

1. Run the `bcdedit repair` command:

    ```text
    bcdedit /deletevalue {default} safeboot
    ```

1. If the previous command does not work, try alternative commands:

    ```text
    bcdedit /deletevalue {current} safeboot
    ```

    ```text
    bcdedit /deletevalue safeboot
    ```

1. If the previous command completes successfully, exit the command prompt, the Windows recovery console will restart, and Windows should load normally, with the controller mode set to AHCI.

    If Windows does not start correctly, you can then manually recreate the bootloader file.

### Recreating the bootloader file

To this end, you need to access either the System partition or the EFI partition on your computer. The Windows disk layout typically includes one of these two configurations:

* A volume that contains Windows (`C:`) and a small hidden partition, usually 100MB in size called System partition, formatted as NTFS. It contains the files needed to start (boot) Windows, as well as recovery tools to help you diagnose and repair your system when it does not start correctly.

* On UEFI-based computers, a volume that contains Windows (`C:`) and a boot partition (also called EFI), typically 256-512MB in size, formatted as FAT32. This partition contains the files needed to start (boot) Windows.

You need to access the partition to make the necessary changes.

If you have already run the `diskpart` utility, you do not need to do anything at this point, you only need to check the letter that is assigned to this partition (e.g. letter `F:`).

Assuming letter `F:` for the boot partition, use the following commands:

1. Switch to the boot partition:

    ```text
    F:
    ```

    ```text
    cd boot
    ```

1. Move the existing boot file aside:

    ```text
    ren BCD BCD.bak
    ```

1. Create a new one:

    ```text
    bcdboot c:\windows /l en-us /s f: /f ALL
    ```

    The `bcdboot` command initializes the system partition by using BCD files from the `C:\Windows` folder.

    Use the `en-us` locale (`/l en-us`), target the system partition assigned letter `F:` (`/s` option), and create boot files both for UEFI and BIOS (`/f ALL` option).

1. Once the previous command completes, reboot. Windows should start normally.

1. You can now re-launch the Ubuntu installer and finish the side-by-side setup of the two operating systems.

