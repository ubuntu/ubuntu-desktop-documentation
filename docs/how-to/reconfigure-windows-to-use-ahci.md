(reconfigure-windows-to-use-ahci)=
# Reconfigure Windows to use AHCI

If the Ubuntu installer detects RST, and Windows is installed on your system, these steps enable Ubuntu to install side by side with Windows, without any loss of data and functionality.

To learn more about RST and its behavior with Ubuntu, see {ref}`intel-rst-during-ubuntu-installation`.


## Back up your data

Any hard drive structure or configuration change, or installation of new operating systems on a hard drive that already contains data might potentially lead to a data loss.

Make sure that your personal data is safe. Even simply copying the important files to an external drive minimizes the risk of data loss.


## Find the current controller mode

1. Open the Device Manager.

1. Under {guilabel}`IDE ATA/ATAPI controllers`, verify which controller mode is in use in Windows.

    If the controller mode is set to anything other than {guilabel}`Standard SATA AHCI Controller`, you need to make a change that allows Windows to boot safely in AHCI mode. This can be done using the Registry Editor.


## Change the controller mode

1. Start Registry Editor, and navigate to the following path:

    ```text
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\iaStorV\
    ```

    ![Regedit](/images/windows-ahci/Regedit.png)

1. In the right column, double-click the `Start` key, and change its value to `0`.

1. Double-click the `iaStorV` entry in the left column to expand it and select the `StartOverride` entry.

1. In the right column, change the value of the key `0` to `0`.

    ![Regedit override](/images/windows-ahci/Regedit-override-dword.png)

1. Repeat these changes for the following path in the Registry Editor, if the path exists on your system:

    ```text
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\storahci\
    ```

1. Open the System Configuration app. You can find it by entering `msconfig` in the Windows search menu.

1. On the {guilabel}`Boot` tab, enable {guilabel}`Safe boot` in the {guilabel}`Boot options` frame. Confirm by clicking {guilabel}`OK`.

1. Reboot the system and start your computer’s firmware (BIOS or UEFI).

    Usually, you can access the firmware by pressing the {kbd}`F2` or {kbd}`Del` key during the early boot sequence.

1. In the firmware menu, change the disk controller type to AHCI.

    The exact terminology and steps to manage the controller type in the firmware depend on the implementation by the platform vendor.

1. Exit the firmware and let the system boot.

    Windows enters safe mode and sets up the hardware using the temporarily enabled drivers.

1. Check the controller mode in the Device Manager.

    It should read: {guilabel}`Standard SATA AHCI Controller`.

    ![Regedit override](/images/windows-ahci/Regedit-override.png)

1. Open the System Configuration app again and disable {guilabel}`Safe boot`.

1. Reboot. Windows starts normally.

## Troubleshooting boot problems

After making the necessary changes to enable Ubuntu to install side by side with Windows, Windows might no longer boot. For instance, this might happen if you made the firmware change without making the registry changes in Windows. In this case, you need to recover your Windows installation.

![The INACCESSIBLE BOOT DEVICE error screen](/images/windows-ahci/INACCESSIBLE-BOOT-DEVICE.png)

You will most likely see a blue screen with a Stop code: `INACCESSIBLE BOOT DEVICE`.

Windows attempts to restart and automatically diagnose and repair the boot-related problems, but it will probably fail to complete the task itself. You need to manually launch the command prompt from the recovery screen and fix the issue.

### Open the command prompt

1. On the screen that gives you the result of the Automatic Repair, click {guilabel}`Advanced options`.

    ![The Automatic Repair screen](/images/windows-ahci/Automatic-repair.png)

1. From the {guilabel}`Choose an option` screen, go to {menuselection}`Troubleshoot --> Advanced options --> Command Prompt`.

    ![Automatic repair did not work](/images/windows-ahci/Automatic-repair-did-not-work.png)

### Diagnose the problem

The Windows command prompt opens. Here, you can run commands to diagnose and repair problems, including boot-related issues.

![The command prompt](/images/windows-ahci/Windows-command-prompt.png)

1. From the command prompt, run the disk partition tool to see and understand the disk layout:

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

    For example, a "wrong" volume might be assigned the letter `C:`. Select it first, assign it a different letter (e.g. `F:` or `H:`), select the volume that contains Windows, and then assign it the letter `C:`.

    ![Disk partitioning example](/images/windows-ahci/windows-10-diskpart.png)

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

    The options used in the command:

    `/l en-us`
    : Use the `en-us` locale.

    `/s f:`
    : Target the system partition assigned letter `F:`.

    `/f ALL`
    : Create boot files both for UEFI and BIOS.

1. Once the previous command completes, reboot. Windows should start normally.

1. You can now re-launch the Ubuntu installer and finish the side-by-side setup of the two operating systems.

