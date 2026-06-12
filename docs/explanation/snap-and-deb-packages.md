(snap-and-deb-packages)=
# Snap and Deb packages

Use the App Center to install and manage apps on Ubuntu Desktop. The App Center supports both snaps and deb packages.

## Packages

### Snaps (default)

The App Center shows [snaps](https://snapcraft.io/docs/) by default, both in the search and  the category pages. Snap apps update automatically and most are sandboxed. That means that you can control which system resources they can access. You can do this by changing the app permissions in the Settings app.

Some snaps, such as developer tools, use [classic confinement](https://snapcraft.io/docs/explanation/security/snap-confinement/#confinement-levels) and are not sandboxed. The Snap Store team [reviews these apps manually](https://snapcraft.io/docs/reference/administration/reviewing-classic-confinement-snaps/).

Snaps are updated daily. You can update quicker in the Manage page.

### Deb packages

You can also install and manage deb packages in the App Center. When you search for deb packages, you will get applications from the [official Ubuntu repositories](https://help.ubuntu.com/community/Repositories/Ubuntu). You can check if an app is a deb package by checking its App Center page.

Security updates for these packages are installed automatically by default. You can apply other updates with the Software Updater. For additional security on these packages, you can enable [Ubuntu Pro](https://ubuntu.com/pro) in the Security Center. Ubuntu Pro is free for personal use on up to 5 machines.

You can also use the App Center to install debs you downloaded for third-partyt developers. Note these might add their own repositories and will have unrestricted access to your resources as well, so make sure you trust the developer. Using apps from third party developers is [discouraged](https://ubuntu.com/server/docs/explanation/software/third-party-repository-usage/index.html).

### Other packages

Flatpaks are not supported in the App Center, but you can [install them on Ubuntu](https://flathub.org/setup/Ubuntu). Most flatpaks are sandboxed. You can manage permissions for flatpaks with [Flatseal](https://flathub.org/en/apps/com.github.tchx84.Flatseal) or [from the terminal](https://docs.flathub.org/docs/for-users/permissions).

AppImages are not supported in the App Center, but you can [run them on Ubuntu](https://docs.appimage.org/introduction/quickstart.html#ref-quickstart). AppImages are not sandboxed, so they have full access to your resources.

## Update apps

All snaps are updated daily by default. You can force the update of a snap in the Manage page in the App Center. Check the [snap documentation](https://snapcraft.io/docs/how-to-guides/manage-snaps/manage-updates/) for advanced settings.

Debs get automatic security updates daily by default. For non-security updates, use the Software Updater. Check the [apt documentation](https://ubuntu.com/server/docs/how-to/software/package-management/) for advanced settings.

## Change permissions

You can manage the permissions for sandboxed apps in the Settings app, under Apps.

For more granular control for files, camera and microphone, you can also try the experimental app permissions in the Security Center.

You can’t change permissions for deb packages nor for snaps with classic confinement: they have full access to your resources.
