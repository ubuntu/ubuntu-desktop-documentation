```{tags} Installation, Security
```

(encrypt-your-disk-with-tpm)=
# Encrypt your disk with TPM

Hardware-backed disk encryption protects the data on your disk using the Trusted Platform Module (TPM) chip. It encrypts your Ubuntu installation and your whole disk. Compared to traditional encryption methods such as LUKS, hardware-backed disk encryption can provide more convenience or more security, depending on your configuration.

To learn how this encryption works, see {ref}`hardware-backed-disk-encryption`.

:::{warning}
Hardware-backed disk encryption is currently a **Beta feature**. You can't use this setup on machines that require third-party, out-of-tree drivers, such as to support certain webcams or virtualization solutions. Drivers for NVIDIA graphics cards are supported.
:::


## Enable the encryption during installation

You can enable hardware-backed encryption when you install Ubuntu Desktop. You cannot enable or disable it after installation.

To install Ubuntu with hardware-backed encryption:

1. Follow the instructions in {ref}`install-ubuntu-desktop` until {guilabel}`Disk setup`.

1. On the {guilabel}`Disk setup` screen, select {menuselection}`Erase disk and install Ubuntu --> Use hardware-backed disk encryption`.

    :::{note}
    Your system might not support all the required security features. In that case, the installer doesn't allow you to select the hardware-backed disk encryption. For more information, refer to the requirements.
    :::

1. On the {guilabel}`Create your account` screen, set a secure password for all user accounts. Without an encryption passphrase, your data is only as safe as the weakest of the user passwords.

1. When the installation is done, the installer shows your recovery key for your encrypted disk.

    You can save the recovery key as a text file on another USB stick. You can also load the QR code with your phone or take a photo of the screen showing the recovery key.

    **Store it somewhere safe**, such as in a password manager.

    :::{important}
    If you lose your recovery key, you might lose access to your data in certain scenarios. While you're logged in, replace the existing recovery key as soon as possible. See {ref}`tpm-fde-get-a-new-recovery-key`.
    :::

1. After starting your new Ubuntu Desktop system, you can optionally {ref}`tpm-fde-set-passphrase`.

## Configure the encryption after installation

Refer to {ref}`configure-hardware-backed-disk-encryption`.
