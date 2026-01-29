(access-a-remote-desktop)=
# Access a remote desktop

<!--
Original tutorial: <https://discourse.ubuntu.com/t/access-a-remote-desktop/13965>
Original author: Nicole Mikołajczyk <me@m4sk.in>
-->

You can view or control the desktop environment on another computer where desktop sharing is enabled. The desktop sharing works over the Remote Desktop Protocol (RDP) or the Virtual Network Computing (VNC) protocol.

On Ubuntu, we recommend using the Remmina application to access a remote desktop. It supports both RDP and VNC.

We'll refer to the system that shares its desktop as the *server*. We'll call the system that accesses the shared desktop remotely the *client*.

:::{rubric} What you'll need
:::

* A client computer running Ubuntu 24.04 LTS or later.
* A server where RDP or VNC desktop sharing is enabled. To configure desktop sharing on Ubuntu 24.04 LTS or later, see {ref}`share-your-desktop-remotely`.
* Access credentials to the server, including its host name, the port number, the user name and the password.

## Install Remmina

Remmina is part of the extended Ubuntu installation.

If you don't have Remmina on your system, install it:

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui

Search for Remmina in the App Center and install it there.
:::

:::{tab-item} Command line
:sync: terminal

Install Remmina as a Snap:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo snap install remmina
```

Alternatively, install Remmina as Deb packages:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install remmina remmina-plugin-rdp remmina-plugin-vnc
```
:::
::::

## Launch Remmina

Remmina’s user-interface is easy to use. A quick connection can be made from the entry field beneath the toolbar by switching from the RDP to the VNC protocol, entering the address of your VNC server and clicking “Connect !”. But for convenience, it’s far better to create a re-usable connection, which we’ll cover in the next step.

![screenshot](upload://uwwDltU2hhaGtHqm2d0sBu6c4Jj.png)

## Add a connection

Click on “New” to open the “Remote Desktop Preference” pane. The following details should be configured:

Server
: The IP address and port of the VNC server you wish to connect to. For example, 192.168.1.2:5901

User name
: Not necessary unless your server is using VNC users.

Password
: If your server uses a password, enter it here. If not entered and your server requires a password, you’ll be able to enter it after starting the connection.

Colour depth
: Choose 24-bit for a fast connection, such as across a LAN, or 256 colours when using a low bandwidth connection.

Quality
: Provides more control over bandwidth and rendering quality, with “Poor” trades visual quality for responsiveness, while “Best” does the opposite.

To enable audio...

Click “Save” when you’re happy with the connection. Now, let’s connect to our VNC!

## Connecting to the server

Connect to the VNC server by selecting your server profile and clicking “connect”.

In toolbar on the left, you have options to switch to fullscreen mode, change view and graphics quality.

If you can only see a fraction of the shared screen, the resolution is larger than your display. Click {guilabel}`Toggle scaled mode` in the toolbar to resize the shared screen to fit the window.
