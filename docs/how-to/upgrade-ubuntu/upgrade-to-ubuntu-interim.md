---
relatedlinks: "[QuestingUpgrades/Kubuntu](https://help.ubuntu.com/community/QuestingUpgrades/Kubuntu), [Upgrading &#32 Lubuntu](https://manual.lubuntu.me/stable/D/upgrading.html), [Upgrading &#32 to &#32 Ubuntu &#32 Studio &#32; 25.10](https://discourse.ubuntu.com/t/ubuntu-studio-25-10-release-notes/53099#p-132280-upgrading-to-ubuntu-studio-2504-5), [Upgrading &#32; to &#32; Xubuntu &#32; 25.10](https://wiki.xubuntu.org/releases/25.10/upgrading), [UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)"
---

(upgrade-to-ubuntu-interim)=
# Upgrade to Ubuntu 25.10

Ubuntu 25.10 ("Questing Quokka") is the latest *interim* release of Ubuntu. Interim releases are supported for nine months. They give you a chance to preview new features and updates ahead of the next Long Term Support (LTS) release.

Long Term Supported releases such as Ubuntu 24.04 LTS are recommended for users looking for a stable environment.

To learn more about the life cycle of Ubuntu releases, see [The Ubuntu lifecycle and release cadence](https://ubuntu.com/about/release-cycle).

Users on interim releases are prompted to upgrade a few days after the next release becomes available. This prompt might happen automatically, or when checking for new updates.


## Check the release notes

We recommended that you read the [release notes for Ubuntu 25.10](https://discourse.ubuntu.com/t/questing-quokka-release-notes/59220), which describe new features, caveats and workarounds for known issues in this version.


## Back up your data

Back up all of your user data to an external storage device. Although it's unlikely that data will be lost during the upgrade process, it's better to be safe than sorry.


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
:input: lsb_release --description
    
No LSB modules are available.
Description:	Ubuntu 24.04.3 LTS
```
:::
::::

You can upgrade to Ubuntu 25.10 from the previous Ubuntu 25.04 interim release, or from the Ubuntu 24.04 LTS release.

If you're running an older Ubuntu release, you must gradually upgrade to Ubuntu 24.04 LTS or 25.04 first before proceeding to Ubuntu 25.10.


(switch-to-interim)=
## Switch to interim

If you're currently using an LTS release such as Ubuntu 24.04 LTS, configure your system to follow interim releases instead.

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui
1. Open the Software & Updates application.

    ![|187x184](https://assets.ubuntu.com/v1/89f374af-tutorial11.png)

1. Go to the {guilabel}`Updates` tab.

1. In the menu labeled {guilabel}`Notify me of a new Ubuntu version`, select {guilabel}`For any new version`, which includes interim releases.

    ![|624x309](https://assets.ubuntu.com/v1/69830192-tutorial12.png)

1. Close the application.
:::

:::{tab-item} Command line
:sync: terminal

1. Edit the `/etc/update-manager/release-upgrades` configuration file.
1. Set the `Prompt=normal` option.
:::
::::

## Apply all updates

Before you start the upgrade, make sure that your current Ubuntu installation is fully updated:

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui

1. Open the Software Updater application.
1. If any updates are available, install them.
1. Restart your computer if prompted.
:::

:::{tab-item} Command line
:sync: terminal

1. Refresh package information:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo apt update
    ```

1. Install updates:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo apt upgrade
    ```

1. Restart your computer if prompted:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: systemctl reboot
    ```
:::
::::

## Start the upgrade

Launch the application that upgrades your system:

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui

1. Open the Software Updater application.

1. The application informs you that a new release is available.

    Click {guilabel}`Upgrade`.
:::

:::{tab-item} Command line
:sync: terminal

```{terminal}
:copy:
:user:
:host:
:dir:
:input: sudo do-release-upgrade
```
:::
::::

If no upgrade is available, you're either on the latest version of Ubuntu or upgrades to the newest release haven't been enabled yet.

Follow the application's instructions and confirm the prompts:

1. The application presents an overview of the upgrade.

1. When all upgrade requirements have been gathered, the application shows an overview of the packages to be installed and removed.

1. While the upgrade is in progress, you might see visual glitches on your screen, such as changing icons. This is normal. Wait until the process is complete.

1. When new packages have been installed, the application prompts you to remove the obsolete packages from the previous Ubuntu release.

    Unless you have a reason to keep the packages, it's best to remove them. This usually takes a minute or two.

1. When the upgrade is complete, restart your computer.


## Troubleshooting

You might encounter these problems when trying to upgrade Ubuntu.

### Upgrade isn't available

The upgrade to the latest interim release only becomes available several days after the official release date. This is to allow time for any critical bugs to be fixed before prompting all users to upgrade. Check again in a few days.

If it's been more than a couple of days, look for known issues in the release notes. Some of them might be blocking the upgrade until they're resolved. You can find updates in the attached bug trackers.

Make sure that the Software & Updates application is set to notify you of new interim releases. See {ref}`switch-to-interim`.

You can force the upgrade manually on the command line:

```{terminal}
:copy:
:user:
:host:
:dir:
:input: sudo do-release-upgrade
```

If the normal upgrade path isn't available yet and you know what you're doing, you can also add the `--devel-release` option to upgrade to the latest development release:

```{terminal}
:copy:
:user:
:host:
:dir:
:input: sudo do-release-upgrade --devel-release
```

:::{warning}
Upgrading to a development release isn't supported and might break your system.
:::
