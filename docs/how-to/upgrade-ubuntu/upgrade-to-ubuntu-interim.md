(upgrade-to-ubuntu-interim)=
# Upgrade to Ubuntu 25.10

Ubuntu 25.10 is the version of the Ubuntu operating system being released in April 2025. The development codename given to this release is \"Questing Quokka\". []{#line-4 .anchor}[]{#line-5 .anchor}

# Before You Start {#Before_You_Start}

-   You can directly upgrade to Ubuntu 25.10 (\"Questing Quokka\") from Ubuntu 25.04 (\"Plucky Puffin\"). []{#line-8 .anchor}

-   Be sure that you have all updates applied to your current version of Ubuntu before you upgrade. []{#line-9 .anchor}

-   Before upgrading it is recommended that you read the [release notes for Ubuntu 25.10](http://wiki.ubuntu.com/QuestingQuokka/ReleaseNotes){.http}, which document caveats and workarounds for known issues in this version. []{#line-10 .anchor}[]{#line-11 .anchor}

If you have a version of Ubuntu other than 25.04, please see [UpgradeNotes](/community/UpgradeNotes) for information on how to upgrade. []{#line-12 .anchor}[]{#line-13 .anchor}

# Upgrade from 25.04 to 25.10 {#Upgrade_from_25.04_to_25.10}

## Upgrading Ubuntu Desktops to 25.10 {#Upgrading_Ubuntu_Desktops_to_25.10}

You can easily upgrade over the network with the following procedure. []{#line-18 .anchor}

1.  Run the **update-manager** application. []{#line-19 .anchor}

2.  In Update Manager, click the **Settings\...** button, and enter your password to start the Software Sources application. []{#line-20 .anchor}

3.  Select the sub menu **Updates** from the Software Sources application. []{#line-21 .anchor}

4.  Confirm the \"Notify me of a new Ubuntu version:\" option is set to \"For any new version\", and change it if otherwise. []{#line-22 .anchor}

5.  Close the Software Sources application and return to Update Manager. []{#line-23 .anchor}

6.  In Update Manager, click the **Check** button to check for new updates. []{#line-24 .anchor}

7.  If there are any updates to install, use the **Install Updates** button to install them. [, and press **Check** again after that is complete.]{.comment style="display:none"} []{#line-25 .anchor}

8.  Run **update-manager**. []{#line-26 .anchor}

9.  A message will appear informing you of the availability of the new release. []{#line-27 .anchor}

10. Click **Upgrade**. []{#line-28 .anchor}

11. Follow the on-screen instructions. []{#line-29 .anchor}[]{#line-30 .anchor}

## Ubuntu Servers {#Ubuntu_Servers}

1.  Install `ubuntu-release-upgrader-core`{.backtick} if it is not already installed: []{#line-33 .anchor}[]{#line-34 .anchor}

        sudo apt-get install ubuntu-release-upgrader-core

2.  Edit `/etc/update-manager/release-upgrades` and set `Prompt=normal` []{#line-36 .anchor}

3.  Launch the upgrade tool: []{#line-37 .anchor}[]{#line-38 .anchor}

        do-release-upgrade

4.  Follow the on-screen instructions. []{#line-40 .anchor}[]{#line-41 .anchor}

## Edubuntu {#Edubuntu}

Please refer to the section \"Upgrading Ubuntu Desktops to 25.10\" above for instructions on upgrading. []{#line-44 .anchor}[]{#line-45 .anchor}

## Lubuntu {#Lubuntu}

Please refer to [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html){.https} for our instructions on upgrading. You may note it contains no new detail, but maybe helpful if upgrade isn\'t found or other issues. []{#line-48 .anchor}[]{#line-49 .anchor}

## Kubuntu {#Kubuntu}

Specific instructions for upgrading Kubuntu to 25.10 can be founds at: [https://help.ubuntu.com/community/QuestingUpgrades/Kubuntu](https://help.ubuntu.com/community/QuestingUpgrades/Kubuntu){.https} []{#line-52 .anchor}[]{#line-53 .anchor}

## Ubuntu Budgie {#Ubuntu_Budgie}

Please refer to the section \"Upgrading Ubuntu Desktops to 25.10\" above for instructions on upgrading. []{#line-56 .anchor}[]{#line-57 .anchor}

## Ubuntu Cinnamon {#Ubuntu_Cinnamon}

Please refer to the section \"Upgrading Ubuntu Desktops to 25.10\" above for instructions on upgrading. []{#line-60 .anchor}[]{#line-61 .anchor}

## Ubuntu Kylin {#Ubuntu_Kylin}

Same steps as ubuntu and please refer to the section \"Upgrading Ubuntu Desktops to 25.10\" above. []{#line-64 .anchor}[]{#line-65 .anchor}

## Ubuntu Studio {#Ubuntu_Studio}

Specific instructions for upgrading Ubuntu Studio to 25.10 can be found at: [https://discourse.ubuntu.com/t/ubuntu-studio-25-10-release-notes/53099#p-132280-upgrading-to-ubuntu-studio-2504-5](https://discourse.ubuntu.com/t/ubuntu-studio-25-10-release-notes/53099#p-132280-upgrading-to-ubuntu-studio-2504-5){.https} []{#line-68 .anchor}[]{#line-69 .anchor}

## Xubuntu {#Xubuntu}

Direct upgrades to Xubuntu 25.10 are supported from Xubuntu 25.04. []{#line-72 .anchor}

-   [Upgrading to Xubuntu 25.10](https://wiki.xubuntu.org/releases/25.10/upgrading){.https} []{#line-73 .anchor}[]{#line-74 .anchor}

# See Also {#See_Also}

-   [UpgradeNotes](/community/UpgradeNotes) for all supported versions of Ubuntu []{#line-76 .anchor}[]{#line-77 .anchor}

# Troubleshooting {#Troubleshooting}

See the [release notes](http://wiki.ubuntu.com/QuestingPuffin/ReleaseNotes){.http}. []{#line-80 .anchor}[]{#line-81 .anchor}
