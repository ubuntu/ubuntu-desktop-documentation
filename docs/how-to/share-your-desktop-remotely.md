(share-your-desktop-remotely)=
# Share your desktop remotely

What you'll need:

- Ubuntu Desktop 24.04 LTS or later with GNOME

1. Go to {menuselection}`Settings --> System --> Remote Desktop`.

1. Enable Desktop Sharing, Remote Login or both.

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
    
    Note down the user name and password. These are different from your regular user credentials, and they only work for the remote desktop sharing.
    
    By default, both types of connection use the 3389 port on your system. However, if you enable both at the same time, Desktop Sharing switches to port 3390, while Remote Login keeps port 3389. You can then choose the connection type from the remote client by setting the right port number.

1. If the firewall is active on your system, allow RDP connections to your system:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ufw allow 3389/tcp
    ```
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ufw allow 3390/tcp
    ```
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo ufw reload
    ```

1. Connect to this system from a remote client. See {ref}`access-a-remote-desktop`.
