(work-around-known-screen-reader-issues)=
# Work around known screen reader issues

Ubuntu 24.04 LTS has certain known issues when using the screen reader. If you encounter them, you can use the following ways to improve accessibility.

## Orca modifier

If the Caps Lock Orca modifier is unreliable, you can either connect a full-size keyboard or you can switch to a different modifier while keeping the laptop layout.

## Replace GTK4 and Flutter applications

The screen reader works fine in GTK3 applications, but in GTK4 and Flutter, you can only browse interactive elements using Tab. You can’t use other Orca commands like Flat Review or object search. Therefore, you can’t read non-interactive elements.

## Upgrade to the latest Ubuntu

Ubuntu 25.04 and 25.10 greatly improves the screen reader experience.

