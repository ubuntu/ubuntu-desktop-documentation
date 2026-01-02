# org.a11y.atspi.Cache

## Description


Interface to access objects in bulk. It provides local access to previously fetched objects and helps improve performance by reducing round-trip calls.

Assistive technology should do a bulk query of all the objects in a new window with the `GetItems` method, and then update them dynamically with the `AddAccessible` and `RemoveAccessible` signals.

<!---
Original description: 


The application should expose this interface at the
/org/a11y/atspi/cache object path.

The `org.a11y.atspi.Accessible` interface has method to transfer an object\'s D-Bus id. The
caller has to then query the object\'s properties individually.
Transferring objects one by one and then their properties produces a lot
of traffic in the accessibility bus.

So, this Cache interface can be used to query objects in bulk. Assistive
tech should try to do a bulk query of all the objects in a new window
with the GetItems method, and then update them dynamically from the
AddAccessible and RemoveAccessible signals.

FIXME: Does GetItems only get called if an application implements
GetApplicationBusAddress? GTK4 doesn\'t implement that, but it
implements GetItems -does that ever get called?
-->

## Methods 

### org.a11y.atspi.Cache.GetItems 



    GetItems (
      OUT nodes a((so)(so)(so)iiassusau)
    )

Returns a list of cached accessible objects as an array with one element for each available object.

Each element in the array contains the following fields:

-   (so): accessible object reference - D-Bus name and object path. The
    rest of the fields refer to this main object.

-   (so): application reference - D-Bus name and object path. This is the
    owner of the main object; the root path of the application that
    registered via the Embed method of the org.a11y.atspi.Socket
    interface.

-   (so): parent object reference - D-Bus name and object path.

    :   If the main object has no parent:

        -   If it is a control, or a window, return the parent
            application.
        -   If the object has the application role, return a null
            reference. FIXME:
            atk-adaptor/adaptors/cache-adaptor.c:append_cache_item()
            returns a reference to the registry in this case (the one it
            obtained from the initial Socket::Embed call); GTK4 returns
            a null reference.
        -   Otherwise, return a null reference (\"\" for the application
            name name and \"/org/a11y/atspi/null\" for the object path).

-   i: index in parent, or -1 for transient widgets/menu items.
    Equivalent to the GetIndexInParent method of the
   ` org.a11y.atspi.Accessible` interface.

-   i: child count of main object, or -1 for defunct/menus. Equivalent
    to the ChildCount property of the `org.a11y.atspi.Accessible`
    interface.

-   as: array of names of the interfaces that the main object supports.
    Equivalent to the GetInterfaces method of the
    org.a11y.atspi.Accessible interface.

-   s: human-readable, localized, short name for the main object.
    Equivalent to the Name property of the `org.a11y.atspi.Accessible`
    interface.

-   u: role. Equivalent to the GetRole method of the
    `org.a11y.atspi.Accessible` interface.

-   s: human-readable, localized description of the object in more
    detail. Equivalent to the Description property of the
    `org.a11y.atspi.Accessible` interface.

-   au: Set of states currently held by an object. Equivalent to the
    GetState method of the `org.a11y.atspi.Accessible` interface.

<!---
Part of the original description: 

Deprecation note: The signature for the return value of this method
changed in 2015, in commit b2c8c4c7. It used to be
\"a((so)(so)(so)a(so)assusau)\". The \"a(so)\" instead of \"ii\" is a
list of references to child objects. The implementation in atspi-misc.c
can handle either version, although the intention is to deprecate the
code that handles the old version. Qt still uses this old signature and
should be changed to the new scheme (see qspi_struct_marshallers.cpp in
the Qt source code).
-->


## Signals 

### org.a11y.atspi.Cache::AddAccessible



    AddAccessible (
      nodeAdded ((so)(so)(so)iiassusau)
    )

Add an accessible object to the cache. See the `org.a11y.atspi.Cache.GetItems` for a
description of the signature.

### org.a11y.atspi.Cache::RemoveAccessible



    RemoveAccessible (
      nodeRemoved (so)
    )

Remove an accessible object from the cache.
