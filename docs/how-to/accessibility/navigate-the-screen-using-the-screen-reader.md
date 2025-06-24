(navigate-the-screen-using-the-screen-reader)=
# Navigate the screen using the screen reader

## Where am I?

In addition to dedicated commands for reading the title bar and the status bar, Orca provides two context-sensitive Where Am I commands: Basic Where Am I and Detailed Where Am I. Basic Where Am I is implemented for all objects. Detailed Where Am I is implemented just for those objects for which there is a significant amount of information you may wish to know, but likely will not wish to know all of the time.

The best way to become familiar with what Where Am I will present is to give the Where Am I commands a try. However, to give you a better idea of the context-sensitive nature of Orca's Where Am I feature, consider the following:

For most widgets, you will at least be told the label and/or name, the type or role of the widget, and the mnemonic and/or accelerator key if they happen to exist. In addition:

 If you are in the spell checker of an application where Orca provides enhanced support, a basic Where Am I will repeat the error respecting your spell check preferences. A detailed Where Am I will cause Orca to present the full details of the error.

***


Orca's Where Am I feature gives you context-sensitive details about your present location. For instance, in tables, Where Am I will give you details about the table cell you are in, but in text it will present the current line along with any text which happens to be selected. The full list of what you can expect Orca to present can be found in the Introduction to Where Am I.

Orca provides the following Where Am I commands:

* Perform basic Where Am I:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Enter`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+Enter`
    :::
    ::::

* Perform detailed Where Am I:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + double-press {kbd}`Enter`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert` + double-press {kbd}`Enter`
    :::
    ::::

In addition to the dedicated Where Am I commands, Orca has additional commands related to obtaining information about your present location:

* Present the title bar:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+/`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+Enter` on the numeric keypad
    :::
    ::::

* Present the status bar:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + double-press {kbd}`/`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert` + double-press {kbd}`Enter` on the numeric keypad
    :::
    ::::

