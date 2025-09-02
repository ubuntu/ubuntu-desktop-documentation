(advanced-disk-setup-features)=
# Advanced disk setup features

When installing Ubuntu, the installer offers several disk setup options. The following advanced features are available:

None
: Use regular disk partitioning with no extra features.

Use LVM
: Logical Volume Management (LVM) makes it easier to create and manage partitions after the installation.

Use LVM and encryption
: Add a disk encryption layer to LVM. This is the recommended option to encrypt your data.

Erase disk and use ZFS
: This advanced file system allows you to create pooled storage volumes that span multiple drives. It supports snapshots and data repair features. It is a powerful option for advanced users.

Erase disk and use ZFS with encryption
: Use ZFS and enable its data encryption feature.

Enable hardware-backed full disk encryption
: TPM-backed full disk encryption (FDE) is a new, **experimental** disk encryption feature of Ubuntu Desktop. For details, see {ref}`hardware-backed-disk-encryption`.

