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

Let Orca speak the text attributes of the current object, such as the font, style, alignment, and other formatting associated with the given characters:

::::{tab-set}
:::{tab-item} Laptop layout
:sync: orca-laptop

{kbd}`CapsLock+F`
:::

:::{tab-item} Desktop layout
:sync: orca-desktop

{kbd}`Insert+F`
:::
::::

### Preferences
 
The number of text attributes is large. You can customize which text attributes Orca presents in speech, along with the order in which Orca lists them. Optionally, Orca can indicate text attributes in braille by "underlining" them as you navigate a document. Go to the {guilabel}`Text Attributes` page of the Orca preferences dialog to change these settings.

You can also customize text attribute presentation for each application that you use in the application-specific settings.

## Identify misspelled words

You can learn about spelling issues in several ways:

* When you examine text formatting, Orca also announces spelling issues as one of the text attributes:

    ::::{tab-set}
    :::{tab-item} Laptop layout
    :sync: orca-laptop

    {kbd}`CapsLock+F`
    :::

    :::{tab-item} Desktop layout
    :sync: orca-desktop

    {kbd}`Insert+F`
    :::
    ::::

    Orca recognizes the spelling issue by reading the underline formatting that applications use to mark errors.

* Enable key echo or word echo. When you misspell a word, Orca announces "misspelled" so that you can immediately go back and correct the error.

* When you move the caret into a word that's misspelled, Orca announces the presence of the spelling error.

* Perform detailed Where Am I to learn more details about the spelling issue:
    
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


## Navigate the document structure

The Structural Navigation feature enables you to browse elements in a document. The types of elements by which you can navigate include:

* Headings and other text blocks
* Form controls
* Links
* Lists and list items
* Landmarks, separators and anchors
* Tables and table cells

Structural Navigation is available in the following environments:

* On **web pages**, you can navigate the full range of elements.
* In **LibreOffice Writer** and OpenOffice Writer, you can navigate table cells.

### Navigate a web page

On web pages, you usually read the content without editing it. You can use the Structural Navigation commands directly. Refer to {ref}`orca-structural-navigation-commands`.

### Navigate elements in a text editor

In editable documents, such as those in **LibreOffice Writer** or an **online text editor**, pressing letters on the keyboard types text in the editor.

Enable Structural Navigation to use letters as navigation shortcuts:

::::{tab-set}
:::{tab-item} Laptop layout
:sync: orca-laptop
    
{kbd}`CapsLock+Z`
:::
    
:::{tab-item} Desktop layout
:sync: orca-desktop

{kbd}`Insert+Z`
:::
::::

Browse elements using Structural Navigation commands:

* On web pages, refer to {ref}`orca-structural-navigation-commands`.
* In Writer, you can only use the commands for {ref}`orca-structural-navigation-commands-tables`.

To go back to writing, disable Structural Navigation using the same shortcut that enables it.


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

