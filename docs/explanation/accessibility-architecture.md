# Architecture of the accessibility stack

## Software Interfaces for assistive technologies

### AT-SPI

The Assistive Technology Service Provider Interface (AT-SPI) is a platform-neutral framework for bi-directional communication between assistive technologies (AT) and applications. 

AT-SPI defines a set of interfaces which specify assistive technologies can get names, roles, states of interface objects, listen for events, or perform actions. 

AT-SPI uses D-Bus method calls and signals. D-Bus is an inter-process communication system in Linux which makes AT-SPI a default accessibility framework for distributions that use D-Bus.  

AT-SPI is made of two components:

* ``at-spi2-core``: a collection of XML interfaces for accessibility
* ``at-spi2-atk``: a library that allows application made with GTK to register accessible objects with AT-SPI

If you are building custom assistive technology tools or want to test accessibility of custom applications that were not built with GTK on Ubuntu Desktop, you must use [AT-SPI DBus XML Interfaces](../reference/accessibility/dbus/index.rst)

### GTK3 and ATK 

GTK is a cross-platform widget toolkit for creating graphical user interface, it is a set of user interface elements that allows developers to build apps quickly and in a consistent manner. The majority of applications within GNOME desktop environment are built with GTK.

GTK3 version of the toolkit integrates with Accessibility Toolkit (ATK). Applications built with GTK3 expose the information about the UI objects using accessibility Accessibility Toolkit (ATK). ATK is an application programming interface which allows developers to avoid having to work with AT-SPI API directly as it provides a set of special input methods. 

### GTK4 and Gtk.Accessible

GTK4 is a newer version of GTK that *does not* integrate with ATK. Instead, GTK4 implements its own [Gtk.Accessible](https://docs.gtk.org/gtk4/iface.Accessible.html) interface.

If you are buildng an application for Ubuntu Desktop and want to make it accessible for Ubuntu Desktop's default assistive technologies such as Orca, it is recommended that you use GTK. Desktop's assistive solutions are able to access information about the apps built with both GTK3 and GTK4.

If you are using a different UI toolkit, you must ensure it implements the AT-SPI D-Bus interfaces, otherwise Desktop's assistive technologies wouldn't be able to interact with it. 

### Flutter

A small selection of applications on Ubuntu Desktop is built with Flutter.

### Overview of Ubuntu Desktop applications and their interfaces

| Application              | Built with    | API                                                                |
| ------------------------ | ------------- | ------------------------------------------------------------------ |
| Gnome Initial Setup      | GTK4          | [Gtk.Accessible](https://docs.gtk.org/gtk4/iface.Accessible.html)  |        
| Login and Lock screens   | ?             | ? |
| System Settings app      | ?             | ? |
| App Store                | ?             | ? |
| Software and Updates     | ?             | ? |


## Hardware interfaces for assistive technologies

### USB HID
### Bluetooth HID 
### Sound output interface