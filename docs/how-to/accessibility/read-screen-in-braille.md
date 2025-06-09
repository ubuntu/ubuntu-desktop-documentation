(read-screen-in-braille)=
# Read the screen in Braille

The Orca screen reader can display the user interface on a refreshable Braille display. It uses the BRLTTY service, which provides access to the Linux console for a blind person using a refreshable Braille display. 

1. Make sure that Orca is installed:

    ```bash
    sudo apt install orca
    ```

2. Make sure that the BRLTTY service is installed:

    ```bash
    sudo apt install brltty brltty-espeak
    ```

3. Add your user to the `brlapi` group to allow access to the Braille device:

    ```bash
    sudo usermod --append -G brlapi user-name
    ```

4. Enable the BRLTTY service:

    ```bash
    sudo systemctl enable --now brltty
    ```

5. Start the Orca screen reader. If it's already enabled, restart it:

    ::::{tab-set}
    :::{tab-item} Keyboard shortcut
    :sync: orca-keyboard

    {kbd}`Super+Alt+S`
    :::

    :::{tab-item} Accessibility menu
    :sync: orca-menu

    In the {ref}`accessibility menu <find-the-accessibility-menu>` in the top bar, select {guilabel}`Screen Reader`.
    :::
    ::::

5. Open Orca preferences:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Space`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+Space`
    :::

    :::{tab-item} Command
    :sync: orca-command

    ```bash
    orca -s
    ```
    :::
    ::::

6. Under the {guilabel}`Braille` tab, make sure that {guilabel}`Enable Braille support` is on.

7. Click {guilabel}`OK` to confirm.

8. Connect your Braille device to the system.

## Read a document in a different language

If you're reading a document in a language different than your system language, set the language text table in BRLTTY.

## Troubleshooting

