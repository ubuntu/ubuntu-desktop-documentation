# Architecture of the accessibility stack

## Software Interfaces for assistive technologies

### AT-SPI

The Assistive Technology Service Provider Interface (AT-SPI) is a platform-neutral framework for bi-directional communication between assistive technologies (AT) and applications. 

AT-SPI defines a set of interfaces for assistive technologies which allow to get names, roles and states of interface objects, listen for events, or perform actions. 

AT-SPI uses D-Bus method calls and signals. D-Bus is an inter-process communication system in Linux, which makes AT-SPI a default accessibility framework for Linux.  

AT-SPI is made of two components:

`at-spi2-core`
: A collection of XML interfaces for accessibility

`at-spi2-atk`
: A library that allows applications made with GTK 3 to register accessible objects with AT-SPI

If you are building custom assistive technology tools or want to test the accessibility of custom applications that were not built with GTK on Ubuntu Desktop, you must use {ref}`at-spi-dbus-xml-interfaces`.

### GTK4 and Gtk.Accessible

GTK is a cross-platform widget toolkit for creating graphical user interfaces. It offers a set of user interface elements that allow developers to build apps quickly and in a consistent manner. The majority of applications within GNOME desktop environment are built with GTK.       

GTK4 is a newer version of GTK that implements its own [Gtk.Accessible](https://docs.gtk.org/gtk4/iface.Accessible.html) interface instead of the previously used ATK.

If you are building an application for Ubuntu Desktop and want to make it accessible for Ubuntu Desktop's default assistive technologies such as Orca, it is recommended that you use GTK. Desktop's assistive solutions are able to access information about the apps built with both GTK3 and GTK4.

If you are using a different UI toolkit, you must ensure it implements the AT-SPI D-Bus interfaces; otherwise, Desktop's assistive technologies wouldn't be able to interact with it. 

### GTK3 and ATK 

GTK3 version of the GTK toolkit that integrates with Accessibility Toolkit (ATK). Applications built with GTK3 expose information about UI objects using the ATK. ATK is an Application Programming Interface (API) that allows developers to avoid working with AT-SPI API directly, as it provides a set of special input methods. 

### Flutter

A selection of applications on Ubuntu Desktop such as [App Center](https://github.com/ubuntu/app-center) are built with Flutter. Flutter engine has compatibility issues with AT-SPI. To learn how to make Fluuter applications that would be compatible with Ubuntu Desktop's default assistive solutions, reach out to the development team at [Discourse](https://discourse.ubuntu.com/tag/flutter).


### Overview of Ubuntu Desktop applications and their interfaces

| Application              | Built with    | API                                                                |
| ------------------------ | ------------- | ------------------------------------------------------------------ |
| Gnome Initial Setup      | GTK4          | [Gtk.Accessible](https://docs.gtk.org/gtk4/iface.Accessible.html)  |        
| Login and Lock screens   | GTK3          | [ATK](https://docs.gtk.org/atk/) |
| System Settings app      | GTK4          | [Gtk.Accessible](https://docs.gtk.org/gtk4/iface.Accessible.html) |
| App Center               | Flutter       | [Flutter API](https://docs.flutter.dev/ui/accessibility-and-internationalization/accessibility) |
| Software and Updates     | GTK3          | [ATK](https://docs.gtk.org/atk/) |

