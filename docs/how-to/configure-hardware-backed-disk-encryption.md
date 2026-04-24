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

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Security Center app.
1. Go to the Disk Encryption tab.
1. Click {guilabel}`Add PIN` or {guilabel}`Add passphrase`.
1. Enter a numeric PIN or an alphanumeric passphrase and confirm.
:::

:::{tab-item} Command line
:sync: terminal
1. Make sure that the `snap-tpmctl` tool is installed:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo snap install snap-tpmctl
    ```

1. Add a PIN or passphrase:

    * PIN:
    
        ```{terminal}
        :copy:
        :user:
        :host:
        :dir:
        sudo snap-tpmctl add-pin
        ```

    * Passphrase:
    
        ```{terminal}
        :copy:
        :user:
        :host:
        :dir:
        sudo snap-tpmctl add-passphrase
        ```

Later, you can change your PIN or passphrase using the `replace-pin` and `replace-passphrase` subcommands.
:::
::::

The next time you reboot, your system asks for your PIN or passphrase. Alternatively, you can also enter the disk recovery key if you forget your PIN or passphrase.


(tpm-fde-get-a-new-recovery-key)=
## Get a new recovery key

Ubuntu Desktop shows you your disk recovery key right after installation. If you lose your recovery key, replace it as soon as possible. Otherwise, you risk losing access to your data. You can't retrieve the existing recovery key but you can get a new one.

To get the recovery key, you must be logged into your Ubuntu user account.

:::{important}
If you can't log in, you have no way to get a new recovery key. In that case, follow {ref}`tpm-fde-no-recovery-key`.
:::

You need to be an administrator on your system to replace the recovery key.

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui

1. Go to the {menuselection}`Security Center --> Disk Encryption`.
1. Select {guilabel}`Replace recovery key…`.
1. The Security Center displays your new recovery key. The previous recovery key stops working as soon as you select {guilabel}`Replace`.
1. Store your new recovery key somewhere safe, such as in a password manager.
:::

:::{tab-item} Command line
:sync: terminal
1. Make sure that the `snap-tpmctl` tool is installed:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo snap install snap-tpmctl
    ```

1. Replace the recovery key:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo snap-tpmctl regenerate-recovery-key
    ```

1. Store your new recovery key somewhere safe, such as in a password manager.
:::
::::


## Manage recovery keys for an organization

You can centrally manage the recovery keys for multiple systems encrypted with TPM/FDE. This is useful if you're the system administrator at an organization where you need centralized control over all encrypted systems ("escrow"). In this setup, TPM/FDE adds a secondary recovery key on each system. This secondary key is subject to central management.

:::{warning}
If the local user of the managed system has root privileges, they can modify both recovery keys on their system using the `snap-tpmctl` tool. The Security Center only gives access to the primary, local recovery key.
:::

Recovery key management is integrated into the **Landscape** systems administration tool. For details, refer to the [Landscape documentation](https://documentation.ubuntu.com/landscape/).

Alternatively, you can build a custom central management solution based on the interfaces provided by the `snap-tpmctl` tool:

:::{dropdown} Relevant commands
* List all recovery keys:

  ```{terminal}
  :copy:
  :user:
  :host:
  :dir:
  sudo snap-tpmctl list-recovery-keys
  ```

* Add a secondary recovery key:

  ```{terminal}
  :copy:
  :user:
  :host:
  :dir:
  sudo snap-tpmctl create-recovery-key
  ```

* Erase all recovery keys and replace them:

  ```{terminal}
  :copy:
  :user:
  :host:
  :dir:
  sudo snap-tpmctl regenerate-recovery-key
  ```

For other options, refer to the `snap-tpmctl help` command.
:::


(tpm-fde-no-recovery-key)=
## What to do if you don’t have a recovery key

Your computer might be asking for a recovery key but you don’t have one.

If you're logged into your Ubuntu user account, you can retrieve or reset your recovery key. See {ref}`tpm-fde-get-a-new-recovery-key`.

If your computer is asking for your recovery key during startup, try undoing any {ref}`recent changes <tpm-fde-when-ubuntu-asks-for-your-recovery-key>` to your computer. For example:

1. Remove any new hardware components.
1. Undo any changes to boot settings.
1. Reboot your computer.
1. Try to log in again.

You can also check if the recovery key was automatically stored in the cloud:

* If your system is managed via Landscape, contact your Landscape administrator for your recovery key.
* Recovery keys for the Windows BitLocker encryption may be stored on your Microsoft Account or your organization account. See [Find your BitLocker recovery key](https://support.microsoft.com/en-us/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6) in the Microsoft Windows documentation.

## Additional resources

- {ref}`recover-data-from-hardware-backed-disk-encryption`
