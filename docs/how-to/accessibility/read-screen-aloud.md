(read-screen-aloud)=
# Read the screen aloud

The Orca screen reader can speak the user interface.

{{a11y_limitations}}

1. Make sure that Orca is installed:

    ```bash
    sudo apt install orca
    ```

2. Start Orca:

    ::::{tab-set}
    :::{tab-item} Using Settings
    :sync: orca-activities

    1. Open the Activities overview and start typing **accessibility**.
    2. Click {guilabel}`Accessibility` to open the panel.
    3. Open the {guilabel}`Seeing` section.
    4. Enable the {guilabel}`Screen Reader` option.
    :::

    :::{tab-item} With a keyboard shortcut
    :sync: orca-keyboard

    Press {kbd}`Super+Alt+S`.

    You can also use this shortcut at the login screen.
    :::

    :::{tab-item} In the accessibility menu
    :sync: orca-menu

    In the {ref}`accessibility menu <find-the-accessibility-menu>` in the top bar, select {guilabel}`Screen Reader`.

    You can also use this menu at the login screen.
    :::
    ::::

3. Listen to the Orca help. Orca tells you its version and gives you pointers on how to use the screen reader:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+H`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+H`
    :::
    ::::

4. If you use Firefox, close it and reopen it. Orca can then read the browser content.


The screen reader stays active the next time that you log in.

