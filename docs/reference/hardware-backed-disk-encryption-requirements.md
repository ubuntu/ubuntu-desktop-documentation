```{tags} Installation, Security
```

(hardware-backed-disk-encryption-requirements)=
# Hardware-backed disk encryption requirements

Ubuntu checks certain system requirements before it allows you to enable {ref}`hardware-backed disk encryption <hardware-backed-disk-encryption>` (TPM/FDE) on your system. Generally, many systems based on Intel and AMD processors are compatible with TPM/FDE. However, these requirements might be stricter than with other disk encryption solutions, such as BitLocker on Windows. The reason for these strict requirements is to guarantee strong user security.

In some cases, your system doesn't allow TPM/FDE as is but it's possible to reconfigure it to enable the requirements. The Ubuntu installer proposes certain automated or manual actions. Some might require a reboot to apply the modifications and the same selection needs to be redone manually.

## Less restrictive requirements

Some of the TPM/FDE requirements are widely supported by many systems. As a rule of thumb, hardware made since 2017 is compatible with these:

- The UEFI firmware (no minimum version) with the following features:

    - It meets the PCR usage and log requirements of the TCG EFI PC Client Platform Profile specification (2.0 family).
    - It implements the TCG EFI Protocol spec (2.0 family). Some older UEFI implementations only support 1.2 family versions of the TCG specifications, which is insufficient for TPM/FDE.

- A PC-client TPM2 device, at least version 1.32 of the reference library specification.

    All recent PC hardware certified for Windows 11 meets this requirement.

- Secure Boot is enabled.

    Currently, Ubuntu requires Secure Boot to be in Deployed Mode, which raises the requirements to UEFI version 2.5 or later. Eventually, the plan is to extend the support to User Mode, too.

## More restrictive requirements

Some requirements are only met by a relatively few systems:

- The UEFI firmware is verified or at least measured by a hardware root of trust.

    This is to check that all the signatures under the root of trust are working. The root of trust verifies the first signature and so this one can't be tempered with. This is a requirement that BitLocker on Windows typically doesn't have.

    - For Intel systems, that's the BootGuard Authenticated Code Module (ACM). We require forced verification for now.
    - For AMD systems, that's currently anything with PSB enabled but will be extended to any modern AMD CPU with the secure processor.

## Report bugs

If you think that your system should be eligible for TPM/FDE given these requirements, but Ubuntu still doesn't enable TPM/FDE, open a bug.
