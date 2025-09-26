(improve-screen-reader-usability)=
# Improve screen reader usability

Ubuntu 24.04 LTS might present some challenges when using the screen reader. If you experience difficulty, the following tips can help enhance the screen reader experience.

## Reconfigure the Orca modifier

With the laptop layout, Orca uses {kbd}`CapsLock` as the Orca modifier in keyboard shortcuts. In some cases, {kbd}`CapsLock` might not reliably trigger the intended command. The {kbd}`Insert` modifier is more reliable.

To improve your experience, you have several options:

* Connect a full-size keyboard with a numeric keypad.

    In Orca preferences on the {guilabel}`General` tab, make sure that Orca switches to the desktop layout.

* If your keyboard has the {kbd}`Insert` key, switch to the {kbd}`Insert` modifier while keeping the laptop layout.

    In Orca preferences on the {guilabel}`Key Bindings` tab, switch {guilabel}`Screen Reader Modifier Key(s)` to {guilabel}`Insert, KP_Insert`.

    Next time you enter Orca commands, remember that you're still using the laptop layout but with {kbd}`Insert` rather than {kbd}`CapsLock`.

* Switch from the Wayland session to X11 (X\.org).

    Although the X11 session is deprecated, the {kbd}`CapsLock` modifier is more reliable there in Ubuntu 24.04.

    The option to select X11 is at the login screen.

## Alternatives to GTK4 applications

GTK4 is the latest version of the GTK toolkit for creating GNOME application interfaces. Applications using the previous GTK3 toolkit offer a more complete experience with screen readers. In Ubuntu 24.04, applications built with GTK4 might not expose all content to the screen reader, although they expose interactive elements such as buttons. You can navigate interactive elements using {kbd}`Tab`. Generally, the screen reader can't read static text such as document content in these applications.

To improve screen reader usability, replace the GTK4 applications that pose issues to you with GTK3 applications:

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

## Alternatives to Flutter applications

Flutter is the toolkit used to create Ubuntu applications such as App Center or Firmware Updater. Currently, screen reader support is limited in Flutter applications across all Ubuntu releases. If you encounter usability limitations, consider these alternatives:

App Center
: App Center manages Deb packages and snaps.

    The Synaptic application is a more accessible interface to Deb packages. It's available from the `synaptic` package.

    No alternative snap interface is currently more accessible than App Center.

Firmware Updater
: Replace with the GNOME Firmware application, which is available from the `gnome-firmware` package.

## Try different keyboard layouts

If you use a mix of various user interface languages and localized keyboard layouts, the screen reader might be using a different keyboard layout for its commands than your active layout. For example, you might be using the French layout but the screen reader commands treat your keyboard as if it had the American English layout.

If screen reader commands don't work, try pressing the key as if another relevant layout was active.

## Consider upgrading to the latest Ubuntu release

The Ubuntu Desktop team continues to improve the screen reader experience in each release. In Ubuntu 25.04 and 25.10, the {kbd}`CapsLock` modifier behaves more consistently, and screen reader support in GTK4 applications is enhanced.

## Enable Orca before running applications

This issue affects Firefox and Chromium-based browsers in particular but can occur with other applications. If Orca is enabled and works in your desktop environment but does not work properly in the application, for example, it does not read web pages in your browser, try closing the application and restarting Orca *before* launching the application again.
