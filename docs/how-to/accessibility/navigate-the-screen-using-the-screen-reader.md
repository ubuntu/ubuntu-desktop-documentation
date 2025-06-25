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


## Examine a window

Orca's Flat Review feature allows you to spatially review the contents, both text and widgets, of the active window. In this mode, Orca treats the window as if it were a two-dimensional sheet of text, eliminating any notion of widget hierarchy or other logical grouping within the window.

The "flattened" contents, also known as the Flat Review context, can be navigated by line, by word, by character, and by object. In addition, you can perform a left-click or right-click on the object being reviewed. Finally, you can use Orca Find, a Flat-Review-based feature to search the active window's contents.

Because the Flat Review context is a spatial representation of the active window's contents, it is created when you first enter Flat Review and only contains those objects which are visible. As a result, you will not be able to use Flat Review to access items which are in the window but currently off-screen. In addition, if the window's contents change of their own accord, the Flat Review context will not automatically be updated. You can cause a new context to be built by toggling Flat Review off and back on.

Finally, Flat Review by its nature is a mode that cannot be used at the same time that Orca is tracking focus. Thus if you are in Flat Review and then use the application's navigation commands to move the caret or to give focus to another object, you will automatically leave Flat Review.

* Toggle flat review (refreshes the flat review context):

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+P`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+-` on the numeric keypad
    :::
    ::::

* Review current item/widget:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Ctrl+K`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+5` on the numeric keypad
    :::
    ::::

* Use Say All to review the current dialog or window:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + double-press {kbd}`;`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    Double-press {kbd}`+` on the numeric keypad
    :::
    ::::


### Review by line

* First line (The "home" position):

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Ctrl+U`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+7` on the numeric keypad
    :::
    ::::

* Previous line:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+U`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`7` on the numeric keypad
    :::
    ::::

* Current line:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+I`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`8` on the numeric keypad
    :::
    ::::

* Spell current line:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + double-press {kbd}`I`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    Double-press {kbd}`8` on the numeric keypad
    :::
    ::::

* Phonetically spell current line:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + triple-press {kbd}`I`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    Triple-press {kbd}`8` on the numeric keypad
    :::
    ::::

* Next line:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+O`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`9` on the numeric keypad
    :::
    ::::

* Last line (the "end" position):

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Ctrl+O`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+9` on the numeric keypad
    :::
    ::::

### Review by word

* Word above:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Ctrl+J`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+4` on the numeric keypad
    :::
    ::::

* Previous word:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+J`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`4` on the numeric keypad
    :::
    ::::

* Current word:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+K`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`5` on the numeric keypad
    :::
    ::::

* Spell current word:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + double-press {kbd}`K`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    Double-press {kbd}`5` on the numeric keypad
    :::
    ::::

* Phonetically spell current word:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + triple-press {kbd}`K`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    Triple-press {kbd}`5` on the numeric keypad
    :::
    ::::

* Next word:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+L`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`6` on the numeric keypad
    :::
    ::::

* Word below:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Ctrl+L`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+6` on the numeric keypad
    :::
    ::::

### Review by character

* Previous character:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+M`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`1` on the numeric keypad
    :::
    ::::

* Current character:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+,`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`2` on the numeric keypad
    :::
    ::::

* Phonetically speak current character:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + double-press {kbd}`,`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    Double-press {kbd}`2` on the numeric keypad
    :::
    ::::

* Speak Unicode value of current character:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + triple-press {kbd}`,`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    Triple-press {kbd}`2` on the numeric keypad
    :::
    ::::

* Next character:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+.`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`3` on the numeric keypad
    :::
    ::::

* Last character on current line:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Ctrl+M`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+1` on the numeric keypad
    :::
    ::::


## Find objects in a window

You can use Orca's Find feature to quickly locate objects that are visible on-screen within the current window.


1. Open the Orca Find dialog:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+[`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Delete` on the numeric keypad
    :::
    ::::

2. A dialog box opens. Enter the search term.

    You can specify several options such as case sensitivity, where the search starts or whether it wraps around the end of the document back to the start.

3. When the search finds a match, Flat Review automatically activates and the matching item or text becomes the current review item.

    Note that the search doesn't modify the focus within the application and it doesn't reposition the caret. If you need to accomplish either, please see Orca's Mouse/Pointer-Related Commands.

4. You can quickly search for the next or previous match:

    * Move flat review to the next instance of a string:

        ::::{tab-set}
        :::{tab-item} Laptop layout
        :sync: orca-laptop

        {kbd}`CapsLock+]`
        :::

        :::{tab-item} Desktop layout
        :sync: orca-desktop

        {kbd}`Insert+Delete` on the numeric keypad
        :::
        ::::

    * Move flat review to the previous instance of a string:

        ::::{tab-set}
        :::{tab-item} Laptop layout
        :sync: orca-laptop

        {kbd}`CapsLock+Ctrl+]`
        :::

        :::{tab-item} Desktop layout
        :sync: orca-desktop

        {kbd}`Insert+Shift+Delete` on the numeric keypad
        :::
        ::::


## What's under the mouse cursor?

With the Mouse Review feature, Orca identifies the object that's visually under the cursor as you move the mouse. If you move the cursor over an accessible object with information to present, Orca presents that object and its information to you. Mouse Review isn't limited to the active window.

Mouse Review is disabled by default because it processes all the changes in the position of the cursor.

* You can enable it permanently:

    Enable the {guilabel}`Speak object under mouse` checkbox on the {guilabel}`General` page of Orca's Preferences dialog.

* You can also set a keyboard shortcut to enable Mouse Review for a short time:

    On the {guilabel}`Key Bindings` page of Orca Preferences, bind the command named {guilabel}`Toggle mouse review mode` to a keyboard shortcut. Then you can enable and disable Mouse Review on an as-needed basis.

:::{note}
You can choose to have Mouse Review always enabled or not and still toggle it on and off by binding and using the Toggle mouse review mode command. It is not necessary to enable it in order to toggle it because settings and keybindings are independent of one another.
:::


## Bookmark an object for later

You can indicate that an object on the screen is of interest and return to it later.

Orca provides several commands which can be used to "bookmark" a given object for the purpose of navigating back to it later.

### Save a bookmark


You can set up to six bookmarks per environment. These can be objects such as widgets within an application or objects on a web page. You can also save bookmarks so that they persist between Orca sessions.

* Save a bookmark to the numbered slot:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Alt` + a number from {kbd}`1` to {kbd}`6`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+Alt` + a number from {kbd}`1` to {kbd}`6`
    :::
    ::::

* Save the defined bookmarks for the application or page:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Alt+B`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+Alt+B`
    :::
    ::::

### Return to a bookmark

You can navigate to the bookmark later, even if you haven't permanently saved the bookmarks associated with your current environment. You can find the bookmark based on its number, or you can browse the saved bookmarks just like Structural Navigation objects.

When you select a bookmark, the exact behavior depends on the current environment. If you are in web content, the caret moves to the bookmark so that you can continue reading. Otherwise, Flat Review activates and the bookmark becomes the current review item.

* Go to a specific, numbered bookmark:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock` + a number from {kbd}`1` to {kbd}`6`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert` + a number from {kbd}`1` to {kbd}`6`
    :::
    ::::

* Go to the previous bookmark for the application or page:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+Shift+B`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+Shift+B`
    :::
    ::::

* Go to the next bookmark for the application or page:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+B`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+B`
    :::
    ::::


