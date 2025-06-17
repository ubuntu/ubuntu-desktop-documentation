# Overview of assitive solutions

## Screen readers 

### Orca

Orca is screen reading software for vision impaired and blind users. 

Orca is preinstalled on Ubuntu Desktop and can be enabled and used without any additional configurations. To learn how to tart using Orca, go to [Read the screen aloud](../../how-to/accessibility/read-screen-aloud.md).

### BRLTTY

The Orca screen reader can display the user interface on a refreshable Braille display. It uses the BRLTTY service, which provides access to the Linux console for a blind person using a refreshable Braille display. 

As Orca, BRLTTY is preinstalled and can be enabled and used without any additional configurations, see [Read the screen in Braille](../../how-to/accessibility/read-screen-in-braille.md).

### Yasr

Yasr is a a general-purpose console screen reader. The name Yasr is an acronym that can stand for either "Yet Another Screen Reader" or "Your All-purpose Screen Reader".

Yasr works by opening a pseudo-terminal and running a shell, intercepting all input and output. It looks at the escape sequences being sent and maintains a virtual window that contains what it believes to be on the screen.

Yasr must be installed manually. To learn more about the tool and its features, consult [Yasr GitHub repository](https://github.com/mgorse/yasr). 

## On-screen keyboards

### GNOME on-screen keyboard

Ubuntu Desktop comes with a GNOME on screen keyboard preinstalled. To start using it, see [How to use an on-screen keyboard](../../how-to/accessibility/use-an-on-screen-keyboard).

### Onboard

Onboard is an onscreen keyboard useful for everybody that cannot use a hardware keyboard, for example Tablet-PC users or mobility impaired users. It has been designed with simplicity in mind.

Onboard must be installed manually. To learn more about the tool and its features, consult [Onboard GitHub repository](https://github.com/dr-ni/onboard). 

## Non-standard input methods

### Dasher

Dasher is an text-entry interface driven by natural continuous pointing gestures. Dasher uses a head-mouse or eyetracker and can be used in contexts where a full-size keyboard cannot be used, for example:

* on a palmtop computer
* on a wearable computer
* when operating a computer one-handed, by joystick, touchscreen, trackball, or mouse
* when operating a computer with zero hands (i.e., by head-mouse or by eyetracker).

Dasher must be installed manually. To learn more about the tool and its features, consult [Dasher website](https://www.inference.org.uk/djw30/dasher/eye.html).
