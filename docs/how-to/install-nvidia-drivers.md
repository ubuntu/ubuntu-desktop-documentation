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
NVIDIA drivers installed from sources outside of those listed in this guide might potentially overwrite those provided by Ubuntu and might break Secure Boot.
:::


## Driver management tools

We recommend using the `ubuntu-drivers` tool or the Additional Drivers app to manage drivers. They share the same logic. By default, these tools only install the pre-built, signed drivers, which are known to work with **Secure Boot**.

Refer to {ref}`building-your-own-kernel-modules-using-thenvidia-dkms-package` if you have a specific use case that requires the DKMS drivers.


## Check driver versions

To check the version of your currently running driver:

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Additional Drivers app.

    If you can't find the app on your system, you can install it from the `software-properties-gtk` package.

1. See which driver is selected under "NVIDIA Corporation".

    *Nouveau* is usually pre-selected as the default, open-source driver.
:::
:::{tab-item} Command line
:sync: terminal

```{terminal}
:copy:
:user:
:host:
:dir:
cat /proc/driver/nvidia/version
```
:::
::::

If you currently have a version of the NVIDIA drivers installed that conflicts with those being installed, `ubuntu-drivers` will uninstall your original drivers before installing the new drivers.


## Update your system and kernel

1. Apply all updates.

    ::::{tab-set}
    :::{tab-item} Graphical interface
    :sync: gui
    Open the Software Updater app and install all available updates.
    :::
    
    :::{tab-item} Command line
    :sync: terminal
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt update && sudo apt upgrade
    ```
    :::
    ::::

2. After the update is complete, reboot your system.


## Install the drivers for desktop and gaming use

For the generic desktop use, we package the **Unified Driver Architecture (UDA)** drivers. You can also find them [on the NVIDIA website](https://www.nvidia.com/en-us/drivers/unix/).

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Additional Drivers app.

    If you can't find the app on your system, you can install it from the `software-properties-gtk` package.

1. Under "NVIDIA Corporation", choose your preferred driver version.

    We recommend the most recent NVIDIA driver with the {guilabel}`proprietary, tested` label.

1. Click {guilabel}`Apply changes` and enter your password.

1. When the installation is complete, restart your system for the changes to take effect.
:::
:::{tab-item} Command line
:sync: terminal
1. Check the available drivers for your hardware:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ubuntu-drivers list
    ```

1. Install the drivers.

    You can rely on automatic detection, which will install the driver that is considered the best match for your hardware:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ubuntu-drivers install
    ```

    Alternatively, you can specify which driver you want. You have to type the driver version (such as `535`) that you saw when you used the `ubuntu-drivers list` command.

    Let's assume we want to install the `535` driver:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ubuntu-drivers install nvidia:535
    ```

1. When the installation is complete, restart your system for the changes to take effect.
:::
::::


## Install the drivers on servers or for computing purposes

For servers and computing tasks, Ubuntu provides the **Enterprise Ready Drivers ({term}`ERD`)** drivers. Their packages can be recognized by the `-server` suffix. You can read more about these drivers [in the NVIDIA documentation](https://docs.nvidia.com/datacenter/tesla/index.html).

Additionally, Ubuntu provides the **NVIDIA Fabric Manager** and the **NVIDIA Switch Configuration and Query (NSCQ) Library**, which you will only need if you have NVswitch hardware. The Fabric Manager and NSCQ library are only available with the ERDs or `-server` driver versions.

1. Check the available drivers for your hardware:

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

1. Install the driver.

    You can rely on automatic detection, which installs the driver that is considered the best match for your hardware:
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ubuntu-drivers install --gpgpu
    ```
    
    Alternatively, you can specify which driver you want. You have to type the driver version (such as `535`) and the `-server` suffix that you saw when you used the `ubuntu-drivers list --gpgpu` command.

    Let's assume we want to install the `535-server` driver (listed as `nvidia-driver-535-server`):
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ubuntu-drivers install --gpgpu nvidia:535-server
    ```

1. You will also want to install the following additional components:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install nvidia-utils-535-server
    ```

    Replace `535` with your selected driver version.

    **TODO:** Are these components useful on Desktop, too? The package seems to contain these files:
    - /usr/bin/nvidia-bug-report.sh
    - /usr/bin/nvidia-debugdump
    - /usr/bin/nvidia-smi
    - /usr/bin/nvidia-xconfig

1. (Optional) Install Fabric Manager and the NSCQ library.

    If your system comes with NVswitch hardware, then you will want to install Fabric Manager and the NVSwitch Configuration and Query library:
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install nvidia-fabricmanager-535 libnvidia-nscq-535
    ```
    
    Replace `535` with your selected driver version.
    
    :::{note}
    While `nvidia-fabricmanager` and `libnvidia-nscq` do not have the same `-server` label in their name, they are really meant to match the `-server` drivers in the Ubuntu archive. For example, `nvidia-fabricmanager-535` matches the `nvidia-driver-535-server` package version (not the `nvidia-driver-535 package`).
    :::

1. When the installation is complete, restart your system for the changes to take effect.


## Transitional packages to new driver branches

When NVIDIA stops support on a driver branch, Ubuntu will transition you to the next supported driver branch automatically if you try to install that driver branch.

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
