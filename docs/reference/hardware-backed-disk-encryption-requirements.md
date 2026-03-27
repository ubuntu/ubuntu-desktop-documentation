```{tags} Installation, Security
```

(hardware-backed-disk-encryption-requirements)=
# Hardware-backed disk encryption requirements

Ubuntu checks certain system requirements before it allows you to enable TPM/FDE on your system. These requirements might be stricter than with other comparable solutions, such as BitLocker on Windows. The reason for these strict requirements is to guarantee user security.

A large set of TPM configurations is compatible, on Intel and AMD processors.

If the system is not in a state to allow TPM/FDE installation, but remediation exists, some actions (automated or manual) are described and proposed to the user. Some may require a reboot for those modifications to be made and the same selection needs to be redone manually.

## Less restrictive requirements

- UEFI (no minimum version) that meets the PCR usage and log requirements of the TCG EFI PC Client Platform Profile spec (2.0 family), and which implements the TCG EFI Protocol spec (2.0 family). Many systems meet this requirement, although some older implementations support 1.2 family versions of the TCG specs, which is not supported.
- A PC-client TPM2 device, at least 1.32 of the reference library spec. Windows 11 now requires TPM2 on every system.
- Secure Boot is enabled (and currently with deployed mode on for UEFI >= 2.5 although we plan to add a way to opt in to installing with just user mode).

## More restrictive requirements

- Firmware is verified or at least measured by a hardware root of trust. This is to check that all the signatures under the root of trust are working. The root of trust verifies the first signature and so this one can't be tempered with. This is a requirement that BitLocker on Windows typically doesn't have.
    - For Intel systems, that's the BootGuard Authenticated Code Module (ACM). We require forced verification for now.
    - For AMD systems, that's currently anything with PSB enabled but will be extended to any modern AMD CPU with the secure processor.

## Report bugs

If you think that your system should be eligible for TPM/FDE given these requirements, but Ubuntu still doesn't enable TPM/FDE, open a bug.
