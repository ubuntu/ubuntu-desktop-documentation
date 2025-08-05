(read-screen-in-braille)=
# Read the screen in Braille

The Orca screen reader can display the user interface on a refreshable Braille display. It uses the BRLTTY service, which provides access to the Linux console for a blind person using a refreshable Braille display. 

To learn the basic control of the screen reader, go to {ref}`getting-started-with-the-screen-reader`.

{{a11y_limitations}}


1. Add your user to the `brlapi` group to allow access to the Braille device:

    ```bash
    sudo usermod --append -G brlapi <user-name>
    ```

2. Enable the BRLTTY service:

    ```bash
    sudo systemctl enable --now brltty
    ```

3. Start the Orca screen reader. If it's already enabled, restart it:

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

4. Open Orca preferences:

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
    orca --setup
    ```
    :::
    ::::

5. Under the {guilabel}`Braille` tab, make sure that {guilabel}`Enable Braille support` is on.

6. Click {guilabel}`OK` to confirm.

7. Connect your Braille device to the system over USB, serial port or Bluetooth.

8. If you use Firefox, close it and reopen it. Orca can then read the browser content.


## Disable speech

The screen reader speaks at the same time as it presents text on your Braille device. You can disable speech:

::::{tab-set}
:::{tab-item} Laptop layout
:sync: orca-laptop

{kbd}`CapsLock+S`
:::

:::{tab-item} Desktop layout
:sync: orca-desktop

{kbd}`Insert+S`
:::
::::


## Braille display commands

You can control the screen reader from your Braille device. Use the following commands:

:::{list-table}
   :header-rows: 1

* - Action
  - Key

* - Pan Braille display to the left
  - Line Left

* - Pan Braille display to the right
  - Line Right

* - Toggle Flat Review mode
  - Freeze

* - Review the word above
  - Line Up

* - Review the word below
  - Line Down

* - Review bottom left
  - Bottom Right

* - Review the home position
  - Top Left

* - Contracted Braille
  - Six Dots

* - Mark the beginning of a text selection
  - Cut Begin

* - Mark the end of a text selection
  - Cut Line

* - Process a cursor routing key
  - Cursor Routing

* - Return to the object with keyboard focus
  - Cursor Position
:::

## Read a document in a different language

If you're reading a document in a language different than your system language, set the language text table in BRLTTY.

1. Browse the available text tables. They're stored in the `/etc/brltty/Text/` directory:

    ```bash
    ls /etc/brltty/Text/
    ```

2. Select the code of the language that you need for your document.

    For example, if you want to read a document in Italian, the text table file is `/etc/brltty/Text/it.ttb` and the language code is `it`.

3. In the `/etc/brltty.conf` file, set the language code in the `text-table` directive. For example, to set the Italian text table:

    ```text
    text-table	it
    ```

## Configure the Braille screen reader

You can configure how Orca presents information on the Braille display.

1. Open Orca preferences:

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

2. Go to the {guilabel}`Braille` tab.

For an explanation of the Orca Braille settings, see [Braille Preferences](https://help.gnome.org/users/orca/stable/preferences_braille.html.en) in the Orca documentation.


## Troubleshooting

Fix common issues with the Braille screen reader.

### The screen reader isn't installed
    
Orca and Braille support are installed by default on Ubuntu Desktop. If you're using a custom desktop or package set, they might not be installed.
    
* Make sure that Orca is installed:

    ```bash
    sudo apt install orca
    ```

* Make sure that the BRLTTY service is installed:

    ```bash
    sudo apt install brltty brltty-espeak
    ```

### My Braille device isn't detected

If your Braille devices isn't detected, try the following options.

* Manually set the driver for your Braille device:

    1. In the `/etc/brltty.conf` file, find the `braille-driver` directive.
    2. Uncomment the line that lists your Braille device driver.

* Manually set the connection method:

    1. In the `/etc/brltty.conf` file, find the `braille-device` directive.
    2. Uncomment the line that matches your connection method.

        For example, to connect to the first paired Bluetooth device that matches your Braille driver, use the following line:

        ```text
        braille-device bluetooth:
        ```

