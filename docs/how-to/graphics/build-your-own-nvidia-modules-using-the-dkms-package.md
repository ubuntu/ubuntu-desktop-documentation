---
myst:
  html_meta:
    description: Install NVIDIA drivers on Ubuntu Desktop or Server using the Dynamic Kernel Module Support (DKMS) packages when you're using a custom kernel or when the standard NVIDIA packages are missing or lagging in release.

relatedlinks: "https://docs.nvidia.com/datacenter/tesla/drivers/driver-lifecycle.html, https://docs.nvidia.com/datacenter/tesla/fabric-manager-user-guide/index.html, https://www.nvidia.com/en-us/data-center/nvlink/, https://docs.nvidia.com/ai-enterprise/release-8/latest/infra-software/vgpu/features/nvswitch.html"
---

```{tags} How-to guide, Graphics
```

(build-your-own-nvidia-modules-using-the-dkms-package)=
# Build your own NVIDIA modules using the DKMS package

By using the Dynamic Kernel Module Support ({term}`DKMS`) driver package, you can build the NVIDIA driver for the exact kernel that you're running. This is useful when you're using a custom kernel or when the standard NVIDIA packages are missing or lagging in release.

:::{warning}
We don't recommend using the DKMS modules unless you are running a custom kernel for which the prebuilt drivers are not supported. This is because the DKMS drivers are not signed with Canonical's key and thus do not support Secure Boot.

For most Ubuntu users, we recommend following the more automated {ref}`install-nvidia-drivers` guide instead.
:::


## Types of NVIDIA drivers

We package two types of NVIDIA drivers:

Unified Driver Architecture (UDA) drivers
: These are recommended for the generic desktop use and gaming. They also support computing use cases such as AI and machine learning. You can also find them [on the NVIDIA website](https://www.nvidia.com/en-us/drivers/unix/).

Enterprise Ready Drivers ({term}`ERD`)
: These are recommended on servers and for computing tasks. These drivers come from an NVIDIA release branch that's qualified and supported for longer on data center GPUs. They omit certain desktop-oriented features. Their packages can be recognized by the `-server` suffix. You can read more about these drivers [in the NVIDIA documentation](https://docs.nvidia.com/datacenter/tesla/index.html).

Additionally, Ubuntu provides the **NVIDIA Fabric Manager** and the **NVSwitch Configuration and Query (NSCQ) library**, which you will only need if you have NVSwitch hardware. The Fabric Manager and NSCQ library are only available with the ERDs or `-server` driver versions.


## Install the kernel modules

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

1. After installing the correct kernel modules, install the correct driver metapackage:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install nvidia-driver-${DRIVER_BRANCH}${SERVER}
    ```

1. If your system comes with NVSwitch hardware, install Fabric Manager and the NVSwitch Configuration and Query library:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install nvidia-fabricmanager-${DRIVER_BRANCH} libnvidia-nscq-${DRIVER_BRANCH}
    ```


## Switch between pre-compiled and DKMS modules

You can switch from the pre-compiled NVIDIA drivers to the DKMS modules or the other way around.

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

1. Install new drivers:

    - To install the pre-compiled drivers, refer to {ref}`install-nvidia-drivers`.
    - To install the DKMS modules, go back to {ref}`build-your-own-nvidia-modules-using-the-dkms-package`.
