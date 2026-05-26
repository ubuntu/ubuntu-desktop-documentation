```{tags} Installation
```

(advanced-disk-setup-features)=
# Advanced disk setup features

When installing Ubuntu Desktop, the installer offers several disk setup options. The recommended ones are as follows:

No encryption
: Use regular disk partitioning with no extra features.

Encrypt with a passphrase
: Enable Logical Volume Management (LVM) with disk encryption. This is the recommended option to encrypt your data.

Use hardware-backed disk encryption
: This is a new encryption method that can unlock your disk automatically without a password. For details, see {ref}`hardware-backed-disk-encryption`.

The following advanced features are available:

Use LVM without encryption
: LVM makes it easier to create and manage partitions after the installation. For details, see {external:ref}`about-lvm`.

Use ZFS without encryption
: This advanced file system allows you to create pooled storage volumes that span multiple drives. It supports snapshots and data repair features. It is a powerful option for advanced users.

Encrypt with a passphrase using ZFS
: Use ZFS and enable its data encryption feature.
