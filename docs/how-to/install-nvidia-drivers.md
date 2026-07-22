---
myst:
  html_meta:
    description: Install NVIDIA drivers on Ubuntu using the ubuntu-drivers tool for UDA desktop drivers or ERD server drivers with Fabric Manager.

relatedlinks: "https://docs.nvidia.com/datacenter/tesla/fabric-manager-user-guide/index.html, https://www.nvidia.com/en-us/data-center/nvlink/, https://docs.nvidia.com/ai-enterprise/release-8/latest/infra-software/vgpu/features/nvswitch.html"
---

```{tags} How-to guide
```

(install-nvidia-drivers)=
# Install NVIDIA drivers

If you have an NVIDIA GPU, you can install official NVIDIA drivers to improve desktop and gaming performance or support computing tasks.

:::{warning}
NVIDIA drivers installed from sources outside of those listed in this guide might potentially overwrite those provided by `ubuntu-drivers` and might break Secure Boot.
:::


## The `ubuntu-drivers` tool

The `ubuntu-drivers` tool relies on the same logic as the "Additional Drivers" graphical tool, and allows more flexibility on desktops and on servers.

The `ubuntu-drivers` tool is recommended if your computer uses Secure Boot, since it will, by default, only install the pre-built, signed drivers which are known to work with Secure Boot. (Refer to "Building your own kernel modules using the NVIDIA DKMS package" later in this page if you have a specific use case that requires the DKMS drivers.)

:::{note}
If you currently have a version of the NVIDIA drivers installed that conflicts with those being installed by `ubuntu-drivers`, `ubuntu-drivers` will uninstall your original drivers before installing the new drivers.
:::


## Check driver versions

To check the version of your currently running driver:

```{terminal}
:copy:
:user:
:host:
:dir:
cat /proc/driver/nvidia/version
```

## Ensure your system and kernel is up-to-date

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt update && sudo apt upgrade
```

After the update is complete, reboot your system.


## Install the drivers for generic use (e.g. desktop and gaming)

For the generic desktop use, we package the **Unified Driver Architecture (UDA)** drivers. You can also find them [on the NVIDIA website](https://www.nvidia.com/en-us/drivers/unix/).

Check the available drivers for your hardware:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo ubuntu-drivers list
```

You can either rely on automatic detection, which will install the driver that is considered the best match for your hardware:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo ubuntu-drivers install
```

Or you can tell the `ubuntu-drivers` tool which driver you would like installed. If this is the case, you will have to use the driver version (such as `535`) that you saw when you used the `ubuntu-drivers list` command.

Let's assume we want to install the `535` driver:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo ubuntu-drivers install nvidia:535
```

## Install the drivers on servers and/or for computing purposes

For servers and computing tasks, Ubuntu provides the **Enterprise Ready Drivers ({term}`ERD`)** drivers. Their packages can be recognized by the `-server` suffix. You can read more about these drivers [in the NVIDIA documentation](https://docs.nvidia.com/datacenter/tesla/index.html).

Additionally, Ubuntu provides the **NVIDIA Fabric Manager** and the **NVIDIA Switch Configuration and Query (NSCQ) Library**, which you will only need if you have NVswitch hardware. The Fabric Manager and NSCQ library are only available with the ERDs or `-server` driver versions.

Check the available drivers for your hardware:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo ubuntu-drivers list --gpgpu

nvidia-driver-470
nvidia-driver-470-server
nvidia-driver-535
nvidia-driver-535-open
nvidia-driver-535-server
nvidia-driver-535-server-open
nvidia-driver-550
nvidia-driver-550-open
nvidia-driver-550-server
nvidia-driver-550-server-open
```

You can either rely on automatic detection, which will install the driver that is considered the best match for your hardware:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo ubuntu-drivers install --gpgpu
```

Or you can tell the `ubuntu-drivers` tool which driver you would like installed. If this is the case, you will have to use the driver version (such as `535`) and the `-server` suffix that you saw when you used the `ubuntu-drivers list --gpgpu` command.

Let's assume we want to install the `535-server` driver (listed as `nvidia-driver-535-server`):

```{terminal}
:copy:
:user:
:host:
:dir:
sudo ubuntu-drivers install --gpgpu nvidia:535-server
```

You will also want to install the following additional components:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install nvidia-utils-535-server
```

### (Optional) Install Fabric Manager and the NSCQ library

If your system comes with NVswitch hardware, then you will want to install Fabric Manager and the NVSwitch Configuration and Query library. You can do so by running the following:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install nvidia-fabricmanager-535 libnvidia-nscq-535
```

:::{note}
While `nvidia-fabricmanager` and `libnvidia-nscq` do not have the same `-server` label in their name, they are really meant to match the `-server` drivers in the Ubuntu archive. For example, `nvidia-fabricmanager-535` will match the `nvidia-driver-535-server` package version (not the `nvidia-driver-535 package`).
:::


## Transitional packages to new driver branches

When NVIDIA stops support on a driver branch, then Canonical will transition you to the next supported driver branch automatically if you try to install that driver branch.

See NVIDIA's [current support matrix](https://docs.nvidia.com/datacenter/tesla/drivers/index.html) in their documentation.

## Troubleshooting

### Driver/library version mismatch error

If you encounter the following error when running the [nvidia-smi](https://developer.nvidia.com/system-management-interface) command:

```{terminal}
:output-only:
Failed to initialize NVML: Driver/library version mismatch
```

This typically indicates that the userspace driver packages were upgraded while the kernel module is still on the older version (for example, the client reports one driver version while the kernel module reports another). This situation often occurs after a system upgrade. To verify this, check the kernel logs:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo dmesg
```

Look for error messages similar to:

```{terminal}
:output-only:
NVRM: API mismatch: the client has the version 570.172.08, but
NVRM: this kernel module has the version 570.158.01.  Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.
```

**Solution**: Rebooting the system will load the updated kernel module and bring the versions back in sync.

### No devices were found error

If you encounter the following error when running the [nvidia-smi](https://developer.nvidia.com/system-management-interface) command:

```{terminal}
:output-only:
No devices were found
```

This may occur if the open-source NVIDIA kernel driver [`nouveau`](https://nouveau.freedesktop.org/) is pre-installed and loaded, which conflicts with the proprietary NVIDIA driver. To check whether `nouveau` is loaded:

```{terminal}
:copy:
:user:
:host:
:dir:
lsmod | grep nouveau
```

**Solution**: If `nouveau` kernel module is loaded, blocklist it and rebuild the `initramfs`:

```{terminal}
:copy:
:user:
:host:
:dir:
echo "blacklist nouveau" | sudo tee /etc/modprobe.d/disable-nouveau.conf
echo "options nouveau modeset=0" | sudo tee -a /etc/modprobe.d/disable-nouveau.conf
sudo rmmod nouveau || true
sudo update-initramfs -u
```

Then reboot the system for the changes to take effect.
