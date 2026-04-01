```{tags} Installation, Security
```

(encrypt-your-disk-with-tpm)=
# Encrypt your disk with TPM

Hardware-backed disk encryption protects the data on your disk using the Trusted Platform Module (TPM) chip. It encrypts your Ubuntu installation and your whole disk. Compared to traditional encryption methods such as LUKS, hardware-backed disk encryption can provide more convenience or more security, depending on your configuration.

To learn how this encryption works, see {ref}`hardware-backed-disk-encryption`.

:::{warning}
Hardware-backed disk encryption is currently an **experimental feature**. Use it only on systems where you don't mind if you accidentally lose your data.

This feature currently supports only the generic kernel. This means that you can’t use this setup on machines that require additional drivers to support webcams or NVIDIA graphics cards. In addition, certain hardware vendors might enable BIOS options that alter the chain of trust.
:::


## Enable the encryption during installation

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

    After installation, start your new system and enter the following command in a terminal:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo snap recovery --show-keys
    ```

    The command displays your recovery key.
    :::

    :::{tab-item} Ubuntu 25.10 and newer
    :sync: ubuntu-25-10

    The Ubuntu installer shows your recovery key when the installation is finished.

    You can save the recovery key as a text file on another USB stick. You can also load the QR code with your phone or take a photo of the screen showing the recovery key.
    :::

    ::::

    :::{important}
    If you lose your recovery key, you might lose access to your data in certain scenarios. While you're logged in, replace the existing recovery key as soon as possible. See {ref}`tpm-fde-get-a-new-recovery-key`.
    :::

## Configure the encryption after installation

Refer to {ref}`configure-hardware-backed-disk-encryption`.
