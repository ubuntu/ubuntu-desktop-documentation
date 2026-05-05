```{tags} Customization
```

(change-the-default-terminal)=
# Change the default terminal

The default terminal, or terminal emulator, is the application that opens when you press {kbd}`Ctrl+Alt+T`. If multiple terminal emulators are installed, you can configure which one is the default.

:::{note}
This is the current way to set your default terminal on Ubuntu 25.04 and later. If you're using an earlier Ubuntu release, such as 24.04 LTS, switch the version of this guide to 24.04.
:::

* Your terminal might enable you to set it as default in the terminal settings. Look for a button similar to {guilabel}`Set as default terminal` in the application preferences. The button might be located in the *Behavior* or *General* section.

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
