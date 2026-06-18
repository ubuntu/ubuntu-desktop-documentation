---
relatedlinks: "[Get &#32; started &#32; with &#32; snaps](https://snapcraft.io/docs/tutorials/get-started/), [Install &#32; and &#32; manage &#32; deb &#32; packages](https://ubuntu.com/server/docs/how-to/software/package-management/)"
---

```{tags} Software
```

(snap-and-deb-packages)=
# Snap and deb packages

You can install apps and other software on Ubuntu using various package formats. The two official, recommended formats are snap and deb packages.

<!--
This page reuses some content originally written for the Community Help Wiki:
https://help.ubuntu.com/community/InstallingSoftware
-->

## What a package is

Software is a very broad term, and is generally taken to mean a program which you can run on your computer. However, such programs often need other resources to work. When you install software, thousands of files may be required just to let the program start. When you think that they all have to be put in exactly the right location, and some of those files may might to be changed depending on what type of computer you have, it can all get very complicated.

Ubuntu uses packages to store everything that a particular program needs to run. A 'package', then, is essentially a collection of files bundled into a single file, which can be handled much more easily. In addition to the files required for the program to run, there are often special files called installation scripts, which copy the files to where they are needed and configure them.


## Source and binary

**Source code** is written by programmers and is essentially a list of instructions to a computer which humans are able to read and write. Computers can only understand this code if it is interpreted for them into a form that they can use directly. One such way of interpreting source code for a computer is by translating or *compiling* it into **binary**, which computers can understand. This binary is then compressed into a *binary package* together with other resources.

Different computers use different types of binary, so if you make a binary package for one type (like an Intel PC), it won't work on another (like an ARM system). This is why you can find the same package, or even the whole Ubuntu installation image, available in several versions for different computer architectures.

Ubuntu chooses the correct binary packages for your system automatically, so you don't have to worry about picking the right ones.

:::{tip}
To find out which architecture you're using, open the Terminal app and enter the following command:

```{terminal}
:copy:

uname -m

x86_64
```

Here, `x86_64` stands for the Intel and AMD 64-bit PC architecture.
:::


## Dependencies

Programs often use some of the same files as each other. Rather than putting these files into each package, a separate package can be installed to provide them for all of the programs that need them. So, to install a program which needs one of these files, the package containing those files must also be installed. When a package depends on another in this way, it is known as a package dependency. By specifying dependencies, packages can be made smaller and simpler, and duplicates of files and programs are mostly removed.

Snap and deb packages have different solutions to package dependencies.


## Snap packages

The App Center on Ubuntu Desktop shows snaps by default, both in the search and on the category pages. Snap apps are usually *sandboxed*. That means that you can limit which system resources they can access.

Updates
: All snaps are updated daily by default. You can update immediately on the {guilabel}`Manage` page of the App Center.

  For advanced settings, refer to {external:ref}`how-to-guides-work-with-snaps-manage-updates`.

App permissions
: You can manage the permissions for sandboxed apps in {menuselection}`Settings --> Apps`.

  For more granular control for files, camera and microphone, you can also try the experimental app permissions in the Security Center.

  Some snaps, such as developer tools, use {external:ref}`classic confinement <explanation-security-snap-confinement>` and are not sandboxed. They have full access to your resources. The Snap Store team {external:ref}`reviews these apps manually <interfaces-reviewing-classic-confinement-snaps>`.

Package dependencies
: When you install a snap package, it makes sure that a base snap such as `core26` is installed for certain underlying resources. A base is a special kind of snap that provides a run-time environment with a minimal set of libraries that are common to most applications. A base snap is usually shared between many applications that need it.

  See [Bases](https://documentation.ubuntu.com/snapcraft/stable/reference/bases/) for more details.

  Resources that can't be found in the base snap are often included directly (*bundled*) in the app's snap package.

Package managers
: On Ubuntu Desktop, you can manage snaps using the App Center. See {ref}`install-or-remove-software`.

  On the command line, you can use the `snap` tool. See [the tutorial](https://snapcraft.io/docs/tutorials/get-started/).

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

Package dependencies
: When you install a deb package, it often installs many other dependency packages. Applications packaged as debs tend to be broken up into many small packages that can be efficiently reused in different combinations. Sometimes, you'll notice that tens of packages are pulled in for your app, for example. However, many dependencies are already installed by default on Ubuntu.

Package managers
: On Ubuntu Desktop, you can manage debs using the App Center. See {ref}`install-or-remove-software`.

  On the command line, you can use the `apt` tool. See the {external+server:ref}`managing-software` tutorial.
