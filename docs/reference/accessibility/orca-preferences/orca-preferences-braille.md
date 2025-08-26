
# Braille preferences

## Enable braille support

Toggles braille display integration. Orca handles BrlTTY absence gracefully.  

**Default value:** Not checked

:::{note}
You must restart Orca after configuring BrlTTY.
:::

## Enable word wrap

Wraps only full words on the braille display.  

**Default value:** Not checked

## Enable contracted braille

Enable support via `liblouis`.  Choose the desired translation table.  

**Default value:** Not checked

## Abbreviated role names

For example, "slider" equals to "sldr".  

**Default value:** Not checked

## Disable end of line symbol

Disables presentation of `$l` at the end of lines.  

**Default value:** Not checked

## Verbosity

Controls how much info is shown in braille:

**Verbose** 
: includes role names and keyboard shortcuts  

**Brief**
: omits tole names and keyboard shortcuts  

**Default value:** Verbose

## Selection and hyperlink indicators

Indicate selected text and links with:

- **Dots 7 and 8** (default)
- **Dot 7**
- **Dot 8**
- **None**

## Text attribute indicators

Enabled and configured on the **Text Attributes** page.

## Flash message settings

Temporary messages displayed in braille.

### Enable flash messages

Toggle display of braille flash messages.  
**Default value:** Checked

### Messages are detailed

Enable longer messages, for example, "Key echo set to word."  

**Default value:** Checked

### Messages are persistent

Keeps messages on screen until overwritten.  

**Default value:** Not checked

### Duration (secs)

Sets time before message disappears. Ignored if persistence is enabled.  

**Default value:** 5
