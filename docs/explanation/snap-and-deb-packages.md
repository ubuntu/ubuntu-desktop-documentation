---
relatedlinks: "[Get &#32; started &#32; with &#32; snaps](https://snapcraft.io/docs/tutorials/get-started/), [Install &#32; and &#32; manage &#32; deb &#32; packages](https://ubuntu.com/server/docs/how-to/software/package-management/)"
---

```{tags} Software
```

(snap-and-deb-packages)=
# Snap and deb packages

You can install apps and other software on Ubuntu using various package formats. The two official, recommended formats are snap and deb packages

## Snap packages

The App Center on Ubuntu Desktop shows snaps by default, both in the search and on the category pages. Snap apps are usually *sandboxed*. That means that you can limit which system resources they can access.

Updates
: All snaps are updated daily by default. You can update immediately on the {guilabel}`Manage` page of the App Center.

  For advanced settings, refer to {external:ref}`how-to-guides-work-with-snaps-manage-updates`.

App permissions
: You can manage the permissions for sandboxed apps in {menuselection}`Settings --> Apps`.

  For more granular control for files, camera and microphone, you can also try the experimental app permissions in the Security Center.

  Some snaps, such as developer tools, use {external:ref}`classic confinement <explanation-security-snap-confinement>` and are not sandboxed. They have full access to your resources. The Snap Store team {external:ref}`reviews these apps manually <interfaces-reviewing-classic-confinement-snaps>`.

## Deb packages

When you search for deb packages in the App Center, it lists applications from the {external:ref}`official Ubuntu repositories <package-archive>`. You can check if an app is a deb package on its App Center page.

You can also use the App Center to install debs that you've downloaded from third-party developers. These might add their own repositories and will have unrestricted access to your resources, so make sure that you trust the developer.

:::{warning}
Using deb apps from third party developers is discouraged. For details, refer to {external:ref}`third-party-repository-usage`.
:::

Updates
: Security updates for deb packages are installed automatically by default. You can apply other updates with the Software Updater.

  For extended security updates, you can enable [Ubuntu Pro](https://ubuntu.com/pro) in the Security Center. Ubuntu Pro is free for personal use on up to 5 machines.

  For advanced settings, refer to {external:ref}`automatic-updates`.

App permissions
: You can't change the permissions for apps installed from deb packages: they always have full access to your resources.
