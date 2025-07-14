(work-around-known-screen-reader-issues)=
# Work around known screen reader issues

Ubuntu 24.04 LTS has certain known issues when using the screen reader. If you encounter them, you can use the following ways to improve accessibility.

## Reconfigure the Orca modifier

With the laptop layout, Orca uses {kbd}`CapsLock` as the Orca modifier in keyboard shortcuts. Sometimes, {kbd}`CapsLock` is unreliable as the modifier and doesn't trigger the intended command. The {kbd}`Insert` modifier is more reliable.

To work around the issue, you have several options:

* Connect a full-size keyboard with a numeric keypad.

    In Orca preferences on the {guilabel}`General` tab, make sure that Orca switches to the desktop layout.

* If your keyboard has the {kbd}`Insert` key, switch to the {kbd}`Insert` modifier while keeping the laptop layout.

    In Orca preferences on the {guilabel}`Key Bindings` tab, switch {guilabel}`Screen Reader Modifier Key(s)` to {guilabel}`Insert, KP_Insert`.

    Next time you enter Orca commands, remember that you're still using the laptop layout but with {kbd}`Insert` rather than {kbd}`CapsLock`.

* Switch from the Wayland session to X11 (X\.org).

    Although the X11 session is deprecated, the {kbd}`CapsLock` modifier is more reliable there in Ubuntu 24.04.

    The option to select X11 is at the login screen.

## Replace GTK4 applications

GTK4 is the latest version of the GTK toolkit for creating GNOME application interfaces. Applications using the previous GTK3 toolkit are fully accessible. However, GTK4 applications in Ubuntu 24.04 only expose interactive elements such as buttons to the screen reader. You can navigate interactive elements using {kbd}`Tab`. Generally, the screen reader can't read static text such as document content in these applications. Features like Flat Review don't work.

To work around the issue, replace the GTK4 applications that pose issues to you with GTK3 applications:

Files
: Replace with Caja, which is available from the `caja` package.

    To launch Caja, press {kbd}`Alt+F2` and enter `caja`.

Text Editor
: Replace with Gedit, which is available from the `gedit` package.

Calculator
: Replace with MATE Calculator, which is available from the `mate-calc` package.

System Monitor
: Replace with MATE System Monitor, which is available from the `mate-system-monitor` package.

    To launch it, press {kbd}`Alt+F2` and enter `mate-system-monitor`.

## Replace Flutter applications

Flutter is the toolkit used to create Ubuntu applications such as the App Center or Firmware Updater. Currently, screen reader support is limited in Flutter applications across all Ubuntu releases. If you experience issues with these applications, consider replacing them with alternative ones:

App Center
: App Center manages Deb packages and snaps.

    The Synaptic application is a more accessible interface to Deb packages. It's available from the `synaptic` package.

    No alternative snap interface is currently more accessible than App Center.

Firmware Updater
: Replace with the GNOME Firmware application, which is available from the `gnome-firmware` package.

## Try different keyboard layouts

If you use a mix of various user interface languages and localized keyboard layouts, the screen reader might be using a different keyboard layout for its commands than your active layout. For example, You might be using the French layout but the screen reader commands treat your keyboard as if it had the American English layout.

If screen reader commands don't work, try pressing the key as if another relevant layout was active.

## Consider upgrading to the latest Ubuntu release

Ubuntu 25.04 and 25.10 greatly improve the screen reader experience. The {kbd}`CapsLock` modifier works as expected. GTK4 applications are fully accessible.

However, Flutter applications still only expose interactive elements.

