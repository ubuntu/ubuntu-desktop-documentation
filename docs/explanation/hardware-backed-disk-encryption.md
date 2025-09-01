---
relatedlinks: "[TPM-backed &#32; Full &#32; Disk &#32; Encryption &#32; is &#32; coming &#32; to &#32; Ubuntu](https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu), [Full &#32; disk &#32; encryption: &#32; LUKS &#32; and &#32; TPM](https://documentation.ubuntu.com/security/docs/security-features/storage/encryption-full-disk/), [Full &#32; disk &#32; encryption &#32; in &#32; Ubuntu &#32; Core](https://documentation.ubuntu.com/core/explanation/full-disk-encryption/), [BitLocker &#32; overview &#32; by &#32; Microsoft](https://learn.microsoft.com/en-us/windows/security/operating-system-security/ data-protection/bitlocker/)"
---

(hardware-backed-disk-encryption)=
# Hardware-backed disk encryption

Hardware-backed disk encryption is a convenient way to keep your data secure. It automatically decrypts the data on your disk at startup, while keeping your data encrypted at rest. This eliminates the need to enter a passphrase every time you start up your machine: you just need to enter your user password to log in. Optionally, you can set a disk encryption passphrase for additional security.

:::{warning}
Hardware-backed disk encryption is currently an **experimental feature**. Use it only on systems where you don't mind if you accidentally lose   your data.
:::


## How hardware-backed disk encryption works

When you enable hardware-backed disk encryption, the encryption keys for your disk are automatically generated and stored safely in your computer’s Trusted Platform Module (TPM).

At every startup, the TPM verifies that your computer's hardware and critical boot software have not been altered. If TPM detects any unauthorized changes, it refuses to unlock the disk, unless the user reverts the changes or provides a recovery key. This means that your data is protected even if your device is stolen: the bad actor can't unlock your disk if they remove the disk and install it in another computer.

In other words, anyone who wants to access your data must know your user password. This provides more security than an unencrypted Ubuntu installation, where the bad actor can just remove your disk and read your data, or start another system on your computer. This feature is also more convenient than traditional disk encryption, such as LUKS: you only have to remember your user password and there's no additional disk password.

For technical details, see [Full disk encryption (FDE)](https://documentation.ubuntu.com/security/docs/security-features/storage/encryption-full-disk/) in the Ubuntu security documentation.


## Recovery key

A recovery key is a long string of numbers that you can use to recover the data on your encrypted disk. You receive the recovery key during or after the Ubuntu installation, depending on your Ubuntu release.

You should store it somewhere safe outside of your computer, such as in a cloud-based password manager.

Ubuntu 24.04 LTS stores the recovery key in a readable form and you can retrieve it. Starting with Ubuntu 25.10, the recovery key is stored in an encrypted form. There, you can't retrieve it but you can reset it in the Security Center to get a new one. However, in both cases you must be able to log into Ubuntu before you can get your recovery key.

:::{important}
If you lose your recovery key, you might lose access to your data in certain scenarios. While you're logged in, replace the existing         recovery key as soon as possible. See {ref}`tpm-fde-get-a-new-recovery-key`.
:::

(tpm-fde-when-ubuntu-asks-for-your-recovery-key)=
### When Ubuntu asks for your recovery key

You need the recovery key in several different situations:

* If you **move your disk** to a new computer, you need to enter your recovery key before your new computer can access the data.

* If you **forget your disk passphrase**, Ubuntu asks for your recovery key to unlock the disk.

* If you **change the hardware, firmware** or other components of your computer, you need to enter your recovery key to confirm that you trust the new configuration. This includes the following changes:

    * Changes to hardware components in your computer
    * Updates to BIOS, UEFI and firmware
    * Changes to boot settings, such as boot order or Secure Boot
    * Errors with authentication, such as entering a wrong password too many times
    * Changes to certain settings, such as organization security policies
    * Resetting or clearing of the TPM module

If you're planning to do any of these changes on your computer, make sure that you know your recovery key first.

:::{warning}
If the system asks you for your recovery key even when no hardware or software on your computer has changed, it might be an attack that tries to gain access to your data.
:::


## Ubuntu alongside another encrypted system

If you have additional encrypted drives or another encrypted operating system on your computer, make sure to safely store the recovery keys to all your drives.

For example, if you install Ubuntu with hardware-backed disk encryption alongside Microsoft Windows with BitLocker enabled, you need to store both recovery keys for Ubuntu and Windows.

You might need individual recovery keys for each drive in case of the events listed in {ref}`tpm-fde-when-ubuntu-asks-for-your-recovery-key`. Updating firmware with the Firmware Updater in Ubuntu might require you to provide recovery keys for non-Ubuntu drives, too.

### Windows BitLocker

If you use BitLocker on Windows or have an encrypted Windows installation in your machine, see the Microsoft documentation on how to [back up](https://support.microsoft.com/en-us/windows/back-up-your-bitlocker-recovery-key-e63607b4-77fb-4ad3-8022-d6dc428fbd0d) and [find](https://support.microsoft.com/en-us/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6) recovery keys.

If you need to apply changes to your system, you can also disable BitLocker temporarily and re-enable BitLocker after the changes have been made. See {ref}`turn-off-bitlocker-in-windows` and {ref}`bitlocker-during-ubuntu-installation`.

### Other platforms

When using recovery keys for other platforms, see the relevant vendor’s documentation.


(tpm-fde-encryption-passphrase)=
## Encryption passphrase

Optionally, you can set a passphrase for additional security. The encryption passphrase is alphanumerical and you enter it every time your computer starts.

When you set a passphrase, your disk is encrypted by both the automatically-generated encryption keys, stored in your TPM, and your passphrase. As a result, your passphrase is still needed to decrypt your disk even if the TPM gets compromised. For instance, the passphrase protects you against a malicious firmware update from the TPM manufacturer.

Enabling the passphrase is particularly useful in the following cases:

* In security-conscious contexts
* For users that handle sensitive data
* For users that might be subject to targeted attacks

Consider the different impact on laptops, desktops and servers as well:

* In a **server** environment, it's more likely that somebody steals your disk rather than the whole computer. Therefore, you might prefer encryption without a passphrase, which ensures disk security and doesn't require physical access to reboot the server.

* With a **laptop**, it's more likely that somebody steals your whole computer when traveling, for example. Therefore, you might want to add the disk encryption passphrase so that your data is protected even before the bad actor tries to break through your login screen.

* With a **desktop** computer, consider which of the risk factors is more likely.

You can enable the encryption passphrase during installation. After installation, you can change the passphrase in the Security Center, but you can't disable it.


## Enable hardware-backed disk encryption

To protect your Ubuntu installation with hardware-backed disk encryption, see {ref}`encrypt-your-disk-with-tpm`.

