(getting-started-with-the-screen-reader)=
# Getting started with the screen reader

Ubuntu Desktop comes with the Orca screen reader. Orca is an open-source tool that reads text on your screen and lets you navigate the user interface using keyboard commands.

Let's explore how to start the screen reader and use Ubuntu Desktop without relying on vision to control the interface.


<!--
## Notes

start Orca with Alt+F2 -> orca. stop it with killall orca.

- basic Orca commands

with the Czech layout, Shift+1 (which types 1) is actually interpreted as Shift+1 by Orca, which means navigating to the previous level 1 heading. to go to the next heading, you press + (no Shift + 1).

I couldn't focus a search field to enter a term in it, even with focus mode :-/

This toggles between two sets of key combinations, suitable for either narrow notebook keyboards or wider external keyboards with a dedicated numeric keypad. The keys on this keypad will be prefixed “KP”, KP Plus, for example, will refer to the Plus key on the keypad. Note that the numeric lock must be deactivated

When Orca is running it replaces many of your normal keyboard letters with commands for navigating the document by structure (more on that below). You can toggle this behavior with Orca Modifier+z.
...
When Orca is running, it replaces a large number of normal keyboard letters with commands for navigating the document according to its structure, as shown below. You can disable this behavior with the shortcut Orca Key Z.

- https://help.gnome.org/users/orca/stable/howto_toggling_caps_lock.html.en
-->

## Enable the screen reader

First, close all windows. It's best to work on a clean desktop so that certain applications don't capture your keyboard commands.

To start the screen reader, press {kbd}`Super+Alt+S`. What we call the {kbd}`Super` key is the key with the Windows logo on PC keyboards, or the {kbd}`Cmd` key on Apple keyboards.

Orca immediately announces "screen reader on".

You can later turn off the screen reader using the same keyboard shortcut. For now, keep it enabled.


## Determine your keyboard layout

Orca uses different keyboard commands depending on the size and layout of your keyboard. Before you learn about Orca commands, you need to find out which layout Orca is using.

1. Press {kbd}`Alt+F2`. The {guilabel}`Run a command` dialog opens and Orca announces it. If the dialog doesn't open, you might need to press the {kbd}`Fn` key with {kbd}`F2`.

2. Type `orca --setup` into the dialog and press {kbd}`Enter`.

    The {guilabel}`Screen Reader Preferences` window opens. The {guilabel}`General` tab is active.

3. Press {kbd}`Tab`. Focus moves to the first element in the window, which is a keyboard layout selector.

    Orca announces what your layout is: laptop or desktop.

4. For now, close the preferences window using {kbd}`Alt+F4`. 


## The Orca modifier on your keyboard

Most of the keyboard commands that control Orca start with the *Orca modifier*. It's a key that acts like {kbd}`Shift` or {kbd}`Ctrl`:

* With the laptop layout, you use {kbd}`CapsLock` as your Orca modifier.

    You might encounter issues with the {kbd}`CapsLock` modifier. Sometimes, the system treats it as plain {kbd}`CapsLock` when it should act as the Orca modifier, or the other way around.

    In that case, toggle {kbd}`CapsLock` by double-pressing it. Alternatively, press {kbd}`CapsLock+Backspace`, which tells Orca to ignore the next key, and then press {kbd}`CapsLock`.

* With the desktop layout, it's {kbd}`Insert`.

    Make sure to disable your {kbd}`NumLock`. Many commands on the desktop layout use keys on the numeric keypad, and they only work when {kbd}`NumLock` is disabled.

<!--
Re-open Orca preferences using Orca modifier + {kbd}`Space`:

* With the laptop layout, that's {kbd}`CapsLock+Space`.
* With the desktop layout, it's {kbd}`Insert+Space`.

The {guilabel}`Screen Reader Preferences` window opens again.
-->



## Ask for the time and date

Let's try an Orca command now. 

* To let Orca tell you the current time, press Orca modifier + {kbd}`T`. That's {kbd}`CapsLock+T` if you have the laptop layout, or {kbd}`Insert+T` on the desktop layout.

    Orca tells you the current hour, minute and second.

* To find out today's date, double-press {kbd}`T` in the same keyboard shortcut. Use {kbd}`CapsLock+T+T` on the laptop layout, or {kbd}`Insert+T+T` on the desktop layout.

    Orca says the date only as numbers. For example, if you hear "zero seven thirty two thousand twenty five", that represents July 30, 2025.
    

## Basic navigation

Let's try opening an application and learning where we are. In this example, we'll use the Firefox web browser.

Start Firefox:

1. Press {kbd}`Super` to open the applications overview and search.

2. Start typing _Firefox_. Type slowly letter by letter and listen to what Orca says.

    Orca announces which application currently matches the search term. When you type "f", Firefox might already be the current match.

3. When Firefox is the active search result, press {kbd}`Enter` to open Firefox.

    When Firefox opens, Orca says: "Mozilla Firefox frame".

In Firefox, open a new tab so that we're on the same page: press {kbd}`Ctrl+T`. Orca announces: "New Tab page tab".

Let's explore where we are:

* Ask for the window title. With the laptop layout, press {kbd}`CapsLock+/`. With the desktop layout, press {kbd}`Insert+Enter` on the numeric keypad.

    Orca announces: "Mozilla Firefox".

* Ask about the active element in the window. Press Orca modifier + {kbd}`Enter`. This is also called the *basic Where Am I*.

    Right now, the active element should be the address bar in the new tab. Orca announces: "Navigation toolbar" and some additional details.

Go to a sample page.

* Say All

* Flat Review?

* Tab

* Caret navigation

Basic GNOME keyboard shortcuts.


## Navigate the panel

how-to/accessibility/navigate-the-interface-using-the-keyboard/#navigate-the-panel


## Reading text documents

Maybe using Firefox as example is the safest option.

use arrows and ctrl+arrows. use Tab for focusable elements. use Say All to read the whole document.

read using caret mode. line up/down actually reads the whole line

Orca’s Say All command speaks document content from your present location to the end of the document.


## Browsing the web

Open Firefox and use structural navigation

On web pages, you don't usually want to read the whole document. You want structural navigation instead.

In order to use the structural navigation commands to exit a form field, you must be in browse mode. If you are in focus mode, you can switch to browse mode by pressing Orca Modifier+A.

structural navigation on the web. in editable documents, you have to activate it first.

- Moving by header
- Moving by landmarks
  - landmarks are elements like page header, search bar, main content.
- Moving by links
- Moving through lists

- Firefox -> Ctrl+K to focus the search bar -> enter search terms -> Alt+Shift+K to get the list of links -> Enter to follow a link -> Alt+Shift+H to get the headings
- deactivate focus mode to leave a focused form
- Orca [structural navigation] supports the following applications: Firefox, LibreOffice, Thunderbird, Pidgin


## Learn more

Orca has a learning mode where keys and commands only tell you what their function is.

To enter learning mode, press Orca modifier + {kbd}`H`. Try various Orca commands that you remember. Try pressing other keys with your Orca modifier. Each time, Orca tells you what the command does.

Press {kbd}`F2` to open a list of Orca keyboard commands. You can browse the list using {kbd}`Up` and {kbd}`Down`.

To exit learning mode, press {kbd}`Escape`.

For more guidance, go to the following pages:

* {ref}`navigate-the-screen-using-the-screen-reader`
* {ref}`read-documents-and-web-pages-using-the-screen-reader`
* {ref}`read-screen-in-braille`
* {ref}`navigate-the-interface-using-the-keyboard`
* {ref}`keyboard-navigation-shortcuts`
* {ref}`improve-screen-reader-usability`


