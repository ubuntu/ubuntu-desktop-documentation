(hardware-backed-disk-encryption)=
# Hardware-backed disk encryption

Hardware-backed encryption is a convenient way to keep your data secure. Usually, you only need to enter your Ubuntu user password to get access to your data, unless you decide to set an optional passphrase for additional security.

The data on your disk will be decrypted automatically, while still keeping your data encrypted at rest. This eliminates the need to enter a passphrase every time you start up your machine: you will just need to enter your user password as usual to log in. Optionally, you can still set a passphrase for additional security.


## How hardware-backed encryption works

When enabling hardware-backed encryption, the encryption keys for your disk are automatically generated and stored safely in your computer’s Trusted Platform Module (TPM).

Every startup, the TPM will verify that your computer's hardware and critical boot software have not been altered. If any unauthorized changes are detected, the TPM will refuse to unlock the disk, unless changes are reverted or a recovery key is provided. This means your data is protected even if your device is stolen: the disk cannot be unlocked if removed and installed on another computer.

You can learn about the technical details in the [TPM-backed Full Disk Encryption is coming to Ubuntu](https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu) blog post.


(tpm-fde-encryption-passphrase)=
## Encryption passphrase

You can require a passphrase every time you start your computer for additional security. Encryption passphrases are alphanumerical.

When you set a passphrase, your disk is encrypted by both the automatically-generated encryption keys, stored in your TPM, and your passphrase. As a result, your passphrase would still be needed to decrypt your disk even if the TPM gets compromised (for instance, because of a malicious firmware update from the TPM manufacturer). This feature is particularly useful in security-conscious contexts, for users that handle sensitive data or that may be subject to targeted attacks.

You can enable the encryption passphrase during installation. After installation, you can change the passphrase in the Security Center, but you can't disable it.


## Recovery key

Once Ubuntu Desktop is installed, you will be shown a recovery key for your encrypted disk. You should save the recovery key somewhere safe to avoid losing access to all your data. If you lose your recovery key, you should replace the existing recovery key with a new one in the Security Center as soon as possible.

You may be asked to provide a recovery key on boot if the system detects certain suspicious events, including:

* Changes to hardware components in your computer
* Updates to BIOS, UEFI and firmware
* Changes to boot settings, such as boot order or secure boot
* Errors with authentication, such as entering a wrong password too many times
* Changes to configuration settings, such as organization security policies
* Resetting or clearing of the TPM module

To avoid losing access to your data, keep your recovery key somewhere safe at all times.

Once Ubuntu Desktop is installed, you will be shown a recovery key for your encrypted disk. If you lose your recovery key, you should replace the existing recovery key with a new one as soon as possible.


## Use recovery keys for other operating systems

You should store recovery keys somewhere safe for any other encrypted drives or operating systems that you have installed in your computer. You may need individual recovery keys for each of them in case of the same events outlined above. Please note that updating firmware with the Firmware Updater in Ubuntu might require you to provide recovery keys for other non-Ubuntu drives.

If you use BitLocker on Windows or have an encrypted Windows installation in your machine, check Microsoft’s documentation on how to [back up](https://support.microsoft.com/en-us/windows/back-up-your-bitlocker-recovery-key-e63607b4-77fb-4ad3-8022-d6dc428fbd0d) and [find](https://support.microsoft.com/en-us/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6) recovery keys.

If you need to apply changes to your system, you can also disable BitLocker temporarily and re-enable BitLocker after the changes have been made. See {ref}`turn-off-bitlocker-in-windows` and {ref}`bitlocker-during-ubuntu-installation`.

When using recovery keys for other platforms, please check the relevant vendor’s documentation.

