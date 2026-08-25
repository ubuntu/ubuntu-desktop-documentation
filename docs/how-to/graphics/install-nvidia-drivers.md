---
myst:
  html_meta:
    description: Install NVIDIA drivers on Ubuntu using the ubuntu-drivers tool for UDA desktop drivers or ERD server drivers with Fabric Manager.

relatedlinks: "https://docs.nvidia.com/datacenter/tesla/fabric-manager-user-guide/index.html, https://www.nvidia.com/en-us/data-center/nvlink/, https://docs.nvidia.com/ai-enterprise/release-8/latest/infra-software/vgpu/features/nvswitch.html"
---

```{tags} How-to guide, Graphics
```

(install-nvidia-drivers)=
# Install NVIDIA drivers

If you have an NVIDIA GPU, you can install official NVIDIA drivers to improve desktop and gaming performance or support computing tasks.

:::{warning}
NVIDIA drivers installed from sources outside of those listed in this guide might potentially overwrite those provided by Ubuntu and might break Secure Boot.

We recommend installing the drivers provided by Ubuntu packages rather than downloading drivers from NVIDIA. The Ubuntu packages ensure that you install libraries compatible with your Ubuntu release.
:::


## Driver management tools

We recommend using the `ubuntu-drivers` tool or the Additional Drivers app to manage drivers. They share the same logic. By default, these tools only install the pre-built, signed drivers, which are known to work with **Secure Boot**.

You can also install NVIDIA drivers as deb packages using the APT tool. This is useful in certain cases:

- You're provisioning Ubuntu on multiple machines and you want to ensure the same driver configuration on all of them.
- You want to learn how the drivers work on a lower level.

In some scenarios, you have to {ref}`install the DKMS driver package <build-your-own-nvidia-modules-using-the-dkms-package>`, which builds the NVIDIA driver for the exact kernel that you're running. For example:

- You're running a custom kernel.
- The NVIDIA driver for your kernel version isn't available yet.


## Driver versions and branches

NVIDIA drivers come with several different support life cycles, also known as branches.

* Generally, we recommend that you install the **Production Branch** (PB) drivers. These drivers are supported for one year and provide a good balance of performance, latest features and stability.
* If you need the latest driver, such as to support a newly released game or the latest CUDA APIs, you can opt for the **New Feature Branch** (NFB) drivers.
* In a regulated enterprise environment, you might prefer the **Long Term Support Branch** (LTSB) drivers, which are supported for three years.

### Check your driver version

To check the version of your currently running driver:

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Additional Drivers app.

    If you can't find the app on your system, you can install it from the `software-properties-gtk` package.

1. See which driver is selected under "NVIDIA Corporation".

    [*Nouveau*](https://nouveau.freedesktop.org/) is usually pre-selected as the default, open-source driver.
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

### Check a driver's support branch

You can use the following command to check which branch a driver belongs to:

```{terminal}
:copy:
:user:
:host:
:dir:

apt show nvidia-driver-VERSION | grep ^Support
```

The output shows the acronym of the branch. For example:

```{terminal}
:copy:
:user:
:host:
:dir:

apt show nvidia-driver-595 | grep ^Support

Support: PB
```

### Transitional packages to new driver branches

When NVIDIA stops support on a driver branch, Ubuntu will transition you to the next supported driver branch automatically if you try to install that driver branch.

See NVIDIA's [current support matrix](https://docs.nvidia.com/datacenter/tesla/drivers/index.html) in their documentation.


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

For the generic desktop use and gaming, we package the **Unified Driver Architecture (UDA)** drivers. These drivers also support computing use cases such as AI and machine learning. You can also find them [on the NVIDIA website](https://www.nvidia.com/en-us/drivers/unix/).

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Additional Drivers app.

    If you can't find the app on your system, you can install it from the `software-properties-gtk` package.

1. Under "NVIDIA Corporation", choose your preferred driver version.

    We recommend the most recent NVIDIA driver with the "proprietary, tested" label. Avoid the "Server" drivers.

    For example, you might select {guilabel}`Using NVIDIA driver (open kernel) metapackage from nvidia-driver-525 (proprietary, tested)`.

    :::{note}
    The "open kernel" driver is a new, open-source implementation of the NVIDIA kernel driver for recent GPUs. It depends on proprietary GPU firmware and proprietary user-space libraries.
    :::

1. Click {guilabel}`Apply changes` and enter your password.

1. When the installation is complete, restart your system for the changes to take effect.
:::

:::{tab-item} Using `ubuntu-drivers`
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
:::

:::{tab-item} Selecting packages manually
:sync: nvidia-drivers-manual
1. Install the metapackage for your kernel flavor (e.g. `generic`, `lowlatency`, etc.), which is specific to the driver branch (e.g. `535`) that you want to install:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-${DRIVER_BRANCH}-${LINUX_FLAVOUR}
    ```
    
    For example, install `linux-modules-nvidia-535-generic`.

1. Check that the modules for your specific kernel/{term}`ABI` were installed by the metapackage:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt-cache policy linux-modules-nvidia-${DRIVER_BRANCH}-$(uname -r)
    ```
    
    For example:
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt-cache policy linux-modules-nvidia-535-$(uname -r)
    ```

1. If the modules were not installed for your current running kernel, upgrade to the latest kernel or install them by specifying the running kernel version:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-${DRIVER_BRANCH}-$(uname -r)
    ```
    
    For example:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-535-$(uname -r)
    ```
:::
::::

When the installation is complete, restart your system for the changes to take effect.

<!--
This section is disabled for the Ubuntu Desktop guide.
It'll be re-enabled in the unified Desktop+Server documentation for Ubuntu OS.

## Install the drivers on servers or for computing purposes

For servers and computing tasks, Ubuntu provides the **Enterprise Ready Drivers ({term}`ERD`)** drivers. These drivers come from an NVIDIA release branch that's qualified and supported for longer on data center GPUs. They omit certain desktop-oriented features. Their packages can be recognized by the `-server` suffix. You can read more about these drivers [in the NVIDIA documentation](https://docs.nvidia.com/datacenter/tesla/index.html).

Additionally, Ubuntu provides the **NVIDIA Fabric Manager** and the **NVIDIA Switch Configuration and Query (NSCQ) Library**, which you will only need if you have NVswitch hardware. The Fabric Manager and NSCQ library are only available with the ERDs or `-server` driver versions.

::::{tab-set}
:::{tab-item} Using `ubuntu-drivers`
:sync: terminal
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
:::

:::{tab-item} Selecting packages manually
:sync: nvidia-drivers-manual
1. Install the metapackage for your kernel flavor (e.g. `generic`, `lowlatency`, etc.), which is specific to the driver branch (e.g. `535`) that you want to install:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-${DRIVER_BRANCH}-server-${LINUX_FLAVOUR}
    ```
    
    For example, install `linux-modules-nvidia-535-server-generic`.

1. Check that the modules for your specific kernel/{term}`ABI` were installed by the metapackage:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt-cache policy linux-modules-nvidia-${DRIVER_BRANCH}-server-$(uname -r)
    ```
    
    For example:
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt-cache policy linux-modules-nvidia-535-server-$(uname -r)
    ```

1. If the modules were not installed for your current running kernel, upgrade to the latest kernel or install them by specifying the running kernel version:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-${DRIVER_BRANCH}-server-$(uname -r)
    ```
    
    For example:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-535-server-$(uname -r)
    ```
:::
::::

::::{dropdown} (Optional) Install Fabric Manager and the NSCQ library
If your system comes with NVSwitch hardware, then you will want to install Fabric Manager and the NVSwitch Configuration and Query library:
    
```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install nvidia-fabricmanager-535 libnvidia-nscq-535
```

Replace `535` with your selected driver version.

:::{note}
While `nvidia-fabricmanager` and `libnvidia-nscq` do not have the same `-server` label in their name, they are really meant to match the `-server` drivers in the Ubuntu archive. For example, `nvidia-fabricmanager-535` matches the `nvidia-driver-535-server` package version (not the `nvidia-driver-535` package).
:::
::::

When the installation is complete, restart your system for the changes to take effect.
-->


## Troubleshooting

- {ref}`build-your-own-nvidia-modules-using-the-dkms-package`
- {ref}`troubleshoot-your-nvidia-gpu-and-drivers`
