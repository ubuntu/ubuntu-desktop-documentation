```{tags} Accessibility
```

(read-screen-aloud)=
# Read the screen aloud

You can enable the Orca screen reader, which speaks the user interface.

To learn its basic control, go to {ref}`get-started-with-the-screen-reader`.

{{a11y_limitations}}


1. Start Orca:

    ::::{tab-set}
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

    :::{tab-item} Using Settings
    :sync: orca-activities

    1. Open the Activities overview and start typing **accessibility**.
    2. Click {guilabel}`Accessibility` to open the panel.
    3. Open the {guilabel}`Seeing` section.
    4. Enable the {guilabel}`Screen Reader` option.
    :::
    ::::

2. Listen to the Orca help. Orca tells you its version and gives you pointers on how to use the screen reader:

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

    To exit help mode, press {kbd}`Esc`.

3. If you use Firefox, close it and reopen it. Orca can then read the browser content.


The screen reader stays active the next time that you log in.


## Installing the screen reader

Orca is installed by default on Ubuntu Desktop. If you're using a custom desktop or package set, Orca might not be installed. Install it using the following command:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo apt install orca
```


## Controlling the screen reader

The Orca screen reader recognizes many keyboard commands to navigate the user interface, interact with windows and read documents:

* {ref}`navigate-the-screen-using-the-screen-reader`
* {ref}`read-documents-and-web-pages-using-the-screen-reader`
