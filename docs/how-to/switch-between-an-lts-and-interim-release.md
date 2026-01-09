```{tags} Updates, Support
```

(switch-between-an-lts-and-interim-release)=
# Switch between an LTS and interim release

Ubuntu releases come in two types with different life cycles: Long Term Support (LTS) releases and interim releases. You can reconfigure your system from one type to another.

## The difference between release types

LTS releases such as Ubuntu 24.04 LTS are recommended for users looking for a stable environment. LTS releases receive five years of support and security updates.

Interim releases are supported for nine months. They give you a chance to preview new features and updates ahead of the next LTS release.

To learn more about the life cycle of Ubuntu releases, see [The Ubuntu lifecycle and release cadence](https://ubuntu.com/about/release-cycle).

## Determine your current release

Before you start upgrading, you need to know which version of Ubuntu you're currently using and whether it's an LTS or interim release.

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
On Ubuntu Desktop, open the Settings application. Navigate to {menuselection}`System --> About`. Your Ubuntu version is listed in the {guilabel}`Operating System` field. For example, it might say "Ubuntu 24.04.3 LTS".

On earlier Ubuntu versions, the information was located on the Details tab.
:::

:::{tab-item} Command line
:sync: terminal

```{terminal}
:copy:
:user:
:host:
:dir:
lsb_release --description
    
No LSB modules are available.
Description:	Ubuntu 24.04.3 LTS
```
:::
::::


(switch-to-interim)=
## Switch to interim

If you're currently using an LTS release such as Ubuntu 24.04 LTS, you can configure your system to follow interim releases instead.

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Software & Updates application.

1. Go to the {guilabel}`Updates` tab.

1. In the menu labeled {guilabel}`Notify me of a new Ubuntu version`, select {guilabel}`For any new version`, which includes interim releases.

1. Close the application.
:::

:::{tab-item} Command line
:sync: terminal

1. Edit the `/etc/update-manager/release-upgrades` configuration file.
1. Set the `Prompt=normal` option.
:::
::::

An upgrade to an interim release becomes available now, unless you're using an LTS release that's just come out and there's no recent interim release yet. Follow the instructions in the {ref}`Upgrade Ubuntu Desktop <upgrade-ubuntu-desktop>` guide. You might have to upgrade several times until you reach the latest interim release.


(switch-to-lts)=
## Switch to LTS

If you're using an interim release of Ubuntu, you can reconfigure your system to be an LTS release. However, you can only do this at certain points in time:

* When you're using an interim release that directly precedes an LTS release, such as on Ubuntu 25.10 before Ubuntu 26.04 LTS.
* When you upgrade to an Ubuntu release that's an LTS release, such as after your upgrade to Ubuntu 26.04 LTS.

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Software & Updates application.

1. Go to the {guilabel}`Updates` tab.

1. In the menu labeled {guilabel}`Notify me of a new Ubuntu version`, select {guilabel}`For long-term support versions`.

1. Close the application.
:::

:::{tab-item} Command line
:sync: terminal

1. Edit the `/etc/update-manager/release-upgrades` configuration file.
1. Set the `Prompt=lts` option.
:::
::::

Your installation now stops offering upgrades to new interim releases, and instead, it stabilizes on the current or upcoming LTS release. When a new LTS release becomes available, follow the instructions in the {ref}`Upgrade Ubuntu Desktop <upgrade-ubuntu-desktop>` guide to upgrade your system.
