(navigate-the-screen-using-the-screen-reader)=
# Navigate the screen using the screen reader

## Where am I?

Orca provides context-sensitive commands that describe the active window and the active object on the screen.

### Window information

Find out which window is active.

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

### Basic information

You can ask Orca for the _basic Where Am I_ with any object on the screen. For most widgets, Orca at least tells you the label or name, the type or role of the widget, and the mnemonic or accelerator key if they exist.

For example, in tables, basic Where Am I gives you details about the table cell that you are in. In text, it presents the current line along with any text which is selected.

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

### Detailed information

Only certain objects provide the _detailed Where Am I_ information. These objects contain a lot of information that you may wish to know, but only on demand.

For example, if you are in the spell checker of an application where Orca provides enhanced support, the basic Where Am I repeats the spelling error. The detailed Where Am I presents the full details of the error. The detailed Where Am I also tells you the position in a progress bar, the status of check boxes and radio buttons, the children in a tree object, the type of a link or the cell coordinates in a table.

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


(orca-examine-a-window)=
## Examine a window

With the **Flat Review** feature, you can review the text and widgets of the active window. In this mode, Orca treats the window as a two-dimensional sheet of text. It browses the objects in the foreground, ignoring widget hierarchy or other logical grouping within the window. It can't access window elements that are currently off-screen.

You can navigate the "flattened" content by line, by word, by character, and by object. You can also perform a left-click or right-click on the selected object.

When you enter Flat Review mode, it captures the state of the window at that moment. If the content of the window changes, Flat Review doesn't update automatically. You can refresh the Flat Review context by toggling Flat Review off and back on.

If you use the application's navigation commands to move the caret or to give focus to another object, you automatically leave Flat Review. 

* Toggle Flat Review (refreshes the window content):

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

* Review the current item or widget:

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


### Review the window by line

* First line (the "home" position):

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

### Review the window by word

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

### Review the window by character

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

* Speak the Unicode value of the current character:

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

* Last character on the current line:

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

Orca Find is based on the {ref}`Flat Review <orca-examine-a-window>` feature.

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

## Keyboard navigation shortcuts

For keyboard shortcuts that launch applications, switch between desktop elements and navigate desktop menus, refer to {ref}`navigate-the-interface-using-the-keyboard`.

