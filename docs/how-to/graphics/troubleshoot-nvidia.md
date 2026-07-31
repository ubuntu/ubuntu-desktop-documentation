```{tags} How-to guide, Graphics
```

(troubleshoot-your-nvidia-gpu-and-drivers)=
# Troubleshoot your NVIDIA GPU and drivers

You can monitor the state of your NVIDIA GPU and resolve common issues.

This guide assumes that you're using the proprietary NVIDIA drivers. Refer to {ref}`install-nvidia-drivers` first.

## Install NVIDIA monitoring and troubleshooting tools

The following tools are available:

`nvidia-bug-report.sh`
: Collects diagnostic information into a compressed report, useful when filing bug reports with NVIDIA.

`nvidia-debugdump`
: Extracts internal GPU debug data, mainly used by NVIDIA support for low-level driver debugging.

`nvidia-smi`
: Monitors your GPU utilization, memory usage, fan speed and clock speed.

  For details, refer to [System Management Interface SMI](https://developer.nvidia.com/system-management-interface).

`nvidia-xconfig`
: Generates the X11 server configuration (`xorg.conf`) for NVIDIA driver settings. Only for legacy Desktop systems.

Install the tools from the package matching your driver version. For example, on a Server system using the driver version 535:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install nvidia-utils-535-server
```


## Driver/library version mismatch error

If you encounter the following error when running the `nvidia-smi` command:

```{terminal}
:output-only:
Failed to initialize NVML: Driver/library version mismatch
```

This typically indicates that the user-space driver packages were upgraded while the kernel module is still on the older version (for example, the client reports one driver version while the kernel module reports another). This situation often occurs after a system upgrade. To verify this, check the kernel logs:

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


## No devices were found error

If you encounter the following error when running the `nvidia-smi` command:

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
