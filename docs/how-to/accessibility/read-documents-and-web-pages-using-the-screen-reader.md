(read-documents-and-web-pages-using-the-screen-reader)=
# Read documents and web pages using the screen reader

## Read documents using caret mode

In caret mode, also known as caret browsing or caret navigation, you navigate a document using the text cursor (caret). You move the cursor using the arrow keys. As you navigate within the text of the document, Orca presents your current location.

Enable caret navigation:

* Applications with text input, such as text editors and word processors, enable caret navigation by default. The caret is the text cursor that you use to enter text in the window.
* In many GNOME applications and in web browser such as Firefox and Chrome, you can enable caret navigation by pressing {kbd}`F7`.
* For other applications, consult their documentation.

Read the document using caret navigation:

* Use {kbd}`Left` and {kbd}`Right` to move and read by character.
* Use {kbd}`Ctrl+Left` and {kbd}`Ctrl+Right` to move and read by word.
* Use {kbd}`Up` and {kbd}`Down` to move and read by line.
* Use {kbd}`Shift` in combination with the previous commands to select and unselect text.

To read, spell, and obtain the Unicode value for the current text, or to read the whole document, refer to {ref}`orca-examine-a-window`.


## Examine text formatting

The term "text attributes" refers to all of the font, style, alignment, and other formatting associated with a given character or series of characters.

### Obtaining Formatting Information

When you press Orca Modifier+F, Orca will speak known text attribute information about an object. In addition, Orca will optionally indicate text attributes in braille by "underlining" them as you navigate a document.

Because the number of text attributes is large, and not everyone cares about every attribute, the Text Attributes page of the preferences dialog allows you to customize which text attributes Orca will present in speech, along with the order in which they should be presented, and which ones Orca will indicate in braille.

Because the Text Attributes page is also part of the application-specific settings, you can customize text attribute presentation on an as-needed basis for each application you use.

### Identifying Misspelled Words

Most applications and toolkits indicate that a word is misspelled by underlining that word with a red, squiggly line. The presence of this line is typically exposed to assistive technologies as a text attribute. As a result, you will find spelling errors amongst the text attributes you can choose. By default, the spelling error attribute is enabled for both speech and braille and will therefore be presented along with any other attributes whose indication you have enabled.

In addition to accessing the presence of spelling errors as a text attribute, if you have key echo and/or word echo enabled and type a word which is misspelled, when the spelling error indication appears, Orca will announce "misspelled" so that you can immediately go back and correct the error.

Finally, when you are navigating within a document and the caret moves into a word which is misspelled, Orca will announce the presence of the spelling error.


## Navigate the document structure

Orca's Structural Navigation feature allows you to navigate amongst elements in a document. The types of elements by which you can navigate include:

* Headings and other text blocks
* Form controls
* Links
* Lists and list items
* Landmarks, separators, and anchors
* Tables and table cells

A full list of individual elements and their associated keybindings can be found in Structural Navigation Commands.

### Supported Applications

Currently, Structural Navigation is fully implemented for web content, including the help content you are reading now. Orca's Structural Navigation support for table cells has also been implemented for OpenOffice Writer and LibreOffice Writer. Implementing the remainder of the Structural Navigation objects to these office suites requires changes to be made by their respective developers. Implementing any Structural Navigation features within Evince will require a similar effort on the part of its developers.
Don't Forget To Toggle Structural Navigation On!

Depending on where you are, it may be necessary for you to explicitly toggle Structural Navigation on before you can use it.

#### When Toggling Structural Navigation On Is Required

In web pages, explicitly toggling Structural Navigation on is generally unnecessary because your interaction with the document largely consists of reading its content. Thus there is no question as to whether the 'H' you just pressed was meant to be a writing command or a navigation command.

On the other hand, in editable documents such as those found in OpenOffice and LibreOffice, it is far more difficult for Orca to accurately predict what you expect to have happen as a result of pressing 'H'. Therefore, before you can use any Structural Navigation command in an editable document, you must first toggle Structural Navigation on by pressing Orca Modifier+Z. When you are finished navigating and ready to resume writing, press Orca Modifier+Z again to toggle Structural Navigation off.

### Available Settings

In addition to the aforementioned commands, Orca has a number of configurable options available specifically for applications in which there is structural navigation support.
Configuring Structural Navigation

1. Give focus to an application for which Orca has Structural Navigation support.
2. Get into the Orca Preferences dialog box for the current application by pressing Ctrl+Orca Modifier+Space.
3. Navigate to the last page of the dialog box which should be named according to the name of your current application.
4. Examine and change the settings as you see fit.
5. Press the OK button.


## Read tables

Orca provides several features specifically designed to improve access to tables found in web pages and other documents: configurable cell versus row reading, Structural Navigation and Dynamic Headers.

### Cell Versus Row Reading

Consider the process of examining the list of messages in your Inbox. In order to have Orca announce the sender, subject, date, and presence of attachments you would need Orca to speak the row. On the other hand, when navigating amongst rows in a spreadsheet, hearing the full row may not be desired if for no other reason than the sheer number of cells in each row. Thus in that case, you would want Orca to only speak the cell with focus. Similar situations occur in document tables.

Orca allows you to customize whether only the cell should be read, or if the full row should be, for GUI tables, document tables, and spreadsheets. Because these settings are independent of one another, you do not have to choose one table reading mode to fit multiple types of tables.

You can set each of Orca's table reading preferences Orca wide as well as on an application-by-application basis. How to do each is described in the guide on Orca's preferences dialogs. The settings can be found on the Speech page.

Lastly, there is also an Orca command which allows you to toggle cell versus row reading on the fly for the currently-active table:

::::{tab-set}
:::{tab-item} Laptop layout
:sync: orca-laptop

{kbd}`CapsLock+F11`
:::

:::{tab-item} Desktop layout
:sync: orca-desktop

{kbd}`Insert+F11`
:::
::::

### Structural Navigation

Orca's table Structural Navigation commands make it possible for you to quickly locate tables, jump immediately to a table's first or last cell, and move to the next cell in any direction.

As you navigate amongst and within tables using Structural Navigation, Orca will announce additional details to help you understand your position, such as the dimensions of the table you just entered and the fact that you have reached the edge of the table in the direction you are moving.

In addition, Orca provides configurable presentation options which work in conjunction with Structural Navigation and allow you to control whether or not cell coordinates are presented, multiple cell spans are indicated, and cell headers are announced.

:::{note}
Don't Forget To Toggle Structural Navigation On!

Depending on where you are, it may be necessary for you to explicitly toggle Structural Navigation on before you can use it. To learn more, read when toggling Structural Navigation on is required.
:::

### Dynamic Headers

Many of the tables you will encounter while reading have cells which serve as the header for a row or a column. Whether or not the creator of that table correctly marked those cells as headers is hard to say. In many cases, the text was simply formatted to be larger and/or bold. And even if the table is correctly marked up, that is no guarantee that the application or toolkit exposes that text as header information to assistive technologies. Orca's Dynamic Header support makes it possible to overcome these challenges.

#### Setting Column Headers

1. Move to the row which contains all of the column headers.
2. Tell Orca that the current row is the one with the headers:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+R`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+R`
    :::
    ::::

#### Setting Row Headers

1. Move to the column which contains all of the row headers.
2. Tell Orca that the current column is the one with the headers:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+C`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+C`
    :::
    ::::

Having set either the column headers or the row headers, you should find that as you navigate amongst the cells, Orca will present each header that has changed. Or to put it another way, Orca will not present the column header over and over again as you move up or down within the current column. Likewise, it will not present the row header over and over again as you move left or right within the current row. However, if you change rows and there are row headers, the header associated with the new row will be presented. And if you change columns and there are column headers, the header associated with the new column will be presented.

To clear headers, simply double-click the command you used to set them. Thus double-clicking Orca Modifier+R tells Orca there are no column headers. Double-clicking Orca Modifier+C tells Orca there are no row headers.


## Fill out forms

When interacting with web pages and other documents using Orca, you are interacting with the document itself; not a buffered copy of that document. Orca's browse and focus modes let you switch between reading and filling out forms.

### Navigating Amongst Form Fields

To navigate amongst form fields, you have several options:

* Use {kbd}`Tab` and {kbd}`Shift+Tab` to navigate amongst focusable objects, regardless of type.
* Use Orca's structural navigation commands for forms.
* Depending on the form and the application, you may also be able to use the arrow keys to navigate to a given form field.

:::{note}
In order to use Orca's caret navigation or structural navigation commands to navigate to a form field, you must be in browse mode. If you are in focus mode, you can switch to browse mode by pressing Orca Modifier+A.
:::

### Exiting Form Fields

To exit a form field, you have several options:

* Use {kbd}`Tab` and {kbd}`Shift+Tab` if you wish to leave the currently-focused form field and move to the next/previous focusable object, regardless of type.
* Use Orca's structural navigation commands for forms to move to the next or previous form field.
* Depending on the form and the application, you may also be able to use the arrow keys to navigate out of a given form field.

:::{note}
In order to use Orca's caret navigation or structural navigation commands to exit a form field, you must be in browse mode. If you are in focus mode, you can switch to browse mode by pressing Orca Modifier+A.
:::


## Interact with live regions

A live region is a dynamically-updated portion of a web page, such as a table of sports statistics, a list of current stock prices, a log from a chat, or an alert displayed by the page you are reading. While live regions appear quite frequently, fully accessible web pages with live regions are encountered less often. This problem is actively being addressed by a number of organizations.

### Live Region Politeness Levels

Live regions have an associated "politeness" level which is set by the author as a means to convey the importance of the information and to suggest when users should be informed by their assistive technology of updates made within that region. Live regions can be "off", "polite", or "assertive" to the point of being "rude."

### Orca's Support for Live Regions

Because you might not agree with the politeness level specified by the author whose page you are viewing, Orca provides a number of live region commands which allow you to modify the level of any or all of the regions on a page. In addition, you can:

* Turn live region support on or off
* Jump to the next and previous live region spatially
* Jump to the last live region which presented information
* Review the last nine live region messages which were presented

