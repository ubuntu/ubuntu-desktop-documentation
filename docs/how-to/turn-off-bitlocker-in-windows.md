```{tags} Installation, Security, Windows
```

(turn-off-bitlocker-in-windows)=
# Turn off BitLocker in Windows

You can disable the BitLocker disk encryption used by Windows so that Ubuntu can access the data. This might be necessary to install Ubuntu alongside Windows.

To learn more about BitLocker and its implications for Ubuntu, see {ref}`bitlocker-during-ubuntu-installation`.

:::{warning}
Certain versions of Windows will no longer allow you to re-enable BitLocker after disabling it.

If you wish to re-encrypt your Windows partition after installing Ubuntu alongside it, check that your version of Windows supports this.
:::

1. Back up your data:

    Any encryption procedure, hard drive structure change or installation of new operating systems on a hard drive that already contains data can potentially lead to a data loss. Make sure that your personal data is safe. Even simply copying the important files to an external drive minimizes the risk of data loss.

1. In Windows, open the Settings app and go to {menuselection}`Privacy & Security --> Device Encryption`. Toggle it off.

    On older versions of Windows, go to {menuselection}`Control Panel --> System and Security --> BitLocker Drive Encryption` and click {guilabel}`Turn off BitLocker`.

    ![The BitLocker Drive Encryption settings in Windows](/images/bitlocker-drive-encryption.png)

1. Windows informs you that it is going to decrypt the data.

    ![The Turn off BitLocker dialog](/images/turn-off-bitlocker.png)

    Wait until it's done.

    ![The BitLocker decryption progress dialog](/images/bitlocker-decryption-progres.png)

    ![The BitLocker decryption notice](/images/bitlocker-decryption-complete.png)

1. Once the decryption is complete, reboot the computer.

1. Log into Windows. Make sure everything works correctly and that all your data is intact.

1. The Windows data is now accessible to Ubuntu.

    If you're installing Ubuntu, you can now reboot your computer and launch the Ubuntu installer. The hard disk configuration step can proceed.
