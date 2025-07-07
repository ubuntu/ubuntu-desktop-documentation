# Architecture of the accessibility stack

## Software interfaces for assistive technologies

### AT-SPI

The Assistive Technology Service Provider Interface (AT-SPI) is a platform-neutral framework for communication between assistive technologies (AT) and applications. 

AT-SPI defines a set of interfaces for assistive technologies which allow to get names, roles, and states of interface objects, listen for events, or perform actions. 

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


## Screen reader and speech synthethis 

Speech synthesizers converts text to human-sounding speech. Typically, they are offered as a backend for screen readers, but they can also be used as standalone programs. Orca is the default screen reader on Ubuntu Desktop. eSpeak and Speech Dispatcher are the 
speech synthesizers that Orca depends on. When Orca identifies the text, it passes it to the Speech Dispatcher for speech synthesis; the Speech Dispatcher then passes the synthesized speech to eSpeak, which plays the sound.

### Orca

Orca is a screen reader for vision impaired and blind users. 

Orca is preinstalled on Ubuntu Desktop and can be used out-of-box. To learn how to configure it, go to {ref}`read-screen-aloud`.

### BRLTTY

The Orca screen reader can display the user interface on a refreshable Braille display. It uses the BRLTTY service, which provides access to the Linux console for a blind person using a refreshable Braille display. 

As Orca, BRLTTY is preinstalled and can be enabled and used without any additional configurations, see {ref}`read-screen-in-braille`.

### eSpeak

eSpeak is a speech synthesizer that supports over 100 languages and accents. eSpeak can be used as a standalalone tool or as a backend component for screen readers, see [eSpeak website](https://espeak.sourceforge.net/)

### Speech dispatcher

Speech dispatcher is a device-independent high-level interface for speech synthesis. It can be used by other software and hardware speech synthesizers as a backend, see [Speech Dispatcher website](https://freebsoft.org/speechd). 

Therefore, Speech Dispatcher is the layer that allows you to switch between text-to-speech (TTS) solutions.

## On-screen keyboards

### GNOME on-screen keyboard

Ubuntu Desktop comes with a GNOME on-screen keyboard preinstalled, it is the on-screen keyboard that we recommend for Desktop. To start using it, see {ref}`use-an-on-screen-keyboard`.




## Hardware interfaces for assistive technologies

### USB 

Ubuntu Desktop supports USB out of the box. 

In Ubuntu, kernel USB drivers handle communications with USB devices such as, for example, `usbhid` which provides support for USB Human Interface Devices (HID) class. Kernel supports all [standard USB classes](https://www.usb.org/defined-class-codes).

`udev` is a device manager in Ubuntu that detects, adds and removed devices. `udev` stores the information about detected USB devices in the `/dev` directory.

If your device conforms to a USB class, it will be assigned a /dev entry and recognized correctly.

#### USB device requirements

You can use USB to connect assistive devices for input/output such as Braille displays, sip-and-puff, foot pedals.

To be able to work on Ubuntu properly, a USB device must:

* use a standard USB class 
* provide a proper USB descriptor so that Ubuntu can identify it
* not require proprietary drivers

If the device uses a custom class, it must provide a `udev` .rules file instead so that Ubuntu can identify it correctly, see [udev documentation](https://www.man7.org/linux/man-pages/man7/udev.7.html) 

### Bluetooth 

Ubuntu Desktop supports Bluetooth out of the box. [BlueZ](https://www.bluez.org/) is the official Bluetooth stack for Linux distributions, including Ubuntu Desktop.

BlueZ implements various Bluetooth profiles such as HID, A2DP, HFP, SPP, and others. See [BlueZ supported profiles](https://www.bluez.org/profiles/). If a device is compliant with one of the supported profiles, BlueZ automatically detects, pairs, and exposes it as an input device on Linux. 

#### Bluetooth device requirements

You can use Bluetooth to connect wireless assistive devices such as switch control devices or head trackers.

To be able to work on Ubuntu properly, a Bluetooth device must:

* use HID for input devices 
* use A2DP/HFP for audio output
