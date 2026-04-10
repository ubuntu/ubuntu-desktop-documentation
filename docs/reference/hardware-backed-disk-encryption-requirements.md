```{tags} Installation, Security
```

(hardware-backed-disk-encryption-requirements)=
# Hardware-backed disk encryption requirements

Ubuntu checks certain system requirements before it allows you to enable {ref}`hardware-backed disk encryption <hardware-backed-disk-encryption>` (TPM/FDE) on your system. Generally, **most systems based on Intel and AMD processors made since 2021** are compatible with TPM/FDE. However, the requirements are stricter than with other disk encryption solutions, such as BitLocker on Windows. These strict requirements exist to guarantee strong security.

```{include} /reuse/tpm-fde-disclaimer.txt
```

Your hardware must meet the following requirements to support TPM/FDE:

- Your devices comes with the Unified Extensible Firmware Interface (UEFI) version 2.5 or later with the following features:

    - It meets the Platform Configuration Register (PCR) usage and log requirements of the Trusted Computing Group (TCG) EFI PC Client Platform Profile specification (2.0 family).
    - It implements the TCG EFI Protocol spec (2.0 family). Some older UEFI implementations only support 1.2 family versions of the TCG specifications, which is insufficient for TPM/FDE.

- Your device has a PC-client Trusted Platform Module version 2 (TPM2) chip, version 1.32 of the reference library specification or later.

- Secure Boot is enabled.

    Currently, Ubuntu requires Secure Boot to be in Deployed Mode.

- The UEFI firmware is verified or at least measured by a hardware root of trust.

    To verify or measure the firmware, your device must feature a dedicated security chip:

    - The Boot Guard Authenticated Code Module (ACM) on Intel systems. Forced verification is required for now.
    - Platform Secure Boot (PSB) enabled on AMD systems.
    
    :::{note}
    Certain hardware vendors might enable firmware options that alter the chain of trust, such as the [Absolute Persistence](https://www.absolute.com/platform/persistence) technology.

    The Ubuntu installer alerts you to this. You can choose to disable the feature if you have the permissions or you can ignore the notice to keep the feature enabled.
    :::

## Strict security requirements

Most of the listed TPM/FDE requirements are widely supported by the majority of PCs made since 2018. Other hardware-backed disk encryption solutions, such as BitLocker on Microsoft Windows, require a similar set of hardware features.

However, TPM/FDE on Ubuntu also checks for a hardware root of trust. This final requirement is much stricter than with the other solutions. It raises the requirements to PCs made since 2021, generally speaking.

With a hardware root of trust, your hardware verifies the UEFI firmware before the firmware runs, based on a read-only piece of code in your CPU. This protects your disk encryption against threats such as malware that targets your firmware, or supply-chain attacks while your hardware is handled after manufacture.

As a consequence of this security requirement, you can't install Ubuntu with TPM/FDE on certain systems that support BitLocker on Microsoft Windows.

## Report bugs

If you think that your system should be eligible for TPM/FDE given these requirements, but Ubuntu still doesn't enable TPM/FDE, [open a bug](https://github.com/canonical/secboot/issues/new).
