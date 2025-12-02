(upgrade-to-ubuntu-24.04-lts)=
# Upgrade to Ubuntu 24.04 LTS

If you’re already running Ubuntu, you can upgrade to a newer release in a few clicks from the Software Updater. Discover how in this quick tutorial, updated for Ubuntu 24.04 LTS.

<!--
Migrated from a Tutorial:
https://discourse.ubuntu.com/t/upgrade-ubuntu-desktop/14012
Original author: Oliver Smith <oliversmith@canonical.com>|
-->

You benefit from getting the latest software, including new security patches, and all the upgraded technology that comes with a new release without having to reinstall and reconfigure your system.

Users on a Long Term Supported release such as **Ubuntu 20.04 LTS** will be prompted to upgrade once the first point release of the following LTS is available. For **Ubuntu 22.04 LTS** this prompt will appear once Ubuntu 22.04.1 LTS is available.

![|624x264](https://assets.ubuntu.com/v1/92f22162-tutorial1.png)

If you are trying to upgrade to an interim release in future (such as the upcoming Ubuntu 22.10). You may need to change your Update settings for the prompt to appear. See ‘Upgrading to interim releases’ at the end of this tutorial.

## Getting ready to upgrade

Before proceeding ensure that your software is up to date by running:

```
sudo apt update
sudo apt upgrade
```

From your terminal, entering your password and pressing **Y** when prompted.


## Follow the upgrade flow

From this point on, the upgrade UI will guide you through the process. First you will see a link to the release notes for the target release, detailing the newest features, improvements and known issues.

![|624x489](https://assets.ubuntu.com/v1/6e924165-tutorial4.png)

Click **Upgrade** to continue.

This will take you to an overview window showing you the progress of the upgrade.

![|535x432](https://assets.ubuntu.com/v1/ecbe7f12-tutorial5.png)

As this progresses through the stages you will receive some additional prompts to progress once the upgrade requirements have been gathered.

![|624x413](https://assets.ubuntu.com/v1/b2fb0f68-tutorial6.png)

Click **Start Upgrade** to continue.

To prevent the OS locking during the process, the lock screen will be disabled.

![|624x316](https://assets.ubuntu.com/v1/c94cc6ac-tutorial7.png)

Click **Close** to continue.

Once the newest packages have been installed you’ll be prompted to remove the obsolete packages from the previous Ubuntu release.

![|624x413](https://assets.ubuntu.com/v1/132bf202-tutorial8.png)

You can choose to keep them, but by default it’s okay to click **Remove** to progress.

Despite the warning that removing packages can take several hours, this is extremely unlikely and after a minute or two you will be prompted to restart your system to complete the upgrade.

![|624x367](https://assets.ubuntu.com/v1/745da112-tutorial9.png)

Click **Restart Now** to complete the upgrade

## Enjoy your shiny new Ubuntu!

![|624x391](https://assets.ubuntu.com/v1/5a52f609-tutorial10.png)

That’s it! Your machine may be slower to reboot during this final step as it completes the initial configuration but after that you’ll be up and running with the latest release of Ubuntu. We hope you enjoy all the new features and functionality it has to offer!

### Help is always at hand

If you have any issues with your upgrade process, or get stuck along the way, you can always reach out to our community.

- [Ubuntu Discourse](https://discourse.ubuntu.com) 
- [Ask Ubuntu](https://askubuntu.com/)
