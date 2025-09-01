(encrypt-your-disk-with-tpm)=
# Encrypt your disk with TPM

Hardware-backed full-disk encryption is an **experimental feature** to protect your data using the Trusted Platform Module (TPM) chip. It encrypts your Ubuntu installation and your whole disk. Compared to traditional encryption methods such as LUKS, hardware-backed full-disk encryption can provide more convenience or more security, depending on your configuration.

To learn how this encryption works, see {ref}`hardware-backed-disk-encryption`.


## Enable hardware-backed encryption during installation

You can enable hardware-backed encryption when you install Ubuntu Desktop. You cannot enable or disable it after installation.

To install Ubuntu with hardware-backed encryption:

1. Follow the instructions in {ref}`install-ubuntu-desktop` until {guilabel}`Disk setup`.

1. On the {guilabel}`Disk setup` screen, select {menuselection}`Advanced features --> Enable hardware-backed disk encryption`.

1. Optional: For an additional layer of security, consider adding an **encryption passphrase**.

    The encryption passphrase is an alphanumerical password that you enter every time your computer starts up to unlock the disk. After installation, you can change the passphrase but you can't disable it.

    To learn when you might want to enable the passphrase, see {ref}`tpm-fde-encryption-passphrase`.

1. On the {guilabel}`Create your account` screen, set a secure password for all user accounts. Without an encryption passphrase, your data is only as safe as the weakest of the user passwords.

1. Once Ubuntu Desktop is installed, you get a recovery key for your encrypted disk. **Store it somewhere safe**, such as in a password manager.

    ::::{tab-set}

    :::{tab-item} Ubuntu 24.04 LTS
    :sync: ubuntu-24-04

    After installation, start your new system and display your recovery key in a terminal:

    ```bash
    sudo snap recovery --show-keys
    ```
    :::

    :::{tab-item} Ubuntu 25.10 and newer
    :sync: ubuntu-25-10

    The Ubuntu installer shows your recovery key when the installation is finished.
    :::

    ::::

    :::{warning}
    If you lose your recovery key, you might lose access to your data in certain scenarios. While you're logged in, replace the existing recovery key as soon as possible. See {ref}`tpm-fde-get-a-new-recovery-key`.
    :::



(tpm-fde-get-a-new-recovery-key)=
## Get a new recovery key

Ubuntu Desktop shows you your disk recovery key right after installation. If you lose your recovery key, replace it as soon as possible. Otherwise, you risk losing access to your data.

To get the recovery key, you must be logged into your Ubuntu user account.

::::{tab-set}

:::{tab-item} Ubuntu 24.04 LTS
:sync: ubuntu-24-04

In Ubuntu 24.04 LTS, you can retrieve the existing recovery key and you can't change it.

To display the recovery key for your encrypted disk, open a terminal and run this command:

```bash
sudo snap recovery --show-keys
```
:::

:::{tab-item} Ubuntu 25.10 and newer
:sync: ubuntu-25-10

In Ubuntu 25.10 and newer, you can't retrieve the existing recovery key but you can get a new one.

You need to be an administrator on your system to replace the recovery key.

1. Go to the {menuselection}`Security Center --> Disk Encryption`.
1. Select {guilabel}`Replace recovery key…`.
1. The Security Center displays your new recovery key. The previous recovery key stops working as soon as you select {guilabel}`Replace`.
:::

::::

Store your new recovery key somewhere safe, such as in a password manager.


## What to do if you don’t have a recovery key

Your computer might be asking for a recovery key but you don’t have one.

If you're logged into your Ubuntu user account, you can retrieve or reset your recovery key. See {ref}`tpm-fde-get-a-new-recovery-key`.

If your computer is asking for your recovery key during startup, try undoing any recent changes to your computer. For example:

1. Remove any new hardware components.
1. Undo any changes to boot settings.
1. Reboot your computer.
1. Try to log in again.

You can also check if the recovery key was automatically stored in the cloud. Recovery keys for the Windows BitLocker encryption may be stored on your Microsoft Account or your organization account. See [Find your BitLocker recovery key](https://support.microsoft.com/en-us/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6) in the Microsoft Windows documentation.

