(upgrade-to-ubuntu-interim)=
# Upgrade to Ubuntu 25.10

Ubuntu 25.10 is the version of the Ubuntu operating system being released in April 2025. The development codename given to this release is "Questing Quokka".

## Before You Start

- You can directly upgrade to Ubuntu 25.10 ("Questing Quokka") from Ubuntu 25.04 ("Plucky Puffin").

- Be sure that you have all updates applied to your current version of Ubuntu before you upgrade.

- Before upgrading it is recommended that you read the [release notes for Ubuntu 25.10](http://wiki.ubuntu.com/QuestingQuokka/ReleaseNotes), which document caveats and workarounds for known issues in this version.

If you have a version of Ubuntu other than 25.04, please see [UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) for information on how to upgrade.

## Upgrade from 25.04 to 25.10

### Upgrading Ubuntu Desktops to 25.10

You can easily upgrade over the network with the following procedure.

1. Run the **update-manager** application.

2. In Update Manager, click the **Settings...** button, and enter your password to start the Software Sources application.

3. Select the sub menu **Updates** from the Software Sources application.

4. Confirm the "Notify me of a new Ubuntu version:" option is set to "For any new version", and change it if otherwise.

5. Close the Software Sources application and return to Update Manager.

6. In Update Manager, click the **Check** button to check for new updates.

7. If there are any updates to install, use the **Install Updates** button to install them.
<!-- and press **Check** again after that is complete.-->

8. Run **update-manager**.

9. A message will appear informing you of the availability of the new release.

10. Click **Upgrade**.

11. Follow the on-screen instructions.

### Ubuntu Servers

1. Install `ubuntu-release-upgrader-core` if it is not already installed:

    ```bash
    sudo apt-get install ubuntu-release-upgrader-core
    ```

2. Edit `/etc/update-manager/release-upgrades` and set `Prompt=normal`.

3. Launch the upgrade tool:

    ```bash
    do-release-upgrade
    ```

4. Follow the on-screen instructions.

### Edubuntu

Please refer to the section "Upgrading Ubuntu Desktops to 25.10" above for instructions on upgrading.

### Lubuntu

Please refer to [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html) for our instructions on upgrading. You may note it contains no new detail, but maybe helpful if upgrade isn't found or other issues.

### Kubuntu

Specific instructions for upgrading Kubuntu to 25.10 can be founds at: [https://help.ubuntu.com/community/QuestingUpgrades/Kubuntu](https://help.ubuntu.com/community/QuestingUpgrades/Kubuntu).

### Ubuntu Budgie

Please refer to the section "Upgrading Ubuntu Desktops to 25.10" above for instructions on upgrading.

### Ubuntu Cinnamon

Please refer to the section "Upgrading Ubuntu Desktops to 25.10" above for instructions on upgrading.

### Ubuntu Kylin

Same steps as ubuntu and please refer to the section "Upgrading Ubuntu Desktops to 25.10" above.

### Ubuntu Studio

Specific instructions for upgrading Ubuntu Studio to 25.10 can be found at [Upgrading to Ubuntu Studio 25.04](https://discourse.ubuntu.com/t/ubuntu-studio-25-10-release-notes/53099#p-132280-upgrading-to-ubuntu-studio-2504-5).

### Xubuntu

Direct upgrades to Xubuntu 25.10 are supported from Xubuntu 25.04.

- [Upgrading to Xubuntu 25.10](https://wiki.xubuntu.org/releases/25.10/upgrading)

## See Also

- [UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) for all supported versions of Ubuntu

## Troubleshooting

See the [release notes](http://wiki.ubuntu.com/QuestingQuokka/ReleaseNotes)
