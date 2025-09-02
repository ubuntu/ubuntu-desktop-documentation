
# General preferences

## Keyboard layout

Specify if you are on a desktop keyboard with a numeric keypad or a laptop keyboard.  
This setting determines the **Orca Modifier** and keyboard shortcuts used for Orca commands.  

**Default value:** Desktop

## Present tooltips

Present information about tooltips on mouse hover.  
This setting does not affect actions that explicitly request tooltips, such as pressing {kbd}`Ctrl+F1` when an object has focus.  

**Default value:** Not checked


<!--
This feature doesn't work at all and leaves Orca in a stuck, unusable state. Commenting out for now.

Mouse commands don't work either but at least they don't permanently disable Orca:
https://help.gnome.org/users/orca/stable/commands_mouse.html.en

## Speak object under mouse

Enable Orca to present information about the object under the mouse pointer when using the Mouse Review feature, see {ref}`orca-mouse-review`.  

**Default value:** Not checked
-->

## Time format and date format

Select how Orca should speak and display the time and date using the combo boxes.  

**Default value:** Use system locale formats

### Navigation in Say All

Orca's **Say All** feature speaks document content from the current location to the end.  

By default, pressing any key interrupts **Say All** .

If **Enable rewind and fast forward in Say All** is checked, use `Up` and `Down` to move through the document.

If **Enable structural navigation in Say All** is checked, structural navigation commands such as the following can be used:

-  {kbd}`H` /  {kbd}`Shift+H`: next/previous heading
-  {kbd}`P` /  {kbd}`Shift+P`: next/previous paragraph
-  {kbd}`T` /  {kbd}`Shift+T`: next/previous table

**Default value:** Not checked

## Announce contextual information in Say All

Orca can announce contextual information during Say All (e.g., entering and leaving blockquotes, lists, tables).  
The following options can be configured independently:

- Announce blockquotes 
- Announce forms 
- Announce landmarks
- Announce lists 
- Announce panels
- Announce tables

**Default value:** Checked

:::{note}
Similar checkboxes exist on the for {ref}`orca-speech-preferences` to control this behavior during navigation.
:::

## Say All By

Choose whether Orca speaks a sentence or a line at a time during **Say All** .  

**Default value:** Sentence