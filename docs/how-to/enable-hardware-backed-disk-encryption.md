(enable-hardware-backed-disk-encryption)=
# Enable hardware-backed disk encryption

Hardware-backed disk encryption is a feature that lets you encrypt your computer’s disk with keys that are generated and stored safely in your computer.

The data in your disk will be decrypted automatically, while still keeping your data encrypted at rest. This eliminates the need to enter a passphrase every time you start up your machine: you will just need to enter your user password as usual to log in. Optionally, you can still set a passphrase for additional security.

To learn how this encryption works, see {ref}`hardware-backed-disk-encryption`.


## Enable hardware-backed encryption during installation

You can enable hardware-backed encryption when you install Ubuntu Desktop. You cannot enable or disable it after installation.

Remember to set a secure password for all user accounts: your data will be only as safe as the weakest of the user passwords in your computer.

Once Ubuntu Desktop is installed, you will be shown a recovery key for your encrypted disk. Store it somewhere safe to avoid losing access to your data.

If you operate in security-conscious contexts, you should also consider adding an encryption passphrase.


## Add an encryption passphrase

You can require a passphrase every time you start your computer for additional security. Encryption passphrases are alphanumerical.

You can enable the encryption passphrase during installation. After installation, you can change the passphrase in the Security Center, but not disable it.


## Save your recovery key

Once Ubuntu Desktop is installed, you will be shown a recovery key for your encrypted disk. You should save the recovery key somewhere safe to avoid losing access to all your data. If you lose your recovery key, you should replace the existing recovery key with a new one in the Security Center as soon as possible.


## Get a new recovery key

Once Ubuntu Desktop is installed, you will be shown a recovery key for your encrypted disk. If you lose your recovery key, you should replace the existing recovery key with a new one as soon as possible.

::::{tab-set}

:::{tab-item} Ubuntu 24.04 LTS
:sync: ubuntu-24-04

We strongly recommend that you retrieve a recovery key as soon as possible.

To get a recovery key for your encrypted Ubuntu drive, open a terminal and run this command:

```bash
sudo snap recovery --show-keys
```
:::

:::{tab-item} Ubuntu 25.10 and newer
:sync: ubuntu-25-10

You need to be an administrator to replace the recovery key.

To replace it, go to the {menuselection}`Security Center --> Disk Encryption`. Select {guilabel}`Replace recovery key…`. A new recovery key will be generated automatically. The old recovery key stops working once you select {guilabel}`Replace`.
:::

::::


## What to do if you don’t have a recovery key

If your computer is asking for a recovery key but you don’t have one, try undoing any recent changes to your computer. For example:

1. Remove any new hardware components
1. Undo any changes to boot settings
1. Reboot your computer
1. Attempt login again

You can also check if the recovery key was automatically stored in the cloud. Recovery keys for Windows’ BitLocker [may be stored](https://support.microsoft.com/en-us/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6) on your Microsoft Account or your organization account.

