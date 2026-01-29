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

## Add a connection

Click {guilabel}`Add a new connection profile` ({guilabel}`+`). The Remote Desktop Preference window opens.

### Server credentials

Enter the server configuration:

Protocol
: If you're connecting to Ubuntu 24.04 LTS or later, or to Microsoft Windows, select RDP. If you're connecting to an earlier Ubuntu release, or to macOS, select VNC.

Server
: The host name or IP address of the server, and the port number assigned to RDP or VNC. For example, `ThinkPad-X1.local:3389` or `192.168.1.2:5901`.

Username
: The user name configured for desktop sharing. Note that this might be different from the actual user name on the server system. With VNC, the user name is only necessary if you're connecting to a server that uses VNC users.

Password
: The password configured for desktop sharing. Note that this might be different from the actual user password on the server system. If not entered and your server requires a password, you'll be able to enter it after starting the connection.

### Set the connection quality

Optionally, you can configure the connection speed and quality in the Remote Desktop Preference dialog:

Colour depth
: Choose 24-bit for a fast connection, such as across a LAN, or 256 colors when using a low bandwidth connection.

Quality (on the Advanced tab)
: Provides more control over bandwidth and rendering quality. {guilabel}`Poor` trades visual quality for responsiveness, while {guilabel}`Best` does the opposite.

### Enable audio

To hear the audio from the server on your client, set {guilabel}`Audio output mode` to {guilabel}`Local` on the Advanced tab.

### Confirm

Click {guilabel}`Save`. Remmina now lists the newly configured connection in the main window.

## Connect to the server

Double-click the configured connection. Remmina tries to connect to the server.

You might need to accept a certificate if this is your first time connecting to the server.

A window opens, displaying the screen on the remote server. Depending on the configuration, it might be the live user session or a login screen.

If you can only see a fraction of the shared screen, its resolution is larger than your display. Click {guilabel}`Toggle scaled mode` in the toolbar on the left to resize the shared screen to fit the window.

In toolbar, you also have options to switch to fullscreen mode, change view and graphics quality.

## Troubleshooting

If Remmina fails to connect to the server:

* Make sure that the server credentials are correct. Check the host name or IP address, the port number, the user name and the password. Try an IP address instead of a host name, or the other way around.

* If you have access to the server, make sure that it's running.

* Check the state of the user on the server:

    If you're trying to use the Desktop Sharing configuration, the user must be logged into the graphical session.

    If you're trying to use the Remote Login configuration, the user must be logged out.

* Make sure that the firewall on the server allows the RDP or VNC ports that you're connecting to.
