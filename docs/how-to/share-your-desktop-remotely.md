```{tags} Remote access
```

(share-your-desktop-remotely)=
# Share your desktop remotely

<!--
Related test plan: <https://wiki.ubuntu.com/DesktopTeam/TestPlans/RemoteDesktop>
-->

You can enable remote desktop sharing on your system. This way, you or other people will be able to view or control your desktop from another computer in real time. The desktop sharing works over the Remote Desktop Protocol (RDP).

We'll refer to the system that shares its desktop as the *server*. We'll call the system that accesses the shared desktop remotely the *client*.

:::{rubric} What you'll need
:::

- Ubuntu Desktop 24.04 LTS or later with GNOME on the server.
- If you want to share your desktop outside of your local network, you need access to your router's configuration, the ability to configure a Virtual Private Network (VPN) or reach out to your network administrator.

## Enable remote desktop sharing

Go to {menuselection}`Settings --> System --> Remote Desktop`.

Enable Desktop Sharing, Remote Login or both:

:::{list-table}
:header-rows: 1
:widths: 1 2 2
    
* -
  - Desktop Sharing
  - Remote Login

* - User session
  - The remote client can connect to your running user session. You must be **logged in** on the server for the connection to work.
  - The remote client can access a login screen and they can start your user session remotely. You must be **logged out** on the server for the connection to work.

* - Remote control
  - You can decide whether the client can also **control** your user session, or if they can only **watch** your screen.
  - The client is always able to **control** your user session.

* - Image quality
  - The resolution of the shared screen is determined by your user session on the server. Therefore, the screen might look **too small, too large or blurry** due to scaling on the client.
  - The resolution of the shared screen is determined by the window on the client. Therefore, the screen is always the **right size and looks sharp**.
:::

<!--
The reason for this screenshot is that the host name, user name and password might be confusing to the reader or too abstract if not seen in context of the remote desktop configuration.
-->
![Desktop Sharing enabled in Settings](/images/gnome-remote-desktop.png)

## Find the access credentials

When you connect from a remote client, you have to know the remote desktop user name and password, the host name of the server and the port number that provides RDP access.

### User name and password

In {menuselection}`Settings --> System --> Remote Desktop`, note down the user name and password.

These are different from your regular user credentials, and they only work for the remote desktop sharing. You can change them here without affecting how you log in.

### Host name on the local network

To point the client to the location of your server, you need either the server host name or its IP address.

If the server and client are both on the **same network**, for example on **your home Wi-Fi**, you can use the host name that you find in {menuselection}`Settings --> System --> Remote Desktop`. You might need to add the `.local` suffix at the end when entering it on the client.

Alternatively, you can use the IPv4 address of the server. Display your local IPv4 address:

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui

If you're using wired network, go to {menuselection}`Settings --> Wired --> your connected network --> Network Options (gear icon) --> IPv4 Address`.

If you're on Wi-Fi, go to {menuselection}`Settings --> Wi-Fi --> your connected network --> Network Options (gear icon) --> IPv4 Address`.
:::

:::{tab-item} Command line
:sync: terminal

```{terminal}
:copy:
:user:
:host:
:dir:
ip -4 address

[...]
2: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> [...]
    inet 192.168.0.91/24 [...]
[...]
```

Here, your IPv4 address is 192.168.0.91.
:::
::::

:::{warning}
The local IPv4 address might change when you reboot the server or reconnect to the network.
:::

### Host name on a public network

If you're sharing the desktop between **different networks**, for example between **your office and your home Wi-Fi**, you need a public IPv4 or IPv6 address for the server.

You might have to configure port forwarding in your router's configuration, or set up access to the server through a VPN.

:::{important}
With port forwarding, you open up your system to the world. This is a security risk because attackers might try to break into your system.

If you only want to share the desktop with a private group of people, use the VPN instead.
:::

Check with your internet provider or your network administrator.

### Port number

By default, Desktop Sharing and Remote Login both use the 3389 port on your system. However, if you enable them both at the same time, Desktop Sharing switches to port 3390, while Remote Login keeps port 3389. You can then choose the connection type to use at the remote client by setting the port number.

## Open RDP ports in your firewall

If the firewall is active, allow RDP connections to your system:

::::{tab-set}
:::{tab-item} Graphical interface
:sync: gui

If the Firewall (`gufw`) application is installed, open it and go to the Rules tab.

Click {guilabel}`Add a rule…` ({guilabel}`+`). Switch to the Simple tab. Enter the following configuration:

* **Policy:** Allow

* **Direction:** In

* **Protocol:** TCP

* **Port:** 3389:3390

Click {guilabel}`Add` to confirm.
:::

:::{tab-item} Command line
:sync: terminal

```{terminal}
:copy:
:user:
:host:
:dir:
sudo ufw allow 3389:3390/tcp
```
```{terminal}
:copy:
:user:
:host:
:dir:
sudo ufw reload
```
:::
::::

## Connect from a client

To connect to this system from a remote client, use an application that supports RDP. Enter the credentials that you've noted down.

On Ubuntu, you can use the Remmina application. See {ref}`access-a-remote-desktop`.
