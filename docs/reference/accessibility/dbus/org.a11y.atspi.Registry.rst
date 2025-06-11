.. _org.a11y.atspi.Registry:

=======================
org.a11y.atspi.Registry
=======================

-----------
Description
-----------

.. _org.a11y.atspi.Registry Description:





.. _org.a11y.atspi.Registry Methods:

-------
Methods
-------

.. _org.a11y.atspi.Registry.RegisterEvent:

org.a11y.atspi.Registry.RegisterEvent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RegisterEvent (
      IN event s,
      IN properties as,
      IN app_bus_name s
    )





event
  

properties
  

app_bus_name
  



.. _org.a11y.atspi.Registry.DeregisterEvent:

org.a11y.atspi.Registry.DeregisterEvent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    DeregisterEvent (
      IN event s
    )





event
  



.. _org.a11y.atspi.Registry.GetRegisteredEvents:

org.a11y.atspi.Registry.GetRegisteredEvents
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRegisteredEvents (
      OUT events a(ss)
    )





events
  


.. _org.a11y.atspi.Registry Signals:

-------
Signals
-------

.. _org.a11y.atspi.Registry::EventListenerRegistered:

org.a11y.atspi.Registry::EventListenerRegistered
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    EventListenerRegistered (
      bus s,
      path s
    )





bus
  

path
  



.. _org.a11y.atspi.Registry::EventListenerDeregistered:

org.a11y.atspi.Registry::EventListenerDeregistered
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    EventListenerDeregistered (
      bus s,
      path s
    )





bus
  

path
  


