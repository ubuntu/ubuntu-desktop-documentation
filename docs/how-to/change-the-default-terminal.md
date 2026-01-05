```{tags} Customization
```

(change-the-default-terminal)=
# Change the default terminal

The default terminal, or terminal emulator, is the application that opens when you press {kbd}`Ctrl+Alt+T`. If multiple terminal emulators are installed, you can configure which one is the default.


## On Ubuntu 24.04 LTS

1. Enter the following command in a terminal:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo update-alternatives --config x-terminal-emulator
    ```

    It lists the terminal emulators that are available on your system. The current default is marked with an asterisk (`*`).

    For example:

    ```text
    There are 2 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

      Selection    Path                             Priority   Status
    ------------------------------------------------------------
      0            /usr/bin/gnome-terminal.wrapper   40        auto mode
    * 1            /usr/bin/gnome-terminal.wrapper   40        manual mode
      2            /usr/bin/kgx                      40        manual mode

    Press <enter> to keep the current choice[*], or type selection number:
    ```

2. Type the number of your selected terminal and confirm with {kbd}`Enter`.

    If you choose auto mode (0), you let your system pick the default terminal. The default might change with future system updates.


## On Ubuntu 25.04 and later

Starting with Ubuntu 25.04, the way to set your default terminal has changed. Since Ubuntu 25.10, the Files application now also respects your configuration when you select {guilabel}`Open in Terminal` from the folder menu.

* Your terminal might enable you to set it as default in the terminal settings. Look for a button similar to {guilabel}`Set as default terminal` in the application preferences. The button might be located in the Behavior or General section.

* If your terminal doesn't have such settings, enter its XDG Desktop identifier in the `~/.config/ubuntu-xdg-terminals.list` file. For example:

    :::{list-table}
    :header-rows: 1

    * - Terminal
      - Identifier
    * - Ptyxis
      - `org.gnome.Ptyxis.desktop:new-window`
    * - GNOME Terminal
      - `org.gnome.Terminal.desktop`
    * - GNOME Console
      - `org.gnome.Console.desktop`
    * - Alacritty
      - `Alacritty.desktop`
    * - Kitty
      - `kitty.desktop`
    :::

    If the file lists multiple terminals, the first line takes precedence.

    :::{note}
    If you're not using the standard Ubuntu GNOME desktop, the name of the configuration file is different. For details, see the `xdg-terminal-exec` man page.
    :::
