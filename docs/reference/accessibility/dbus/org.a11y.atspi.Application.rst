.. _org.a11y.atspi.Application:

==========================
org.a11y.atspi.Application
==========================

-----------
Description
-----------

.. _org.a11y.atspi.Application Description:

Interface that must be implemented by the root object of an application.



.. _org.a11y.atspi.Application Properties:

----------
Properties
----------

.. _org.a11y.atspi.Application:ToolkitName:

org.a11y.atspi.Application:ToolkitName
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ToolkitName readable s


name of the toolkit used to implement the application's user interface.



.. _org.a11y.atspi.Application:Version:

org.a11y.atspi.Application:Version
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Version readable s


version of the toolkit used to implement the application's user interface.



.. _org.a11y.atspi.Application:AtspiVersion:

org.a11y.atspi.Application:AtspiVersion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    AtspiVersion readable s


You should return "2.1" here.
This was intended to be the version of the atspi interfaces
that the application supports, but atspi will probably move to
using versioned interface names instead.  Just return "2.1" here.




.. _org.a11y.atspi.Application:Id:

org.a11y.atspi.Application:Id
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Id readwrite i


set to an arbitrary numerical id when an application registers with the registry.
When a freshly-started application uses the
org.a11y.atspi.Socket.Embed method to register with the
accessibility registry, the registry will set a numerical id
on the application.

Per https://gitlab.gnome.org/GNOME/at-spi2-core/-/issues/82 it
may turn out that this id is not actually used subsequently.
This is a remnant of the time when registryd actually had to
make up identifiers for each application.  With DBus, however,
it is the bus that assigns unique names to applications that
connect to it.

Your application or toolkit can remember the Id passed when
the accessibility registry sets this property, and return it
back when the property is read.



.. _org.a11y.atspi.Application Methods:

-------
Methods
-------

.. _org.a11y.atspi.Application.GetLocale:

org.a11y.atspi.Application.GetLocale
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetLocale (
      IN lctype u,
      OUT unnamed_arg1 s
    )





lctype
  

unnamed_arg1
  



.. _org.a11y.atspi.Application.GetApplicationBusAddress:

org.a11y.atspi.Application.GetApplicationBusAddress
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetApplicationBusAddress (
      OUT unnamed_arg0 s
    )





unnamed_arg0
  


