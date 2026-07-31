---
myst:
  html_meta:
    description: Install NVIDIA drivers on Ubuntu using the ubuntu-drivers tool for UDA desktop drivers or ERD server drivers with Fabric Manager.

relatedlinks: "https://docs.nvidia.com/datacenter/tesla/fabric-manager-user-guide/index.html, https://www.nvidia.com/en-us/data-center/nvlink/, https://docs.nvidia.com/ai-enterprise/release-8/latest/infra-software/vgpu/features/nvswitch.html"
---

```{tags} How-to guide, Graphics
```

(nvidia-driver-packages)=
# Select NVIDIA driver packages manually

If you have an NVIDIA GPU, you can install official NVIDIA drivers as deb packages using the APT tool. This is useful in several cases:

- You're provisioning Ubuntu on multiple machines and you want to ensure the same driver configuration on all of them.
- You're running a custom kernel, so you need the DKMS driver.
- The NVIDIA driver for your kernel version isn't available yet, so you need the DKMS driver.
- You want to learn how the drivers work on a lower level.

For most Ubuntu users, we recommend following the more automated {ref}`install-nvidia-drivers` guide instead.

:::{warning}
NVIDIA drivers installed from sources outside of those listed in this guide might potentially overwrite those provided by `ubuntu-drivers` and might break Secure Boot.
:::

## Types of NVIDIA drivers

We package two types of NVIDIA drivers:

Unified Driver Architecture (UDA) drivers
: These are recommended for the generic desktop use and gaming. They also support computing use cases such as AI and machine learning. You can also find them [on the NVIDIA website](https://www.nvidia.com/en-us/drivers/unix/).

Enterprise Ready Drivers ({term}`ERD`)
: These are recommended on servers and for computing tasks. These drivers come from an NVIDIA release branch that's qualified and supported for longer on data center GPUs. They omit certain desktop-oriented features. Their packages can be recognized by the `-server` suffix. You can read more about these drivers [in the NVIDIA documentation](https://docs.nvidia.com/datacenter/tesla/index.html).

Additionally, Ubuntu provides the **NVIDIA Fabric Manager** and the **NVIDIA Switch Configuration and Query (NSCQ) Library**, which you will only need if you have NVswitch hardware. The Fabric Manager and NSCQ library are only available with the ERDs or `-server` driver versions.

## Check driver versions

To check the version of your currently running driver:

```{terminal}
:copy:
:user:
:host:
:dir:
cat /proc/driver/nvidia/version
```

## Install the kernel modules

If your system uses Secure Boot (as most modern Intel and AMD systems do), your kernel will require the kernel modules to be signed. There are two mutually exclusive ways to achieve this:

- {ref}`install-the-pre-compiled-nvidia-modules-for-your-kernel`
- {ref}`build-your-own-kernel-modules-using-the-nvidia-dkms-package`

(install-the-pre-compiled-nvidia-modules-for-your-kernel)=
### Install the pre-compiled NVIDIA modules for your kernel

1. Install the metapackage for your kernel flavor (e.g. `generic`, `lowlatency`, etc.), which is specific to the driver branch (e.g. `535`) that you want to install, and whether you want the compute vs. general display driver (e.g. `-server` or not):

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-${DRIVER_BRANCH}${SERVER}-${LINUX_FLAVOUR}
    ```
    
    For example, install `linux-modules-nvidia-535-generic`.

1. Check that the modules for your specific kernel/{term}`ABI` were installed by the metapackage:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt-cache policy linux-modules-nvidia-${DRIVER_BRANCH}${SERVER}-$(uname -r)
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
    sudo apt install linux-modules-nvidia-${DRIVER_BRANCH}${SERVER}-$(uname -r)
    ```
    
    For example:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-modules-nvidia-535-$(uname -r)
    ```

(build-your-own-kernel-modules-using-the-nvidia-dkms-package)=
### Build your own kernel modules using the NVIDIA DKMS package

By using the {term}`DKMS` driver package, you can build the NVIDIA driver for the exact kernel that you're running. This is useful when you're using a custom kernel or when the standard NVIDIA packages are missing or lagging in release.

:::{warning}
We don't recommend using the DKMS modules unless you are running a custom kernel for which the prebuilt drivers are not supported. This is because the DKMS drivers are not signed with Canonical's key and thus do not support Secure Boot.
:::

The general procedure is to install the relevant NVIDIA DKMS package and `linux-headers` to build the kernel modules, and enroll your own key to sign the modules.

1. Install the `linux-headers` metapackage for your kernel flavor (e.g. `generic`, `lowlatency`, etc.):

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-headers-${LINUX_FLAVOUR}
    ```

1. Check that the headers for your specific kernel were installed by the metapackage:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt-cache policy linux-headers-$(uname -r)
    ```

1. If the headers for your current running kernel were not installed, install them by specifying the running kernel version:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install linux-headers-$(uname -r)
    ```

1. Install the NVIDIA DKMS package for your desired driver series:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install nvidia-dkms-${DRIVER_BRANCH}${SERVER}
    ```
    
    This may automatically guide you through creating and enrolling a new key for Secure Boot.

    Alternatively, you can use `ubuntu-drivers` to automatically select an appropriate DKMS driver branch:
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ubuntu-drivers install --include-dkms
    ```

## Install the user-space drivers and the driver libraries

After installing the correct kernel modules (see the relevant section of this document), install the correct driver metapackage:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install nvidia-driver-${DRIVER_BRANCH}${SERVER}
```

### (Optional) Install Fabric Manager and the NSCQ library

If your system comes with NVswitch hardware, then you will want to install Fabric Manager and the NVSwitch Configuration and Query library. You can do so by running the following:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install nvidia-fabricmanager-${DRIVER_BRANCH} libnvidia-nscq-${DRIVER_BRANCH}
```

:::{note}
While `nvidia-fabricmanager` and `libnvidia-nscq` do not have the same `-server` label in their name, they are really meant to match the `-server` drivers in the Ubuntu archive. For example, `nvidia-fabricmanager-535` matches the `nvidia-driver-535-server` package version (not the `nvidia-driver-535 package`).
:::


## Switch between pre-compiled and DKMS modules

1. Remove all existing NVIDIA packages from your system:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt --purge remove '*nvidia*${DRIVER_BRANCH}*'
    ```
    
    If you are unsure which `${DRIVER_BRANCH}` to pick for removal, you might look at the installed nvidia packages and see the different `${DRIVER_BRANCH}` numbers that are present on your system.

    Since `autoremove` will take care of all indirect dependencies, it is sufficient to list those that have been directly installed by using `apt-mark`.
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    apt-mark showmanual | grep nvidia
    ```

1. Remove any additional packages that may have been installed as a dependency (e.g. the `i386` libraries on `amd64` systems) and which were not caught by the previous command:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt autoremove
    ```

1. Install new drivers by following the earlier sections of this guide: {ref}`nvidia-driver-packages`.
