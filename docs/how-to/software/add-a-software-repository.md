---
relatedlinks: "[Extra &#32 software &#32 - &#32 Ubuntu &#32 Server &#32 documentation](https://ubuntu.com/server/docs/how-to/software/package-management/#extra-repositories), https://ubuntu.com/server/docs/explanation/software/third-party-repository-usage/, https://help.ubuntu.com/community/Repositories/Ubuntu, https://help.ubuntu.com/community/Repositories/CommandLine"
---

(add-a-software-repository)=
# Add a software repository

In addition to official Ubuntu sources, software is also available from third-party, community-maintained sources. If you want to install software from a third-party software repository, you must add it to Ubuntu's list of available repositories.

:::{warning}
Only add software repositories from sources that you trust!

Third-party software repositories are not checked for security or reliability by Ubuntu members, and may contain software which is harmful to your computer.
:::

## Add a PPA

Personal Package Archives (PPAs) are software repositories designed for Ubuntu users and are easier to install than other third-party repositories. PPAs are often used to distribute pre-release software so that it can be tested.

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui

1. On the PPA's overview page, look for the {guilabel}`Adding this PPA to your system` heading. Copy the PPA's location, which should look similar to: `ppa:mozillateam/firefox-next`.

1. Open the Software & Updates application.

1. Switch to the Other Software tab.

1. Click {guilabel}`Add` and enter the PPA's location that you copied earlier.

1. Click {guilabel}`Add Source`. Enter your password.

1. Close the Software & Updates window. App Center will then check your software sources for new software, including the PPA that you've just added.
:::
:::{tab-item} Command line
:sync: terminal

1. On the PPA's overview page, look for the {guilabel}`Adding this PPA to your system` heading. Copy the PPA's location, which should look similar to: `ppa:mozillateam/firefox-next`.

1. Enable the PPA using the `add-apt-repository` tool:

    <!--
    Should be installed by default. On older or minimal Ubuntu releases, you may have to install software-properties-common and/or python-software-properties first:
    sudo apt-get install python-software-properties
    -->
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo add-apt-repository ppa:<user>/<repo-name>
    ```

    Replace `ppa:<user>/<repo-name>` with the PPA's location that you copied earlier.

1. Check your software sources for new software, including the PPA that you've just added:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt update
    ```
:::
::::

You can now install software from the PPA.

## Add a third-party repository other than PPA

You can find many software repositories for Ubuntu outside of the PPA platform. These are managed using standard Debian tools, and they require more manual steps.

1. Open the Software & Updates application.

1. Switch to the Other Software tab.

1. Click {guilabel}`Add` and enter the APT line for the repository. This should be available from the website of the repository, and should look similar to:

    ```text
    deb http://archive.ubuntu.com/ubuntu/ questing main
    ```

1. Click {guilabel}`Add Source`. Enter your password.

1. Close the Software & Updates window. App Center will then check your software sources for new software.

1. Check if the repository provides a signing key (GPG key) to be able to verify downloaded packages. Follow possible instructions on how to download and install the signing key.
