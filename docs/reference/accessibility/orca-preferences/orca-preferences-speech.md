
(orca-speech-preferences)=
# Speech preferences

## Enable speech

Controls whether Orca uses a speech synthesizer.  

**Default value:** Checked

## Verbosity

Determines how much information Orca speaks in different contexts.  

**Default value:** Verbose

## Punctuation level

Controls how much punctuation is spoken:

**None**
: no punctuation (except symbols like bullets, Unicode fractions)  

**Some**
: adds math and currency symbols, `^`, `@`, `/`, `&`, `#`  

**Most**
: adds nearly all punctuation except `!`, `'`, `,`, `.`, `?`  

**All**
: every known punctuation symbol

**Default value:** Most

## Spoken Context

Provides system-level info about the focused item via the System voice.

**Only speak displayed text**
: restricts speech to visible on-screen text  

**Default value:** Not checked

Enabling "Only speak displayed text" disables the following options:

**Speak blank lines**
: says "blank" for empty lines  
**Default value:** Checked

**Speak indentation and justification**
: useful when working with code  
**Default value:** Not checked

**Speak misspelled-word indicator**
: announces "misspelled" when relevant  
**Default value:** Checked

**Speak object mnemonics**
: announces shortcut keys (e.g., Alt+O for OK)  
**Default value:** Not checked

**Speak child position**
: announces item position in menus/lists/trees (e.g., "9 of 16")  
**Default value:** Not checked

**Speak tutorial messages**
: provides interaction tips for focused items  
**Default value:** Not checked

**Speak description**
: includes accessible description along with name  
**Default value:** Checked

**System messages are detailed**
: enables verbose system messages  
**Default value:** Checked

**Speak colors as names**
: says names like "midnight blue" instead of RGB values  
**Default value:** Checked

## Announce contextual information during navigation

Orca will notify you when navigating into/out of containers.  

- Announce blockquotes
- Announce forms
- Announce landmarks
- Announce lists
- Announce panels
- Announce tables

**Default value:** Checked 

:::{note}
These are independent of **Say All** settings.
:::

## Speak full row settings

Orca will speak the full row rather than just the focused cell in:

**GUI tables**
: e.g., as email list  
**Default value:** Checked

**Document tables**
: e.g., in Writer or web  
**Default value:** Checked

**Spreadsheets**
: **Default value:** Not checked
