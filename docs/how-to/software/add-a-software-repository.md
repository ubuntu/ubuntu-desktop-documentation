(add-a-software-repository)=
# Add a software repository

Software is available from third-party sources, as well as from the default Ubuntu software repositories. If you want to install software from a third-party software repository, you must add it to Ubuntu's list of available repositories.

:::{warning}
Only add software repositories from sources that you trust!

Third-party software repositories are not checked for security or reliability by Ubuntu members, and may contain software which is harmful to your computer.
:::

## Add a PPA

Personal Package Archives (PPAs) are software repositories designed for Ubuntu users and are easier to install than other third-party repositories. PPAs are often used to distribute pre-release software so that it can be tested.

1. On the PPA's overview page, look for the {guilabel}`Adding this PPA to your system` heading. Make a note of the PPA's location, which should look similar to: `ppa:mozillateam/firefox-next`.

1. Open the Software & Updates application.

1. Switch to the Other Software tab.

1. Click {guilabel}`Add` and enter the PPA's location that you noted earlier.

1. Click {guilabel}`Add Source`. Enter your password.

1. Close the Software & Updates window. App Center will then check your software sources for new software.


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
