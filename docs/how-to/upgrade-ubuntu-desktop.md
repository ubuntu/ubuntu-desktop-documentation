---
relatedlinks: "[NobleUpgrades/Kubuntu](https://help.ubuntu.com/community/NobleUpgrades/Kubuntu),
  [QuestingUpgrades/Kubuntu](https://help.ubuntu.com/community/QuestingUpgrades/Kubuntu),
  [Upgrading &#32 Lubuntu](https://manual.lubuntu.me/stable/D/upgrading.html),
  [Upgrading &#32 to &#32 Ubuntu &#32 Studio &#32; 24.04 &#32; LTS](https://ubuntustudio.org/ubuntu-studio-24-04-lts-release-notes/#upgrading),
  [Upgrading &#32 to &#32 Ubuntu &#32 Studio &#32; 25.10](https://discourse.ubuntu.com/t/ubuntu-studio-25-10-release-notes/67578#p-175511-upgrading-to-ubuntu-studio-2510),
  [Upgrading &#32; to &#32; Xubuntu &#32; 24.04](https://wiki.xubuntu.org/releases/24.04/upgrading),
  [Upgrading &#32; to &#32; Xubuntu &#32; 25.10](https://wiki.xubuntu.org/releases/25.10/upgrading),
  [UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)"
---

(upgrade-ubuntu-desktop)=
# Upgrade Ubuntu Desktop

<!--
Originally, this comes from a Tutorial and a Community Help Wiki pages:

https://discourse.ubuntu.com/t/upgrade-ubuntu-desktop/14012
Author 	Oliver Smith oliversmith@canonical.com

https://help.ubuntu.com/community/QuestingUpgrades/
https://help.ubuntu.com/community/UpgradeNotes
-->

You can upgrade your Ubuntu installation when a new version comes out. The upgrade process is interactive and takes up to an hour, depending on your internet connection speed and computer performance.

You benefit from getting the latest software, including new security patches, and all the upgraded technology that comes with a new release without having to reinstall and reconfigure your system.

:::{note}
If you're upgrading from a very outdated release, you might have to repeat the upgrade process several times.

Ubuntu only supports sequential upgrades: from one Long Term Support (LTS) release to the next, or from one interim release to the next.
:::


## Latest releases

Your Ubuntu installation follows one of these upgrade paths:

* If you're using a **Long Term Support (LTS) release** like most of Ubuntu users, the latest version that you can upgrade to is [Ubuntu 24.04 LTS](https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890).

    Upgrades to the latest LTS release become available after the first point release, such as with Ubuntu 24.04.01. This usually happens several months after the initial release.

* If you're using **interim releases**, you can upgrade to [Ubuntu 25.10](https://discourse.ubuntu.com/t/questing-quokka-release-notes/59220).

    Upgrades to the latest interim release become available a few days after the official release date.

If you want to upgrade from an LTS release to an interim release, see {ref}`switch-between-an-lts-and-interim-release`.


## Prepare for the upgrade

* If you're using a laptop or a mobile device, make sure that it's **plugged into a power source**.

* Check that there is **enough free disk space**. Ubuntu needs to store several gigabytes of data during the upgrade.

* **Back up** all of your user data to an external storage device. Although it's unlikely that data will be lost during the upgrade process, it's better to be safe than sorry.

* Make sure that your current Ubuntu installation is fully **updated**:

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

Start the application that upgrades your system:

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

If no upgrade is available, you're either on the latest version of Ubuntu or upgrades to the latest release haven't been enabled yet.

The process is interactive. Follow the application's instructions and confirm the prompts:

1. The application presents an **overview** of the upgrade, including a link to the release notes.

1. When all upgrade requirements have been gathered, the application shows an overview of the **packages** to be installed and removed.

1. If you installed packages from Personal Package Archives (PPAs) or third-party repositories, the **Foreign Packages Installed** prompt opens.

    You can try to proceed with the upgrade. If the upgrade fails, remove the packages manually and try the upgrade again. When you log into the upgraded system later, reinstall the third-party packages.

1. While the upgrade is in progress, you might see visual **glitches** on your screen, such as changing icons. This is normal. Wait until the process is complete.

1. When new packages have been installed, the application prompts you to remove the **obsolete packages** from the previous Ubuntu release.

    Unless you have a reason to keep the packages, it's best to remove them. This usually takes a minute or two.

1. When the upgrade is complete, **restart** your computer.


## Finalize the upgrade

Your new, upgraded Ubuntu starts up. Log in and check that everything works as expected.

Third-party software repositories and PPAs might have been disabled during the release upgrade. Check if you need to re-enable them or find updated versions. You can do this in the Software & Updates application, on the {guilabel}`Other Software` tab.


## Troubleshooting

You might encounter these problems when trying to upgrade Ubuntu.

### The upgrade isn't available

LTS upgrades only become available with the first point release, such as 24.04.1.

Upgrades to the latest interim release become available several days after the official release date. This is to allow time for any critical bugs to be fixed before prompting all users to upgrade. Check again in a few days. If it's been more than a couple of days, look for known issues in the release notes. Some of them might be blocking the upgrade until they're resolved. You can find updates in the attached bug trackers.

If you want to upgrade to an interim release, make sure that your system is {ref}`properly configured <switch-between-an-lts-and-interim-release>`.

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

### The system is slow

Your machine might be slow to reboot right after the upgrade because it still needs to complete the initial configuration. After that, it should be back to normal speed.

If it seems that the new Ubuntu release is much slower than the previous one, check the system requirements in the release notes to make sure that your hardware is still supported.

You can also {ref}`reinstall Ubuntu <install-ubuntu-desktop>` from scratch to get a clean system.

You can return to an earlier LTS release by reinstalling Ubuntu. Downgrading the existing system isn't supported. Make sure that the release that you choose still receives security updates.

Consider [Ubuntu flavors](https://ubuntu.com/desktop/flavors). These are community projects that provide alternative desktop environments and default applications. They might run better on older hardware while still being based on the latest Ubuntu release. However, flavors aren't supported by Canonical.

### The system powered off during the upgrade

If  your computer lost power during the upgrade, try to start it again. It might be able to resume the upgrade process. Log in and try to fix any broken packages.

1. Configure unpacked updates:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo dpkg --configure -a
    ```

1. Fix broken dependencies:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    :input: sudo apt --fix-broken install
    ```

If you can't log in or the these steps didn't work, it's best to ask for help on the Ubuntu support channels. See {ref}`project-and-community`.
