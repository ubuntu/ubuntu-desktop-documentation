```{tags} Installation, Security
```

(configure-hardware-backed-disk-encryption)=
# Configure hardware-backed disk encryption

On an Ubuntu installation where the hardware-backed disk encryption (TPM/FDE) is enabled, you can configure certain security options. You can also recover access to your disk in certain scenarios.

```{include} /reuse/tpm-fde-disclaimer.txt
```

(tpm-fde-set-passphrase)=
## Set a disk encryption PIN or passphrase

For an additional layer of security, you can add an encryption PIN or passphrase. You enter them every time your computer starts up to unlock the disk.

To learn when you might want to enable the PIN or passphrase, see {ref}`tpm-fde-encryption-passphrase`.

1. Open the Security Center app.
1. Go to the Disk Encryption tab.
1. Click {guilabel}`Add PIN` or {guilabel}`Add passphrase`.
1. Enter a numeric PIN or an alphanumeric passphrase and confirm.

The next time you reboot, your system asks for your PIN or passphrase. Alternatively, you can also enter the disk recovery key if you forget your PIN or passphrase.


(tpm-fde-get-a-new-recovery-key)=
## Get a new recovery key

Ubuntu Desktop shows you your disk recovery key right after installation. If you lose your recovery key, replace it as soon as possible. Otherwise, you risk losing access to your data. You can't retrieve the existing recovery key but you can get a new one.

To get the recovery key, you must be logged into your Ubuntu user account.

:::{important}
If you can't log in, you have no way to get a new recovery key. In that case, follow {ref}`tpm-fde-no-recovery-key`.
:::

You need to be an administrator on your system to replace the recovery key.

1. Go to the {menuselection}`Security Center --> Disk Encryption`.
1. Select {guilabel}`Replace recovery key…`.
1. The Security Center displays your new recovery key. The previous recovery key stops working as soon as you select {guilabel}`Replace`.
1. Store your new recovery key somewhere safe, such as in a password manager.


(tpm-fde-no-recovery-key)=
## What to do if you don’t have a recovery key

Your computer might be asking for a recovery key but you don’t have one.

If you're logged into your Ubuntu user account, you can retrieve or reset your recovery key. See {ref}`tpm-fde-get-a-new-recovery-key`.

If your computer is asking for your recovery key during startup, try undoing any {ref}`recent changes <tpm-fde-when-ubuntu-asks-for-your-recovery-key>` to your computer. For example:

1. Remove any new hardware components.
1. Undo any changes to boot settings.
1. Reboot your computer.
1. Try to log in again.

You can also check if the recovery key was automatically stored in the cloud. Recovery keys for the Windows BitLocker encryption may be stored on your Microsoft Account or your organization account. See [Find your BitLocker recovery key](https://support.microsoft.com/en-us/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6) in the Microsoft Windows documentation.


## Additional resources

- {ref}`recover-data-from-hardware-backed-disk-encryption`
