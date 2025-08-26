---
sequential_nav: both
---

(get-started-with-the-screen-reader)=
# Get started with the screen reader

Ubuntu Desktop comes with the Orca screen reader. Orca is an open-source tool that reads text on your screen and lets you navigate the user interface using keyboard commands.

Let's explore how to start the screen reader and use the Ubuntu Desktop interface without relying on vision.


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


## Ask for the time and date

Let's try an Orca command now. 

* To let Orca tell you the current time, press Orca modifier + {kbd}`T`. That's {kbd}`CapsLock+T` if you have the laptop layout, or {kbd}`Insert+T` on the desktop layout.

    Orca tells you the current hour, minute and second.

* To find out today's date, double-press {kbd}`T` in the same keyboard shortcut. Use {kbd}`CapsLock+T+T` on the laptop layout, or {kbd}`Insert+T+T` on the desktop layout.

    Orca says the date only as numbers. For example, if you hear "zero seven thirty two thousand twenty five", that represents July 30, 2025.
    

## Check your internet connection

In the following sections, we'll cover some basic Orca controls in a web browser. Before we launch the web browser, let's ensure that the internet connection is on. In the process, we're going to explore how to control the desktop interface from the keyboard.

Network settings are available in the top bar. Press {kbd}`Ctrl+Alt+Tab` to cycle through the areas of the user interface. Notice that you can also focus the Dash, which contains application launchers, and the desktop icons frame. Select "Top Bar" and release the keys.

Now, you can browse the elements in the top bar. Press {kbd}`Tab` until you hear "System Menu".

Press {kbd}`Enter` to activate the menu and press {kbd}`Down` to descend into the quick settings menu.

Inside the menu, you can again use {kbd}`Tab` to cycle through the menu items. You'll hear items such as the battery percentage, a screenshot button, a settings button, a screen lock button and a power off button.

Eventually, you might arrive to the {guilabel}`Wired` toggle button. If Orca says that the button is "pressed", you're connected to wired network.

You might also encounter the {guilabel}`Wi-Fi` toggle button. If it's "pressed", it means that the wireless subsystem is enabled. However, you might not be connected to any wireless network. Let's find out:

1. Press {kbd}`Tab` again and go to the "Open Menu" button.
2. Activate it and press {kbd}`Down` to descend into the list of wireless networks.
3. If you're connected to a wireless network, it's the first one on the list. Orca tells you the network name, security, the signal strength, and says "checked".

    If you're not connected to any wireless network, Orca doesn't say "checked". In that case, browse the network list using {kbd}`Up` and {kbd}`Down`. When you find your network, activate it, and if asked, enter the password.


## Launch Firefox

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

:::{note}
You might be using multiple keyboard layouts or a different keyboard layout than your interface language. In that case, Orca commands might follow a different keyboard layout than expected.

If some Orca commands work and others don't, try entering them as if another keyboard layout was active.
:::

## Read the application content

Let's read some web pages. We'll start with a simple one.

Enter [`example.org`](https://example.org) in the Firefox address bar.

To read the entire page content, press Orca modifier + {kbd}`;`. The page contains one heading, two paragraphs and one link.

Let's compare that with another way to read the content of applications: Flat Review. To read the whole window, press Orca modifier and double-press {kbd}`;`. Orca starts reading the elements of the Firefox window first before it gets to the web page.

Another common way to read text is caret navigation. Press {kbd}`F7` and confirm using {kbd}`Alt+Y`. Use the arrow keys to move your text cursor (caret) on the web page:

* Pressing {kbd}`Left` and {kbd}`Right` reads the text by letter.
* Pressing {kbd}`Ctrl+Left` and {kbd}`Ctrl+Right` reads the text by word.
* Pressing {kbd}`Up` and {kbd}`Down` reads the text by line.

Try placing your cursor roughly to the middle of the document. When you press Orca modifier + {kbd}`;` to read the document, it starts reading from your current position to the end of the page.


## Focus elements

The [`example.org`](https://example.org) page contains one link. Press {kbd}`Tab` to switch focus to it.

As you press {kbd}`Tab` again, the focus moves through interactive elements in the Firefox interface until it cycles back to the link.

When you focus the link, Orca tells you where the link leads. To repeat the information, press Orca modifier + {kbd}`Enter`. The is the *basic Where Am I* command. To hear more information, press Orca modifier and double-press {kbd}`Enter`. This is the *detailed Where Am I* command.

Press {kbd}`Enter` to activate the focused element. In this case, follow the link.


## Browsing the web using Structural Navigation

We've opened a longer, more complex web page: [Example Domains](https://www.iana.org/help/example-domains).

If you press Orca modifier + {kbd}`;` to hear the whole page, you'll notice that you might not be interested in every part. Press {kbd}`Escape` to stop reading.

With Structural Navigation, you can read the page by headings, links, lists and other elements:

* To get a list of **headings** on this page, press {kbd}`Alt+Shift+H`.

    Move through the headings using {kbd}`H` and {kbd}`Shift+H`.

* To get a list of **links** on this page, press {kbd}`Alt+Shift+K`.

    Move through the links using {kbd}`K` and {kbd}`Shift+K`.

* To get a list of **lists** on this page, press {kbd}`Alt+Shift+L`.

    Move through the lists using {kbd}`L` and {kbd}`Shift+L`.

* To get a list of **paragraphs** on this page, press {kbd}`Alt+Shift+P`.

    Move through the paragraphs using {kbd}`P` and {kbd}`Shift+P`.

Orca supports many more Structural Navigation commands. You can find a complete reference at {ref}`orca-structural-navigation-commands`.

:::{note}
If a form field or another kind of text entry is focused, Structural Navigation commands don't work because you're typing text. To re-enable Structural Navigation, press Orca modifier + {kbd}`Z`. Alternatively, leave the field using {kbd}`Tab`.
:::


## Other applications

In other applications, you can use most of the commands that we've covered:

* Usually, you want to use {kbd}`Tab` to browse the interactive elements.

* In text editors, caret navigation works by default. In some other applications like document viewers, you can enable it using {kbd}`F7`.

* Try using the commands to read the document and read the window: Orca modifier + {kbd}`;` and Orca modifier + {kbd}`;+;`. In some applications, such as text editors and other text entries, the commands might not work.

* Only a couple of application support Structural Navigation: Firefox, LibreOffice, Thunderbird and Pidgin. In LibreOffice, you can only use Structural navigation to browse tables in Writer. In editable documents, enable Structural navigation using Orca modifier + {kbd}`Z`.

If you experience difficulty with some applications, you can find tips in [Improve screen reader usability](improve-screen-reader-usability).


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

