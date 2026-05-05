```{tags} Customization
```

(change-the-default-terminal)=
# Change the default terminal

The default terminal, or terminal emulator, is the application that opens when you press {kbd}`Ctrl+Alt+T`. If multiple terminal emulators are installed, you can configure which one is the default.

:::{note}
This is the legacy way to set your default terminal on Ubuntu 24.10 an earlier. If you're using a later Ubuntu release, such as 26.04 LTS, switch the version of this guide to latest.
:::

1. Enter the following command in a terminal:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo update-alternatives --config x-terminal-emulator
  
    There are 2 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

      Selection    Path                             Priority   Status
    ------------------------------------------------------------
      0            /usr/bin/gnome-terminal.wrapper   40        auto mode
    * 1            /usr/bin/gnome-terminal.wrapper   40        manual mode
      2            /usr/bin/kgx                      40        manual mode

    Press <enter> to keep the current choice[*], or type selection number:
    ```

    It lists the terminal emulators that are available on your system. The current default is marked with an asterisk (`*`).

2. Type the number of your selected terminal and confirm with {kbd}`Enter`.

    If you choose auto mode (0), you let your system pick the default terminal. The default might change with future system updates.
