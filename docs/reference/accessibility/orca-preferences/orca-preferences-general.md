
# General preferences

## Keyboard Layout

Specify if you are on a desktop keyboard with a numeric keypad or a laptop keyboard.  
This setting determines the **Orca Modifier** and keyboard shortcuts used for Orca commands.  
**Default value:** `Desktop`

## Present Tooltips

Present information about tooltips on mouse hover.  
This setting does not affect actions that explicitly request tooltips, such as pressing `Ctrl+F1` when an object has focus.  
**Default value:** `Not checked`

## Speak Object Under Mouse

Enable Orca to present information about the object under the mouse pointer when using the **Mouse Review** feature.  
**Default value:** `Not checked`

## Time Format and Date Format

Select how Orca should speak and display the time and date using the combo boxes.  
**Default value:** Use system locale formats

### Navigation in Say All

Orca's **Say All** feature speaks document content from the current location to the end.  
By default, pressing any key interrupts Say All.

If **Enable rewind and fast forward in Say All** is checked, use `Up` and `Down` to move through the document.

If **Enable structural navigation in Say All** is checked, structural navigation commands such as the following can be used:

-  {kbd}`H` /  {kbd}`Shift+H`: next/previous heading
-  {kbd}`P` /  {kbd}`Shift+P`: next/previous paragraph
-  {kbd}`T` /  {kbd}`Shift+T`: next/previous table

**Default value:** `Not checked`

## Announce Contextual Information in Say All

Orca can announce contextual information during Say All (e.g., entering and leaving blockquotes, lists, tables).  
The following options can be configured independently:

- Announce blockquotes 
- Announce forms 
- Announce landmarks
- Announce lists 
- Announce panels
- Announce tables

**Default value:** `Checked`

Note: Similar checkboxes exist on the **Speech** page to control this behavior during navigation.

## Say All By

Choose whether Orca speaks a sentence or a line at a time during Say All.  
**Default value:** `Sentence`