(read-documents-and-web-pages-using-the-screen-reader)=
# Read documents and web pages using the screen reader

(orca-read-documents-using-caret-mode)=
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


(orca-navigate-the-document-structure)=
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

In editable documents, such as those in **LibreOffice Writer** or an **online text editor**, pressing letters on the keyboard types text in the editor. Enable Structural Navigation to use letters as navigation shortcuts instead:

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

Orca provides several features to access tables on web pages and in other documents.

### Read the cell or the row

Consider the list of **messages in your Inbox**. To hear the sender, subject, date and presence of attachments, you want Orca to **speak the row**.

On the other hand, consider the **rows in a spreadsheet**. You might not want to hear the full row because of the large number of cells in each row. In that case, you want Orca to only **speak the cell with focus**. Similar situations occur in document tables.

You can switch between cell and row reading for the current table:

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

You can customize whether Orca reads the cell or the full row by default. You can also choose different table reading modes for each type of table and for specific applications. To edit the options, go to the {guilabel}`Speech` page of Orca preferences.

### Structural Navigation

With Structural Navigation commands, you can locate tables, jump to the first or last cell and move to the next cell in any direction.

As you navigate the table, Orca announces the details about your position, such as the dimensions of the table or that you have reached the edge of the table.

For details, refer to {ref}`orca-navigate-the-document-structure`.

### Mark a row or column as a header

Many tables have incorrectly marked headers. A row or column often serves as a header but it only uses bold or large text instead of semantic markup. In other cases, the header might be correct but the application or the toolkit don't provide the information to the screen reader.

In those cases, you can manually mark a row or column as a header using the Dynamic Header feature.

#### Set a row as a header

Tell Orca that the current row is the one with the headers:

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

#### Set a column as a header

Tell Orca that the current column is the one with the headers:

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

#### Reset the custom header

To clear headers, double-press the command that you used to set them. This removes all custom row headers or column headers.


## Fill out forms

In browse mode, you can read forms. In focus mode, you can fill out form fields.

### Read or write

Use the following shortcut to switch between the modes:

::::{tab-set}
:::{tab-item} Laptop layout
:sync: orca-laptop

{kbd}`CapsLock+A`
:::

:::{tab-item} Desktop layout
:sync: orca-desktop

{kbd}`Insert+A`
:::
::::

To enable **sticky focus mode**, double-press the shortcut. To enable **sticky browse mode**, triple-press the shortcut.

### Browse form fields

In **browse** and **focus mode**, you can browse all focusable objects using {kbd}`Tab` and {kbd}`Shift+Tab`. After the last form field, you exit the form.

In **browse mode**:

* To navigate to a specific form field, use Structural Navigation commands for {ref}`orca-structural-navigation-commands-forms`.

* To leave the form and navigate to another object, use {ref}`orca-structural-navigation-commands`.

* In certain forms and applications, you can also use {ref}`caret mode <orca-read-documents-using-caret-mode>`.


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

