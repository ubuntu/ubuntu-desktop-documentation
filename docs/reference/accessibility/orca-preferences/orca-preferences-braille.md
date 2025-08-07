
# Braille preferences

## Enable Braille Support

Toggles braille display integration. Orca handles BrlTTY absence gracefully.  
**Default value:** `Not checked`

*Note:* Restart Orca after configuring BrlTTY.

## Enable Word Wrap

Wraps only full words on the braille display.  
**Default value:** `Not checked`

## Enable Contracted Braille

Enable support via `liblouis`.  
Choose the desired translation table.  
**Default value:** `Not checked`

## Abbreviated Role Names

E.g., "slider" → "sldr"  
**Default value:** `Not checked`

## Disable End of Line Symbol

Disables presentation of `$l` at the end of lines.  
**Default value:** `Not checked`

## Verbosity

Controls how much info is shown in braille:

- **Verbose** — includes role names and keyboard shortcuts  
- **Brief** — omits them  
**Default value:** `Verbose`

## Selection and Hyperlink Indicators

Indicate selected text and links with:

- **Dots 7 and 8** *(default)*
- **Dot 7**
- **Dot 8**
- **None**

## Text Attribute Indicators

Enabled and configured on the **Text Attributes** page.

## Flash Message Settings

Temporary messages displayed in braille.

### Enable Flash Messages

Toggle display of braille flash messages.  
**Default value:** `Checked`

### Messages Are Detailed

Longer messages like "Key echo set to word."  
**Default value:** `Checked`

### Messages Are Persistent

Keeps messages on screen until overwritten.  
**Default value:** `Not checked`

### Duration (secs)

Sets time before message disappears. Ignored if persistence is enabled.  
**Default value:** `5`
