.. _org.a11y.atspi.Socket:

=====================
org.a11y.atspi.Socket
=====================

-----------
Description
-----------

.. _org.a11y.atspi.Socket Description:

Interface to register an application on the registry.



.. _org.a11y.atspi.Socket Methods:

-------
Methods
-------

.. _org.a11y.atspi.Socket.Embed:

org.a11y.atspi.Socket.Embed
^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Embed (
      IN plug (so),
      OUT socket (so)
    )




for the application's' root object.

This is the entry point for an application that wants to register itself against
the accessibility registry.  The application's root object, which it passes in
``plug``, must support the org.a11y.atspi.Application interface.

When an application calls this method on the registry, the following handshake happens:

* Application calls this method on the registry to identify itself.

* The registry sets the "Id" property on the org.a11y.atspi.Application interface on the ``plug`` object.

* The Embed method returns with the bus name and object path for the registry's root object.

Returns: the bus name and object path of the registry's root object.



plug
  a string for the unique bus name of the application, and an object path

socket
  



.. _org.a11y.atspi.Socket.Embedded:

org.a11y.atspi.Socket.Embedded
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Embedded (
      IN path s
    )



This method is called by a socket to inform the plug that it is being
embedded. The plug should register the embedding socket as its parent.



path
  the object path of the socket.



.. _org.a11y.atspi.Socket.Unembed:

org.a11y.atspi.Socket.Unembed
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Unembed (
      IN plug (so)
    )




for the application's' root object.

Unregisters an application from the accesibility registry.  It is not necessary to
call this method; the accessibility registry detects when an application
disconnects from the bus.



plug
  a string for the unique bus name of the application, and an object path


.. _org.a11y.atspi.Socket Signals:

-------
Signals
-------

.. _org.a11y.atspi.Socket::Available:

org.a11y.atspi.Socket::Available
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Available (
      socket (so)
    )



The accessibility registry emits this signal early during startup, when it has
registered with the DBus daemon and is available for calls from applications.



socket
  application and object path for the registry's root object.


