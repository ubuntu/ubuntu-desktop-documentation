(snap-and-deb-packages)=
# Snap and Deb packages

Use the App Center to install and manage apps on Ubuntu Desktop. The App Center supports both snaps and deb packages.

## Snap packages (default)

The App Center shows [snaps](https://snapcraft.io/docs/) by default, both in the search and the category pages. Snap apps update automatically and most are *sandboxed*. That means that you can control which system resources they can access. You can do this by changing the app permissions in Settings.

Some snaps, such as developer tools, use {external:ref}`classic confinement <explanation-security-snap-confinement>` and are not sandboxed. The Snap Store team {external:ref}`reviews these apps manually <interfaces-reviewing-classic-confinement-snaps>`.

Updates
: All snaps are updated daily by default. You can update immediately on the {guilabel}`Manage` page of the App Center. For advanced settings, refer to {external:ref}`how-to-guides-work-with-snaps-manage-updates`.

App permissions
: You can manage the permissions for sandboxed apps in {menuselection}`Settings --> Apps`. For more granular control for files, camera and microphone, you can also try the experimental app permissions in the Security Center.

## Deb packages

You can also install and manage deb packages in the App Center. When you search for deb packages, you will get applications from the [official Ubuntu repositories](https://help.ubuntu.com/community/Repositories/Ubuntu). You can check if an app is a deb package by checking its App Center page.

You can also use the App Center to install debs you downloaded for third-party developers. Note these might add their own repositories and will have unrestricted access to your resources as well, so make sure you trust the developer. Using apps from third party developers is [discouraged](https://ubuntu.com/server/docs/explanation/software/third-party-repository-usage/index.html).

Updates
: Security updates for these packages are installed automatically by default. You can apply other updates with the Software Updater. For additional security on these packages, you can enable [Ubuntu Pro](https://ubuntu.com/pro) in the Security Center. Ubuntu Pro is free for personal use on up to 5 machines.

  Debs get automatic security updates daily by default. For non-security updates, use the Software Updater. Check the [apt documentation](https://ubuntu.com/server/docs/how-to/software/package-management/) for advanced settings.

App permissions
: You can’t change permissions for deb packages nor for snaps with classic confinement: they have full access to your resources.
