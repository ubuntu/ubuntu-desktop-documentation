.. _org.a11y.atspi.DeviceEventController:

====================================
org.a11y.atspi.DeviceEventController
====================================

-----------
Description
-----------

.. _org.a11y.atspi.DeviceEventController Description:

Legacy interface for keystroke listeners and generation of keyboard/mouse events

This interface is being replaced by the functions in atspi-device-listener.h.



.. _org.a11y.atspi.DeviceEventController Methods:

-------
Methods
-------

.. _org.a11y.atspi.DeviceEventController.RegisterKeystrokeListener:

org.a11y.atspi.DeviceEventController.RegisterKeystrokeListener
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RegisterKeystrokeListener (
      IN listener o,
      IN keys a(iisi),
      IN mask u,
      IN types u,
      IN mode (bbb),
      OUT unnamed_arg5 b
    )



The ``types`` can be a mask of the following:

  * KEY_PRESS   = 1 << 0
  * KEY_RELEASE = 1 << 1

Note that Orca always passes (KEY_PRESS | KEY_RELEASE).

The ``mode`` is composed of three flags (see AtspiKeyListenerSyncType):

  * synchronous: Events are delivered synchronously, before
    the currently focused application sees them.  If false,
    events may be delivered asynchronously, which means in some
    cases they may already have been delivered to the
    application before the AT client receives the notification.

  * preemptive: (called CANCONSUME in AtspiKeyListenerSyncType)
    Events may be consumed by the AT client.  Requires the synchronous flag to be set.

  * global: (called ALL_WINDOWS in AtspiKeyListenerSyncType)
    Events are received not from the application toolkit layer,
    but from the device driver or windowing system subsystem.

Returns: boolean indicating whether the operation was successful.  This is always
TRUE for non-global listeners (c.f. ``mode``), and may be FALSE for global listeners
if the underlying XGrabKey() failed (see spi_dec_x11_grab_key).



listener
  path of object to be notified when the following keys are pressed

keys
  array of (key_code, key_sym, key_string, unused)

mask
  modifier mask in X11 style (see Xlib.h)

types
  mask of press/release; see the description below.

mode
  struct of flags (synchronous, preemptive, global), see the description below.

unnamed_arg5
  



.. _org.a11y.atspi.DeviceEventController.DeregisterKeystrokeListener:

org.a11y.atspi.DeviceEventController.DeregisterKeystrokeListener
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    DeregisterKeystrokeListener (
      IN listener o,
      IN keys a(iisi),
      IN mask u,
      IN type u
    )





listener
  

keys
  

mask
  

type
  



.. _org.a11y.atspi.DeviceEventController.GetKeystrokeListeners:

org.a11y.atspi.DeviceEventController.GetKeystrokeListeners
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetKeystrokeListeners (
      OUT unnamed_arg0 a(souua(iisi)u(bbb))
    )





unnamed_arg0
  



.. _org.a11y.atspi.DeviceEventController.GenerateKeyboardEvent:

org.a11y.atspi.DeviceEventController.GenerateKeyboardEvent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GenerateKeyboardEvent (
      IN keycode i,
      IN keystring s,
      IN type u
    )





keycode
  

keystring
  

type
  



.. _org.a11y.atspi.DeviceEventController.GenerateMouseEvent:

org.a11y.atspi.DeviceEventController.GenerateMouseEvent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GenerateMouseEvent (
      IN x i,
      IN y i,
      IN eventName s
    )





x
  

y
  

eventName
  



.. _org.a11y.atspi.DeviceEventController.NotifyListenersSync:

org.a11y.atspi.DeviceEventController.NotifyListenersSync
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NotifyListenersSync (
      IN event (uiuuisb),
      OUT unnamed_arg1 b
    )





event
  

unnamed_arg1
  



.. _org.a11y.atspi.DeviceEventController.NotifyListenersAsync:

org.a11y.atspi.DeviceEventController.NotifyListenersAsync
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NotifyListenersAsync (
      IN event (uiuuisb)
    )





event
  


