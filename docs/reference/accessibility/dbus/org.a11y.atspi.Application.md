# org.a11y.atspi.Application

## Description

Interface that must be implemented by the root object of an application.

## Properties

### org.a11y.atspi.Application:ToolkitName 



    ToolkitName readable s



Name of the GUI toolkit used by the application, for example GTK or Qt. 

### org.a11y.atspi.Application:Version 



    Version readable s



Version of the GUI toolkit used by the application.

### org.a11y.atspi.Application:AtspiVersion 



    AtspiVersion readable s



Version of the AT-SPI that the application supports.

<!---
Original description: 
You should return \"2.1\" here. This was intended to be the version of
the atspi interfaces that the application supports, but atspi will
probably move to using versioned interface names instead. Just return
\"2.1\" here.
-->


### org.a11y.atspi.Application:Id



    Id readwrite i



A numerical ID of the application, generated when an application uses ``org.a11y.atspi.Socket.Embed`` to register with the accessibility registry. 

<!---
Original description: 
Per <https://gitlab.gnome.org/GNOME/at-spi2-core/-/issues/82> it may
turn out that this id is not actually used subsequently. This is a
remnant of the time when registryd actually had to make up identifiers
for each application. With DBus, however, it is the bus that assigns
unique names to applications that connect to it.

Your application or toolkit can remember the ID passed when the
accessibility registry sets this property, and return it back when the
property is read.

TO-DO: Check if this ID is actually used for anything and if it needs to be documented.
-->


## Methods

### org.a11y.atspi.Application.GetLocale 



    GetLocale (
      IN lctype u,
      OUT unnamed_arg1 s
    )



Returns a locale of the application in a POSIX locale format. Use it to adjust behavior of the software such as speech output or formatting according to the application's language and regional settings.

### org.a11y.atspi.Application.GetApplicationBusAddress



    GetApplicationBusAddress (
      OUT unnamed_arg0 s
    )



Returns a D-Bus address for the main D-Bus connection of the application. 

