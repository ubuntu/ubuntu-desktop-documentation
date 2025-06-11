.. _org.a11y.atspi.Event.Object:

===========================
org.a11y.atspi.Event.Object
===========================

-----------
Description
-----------

.. _org.a11y.atspi.Event.Object Description:





.. _org.a11y.atspi.Event.Object Signals:

-------
Signals
-------

.. _org.a11y.atspi.Event.Object::PropertyChange:

org.a11y.atspi.Event.Object::PropertyChange
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    PropertyChange (
      property s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      value v,
      properties a{sv}
    )





property
  

unnamed_arg1
  

unnamed_arg2
  

value
  

properties
  



.. _org.a11y.atspi.Event.Object::BoundsChanged:

org.a11y.atspi.Event.Object::BoundsChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    BoundsChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::LinkSelected:

org.a11y.atspi.Event.Object::LinkSelected
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    LinkSelected (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::StateChanged:

org.a11y.atspi.Event.Object::StateChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    StateChanged (
      state s,
      enabled i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





state
  

enabled
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::ChildrenChanged:

org.a11y.atspi.Event.Object::ChildrenChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ChildrenChanged (
      operation s,
      index_in_parent i,
      unnamed_arg2 i,
      child v,
      properties a{sv}
    )





operation
  

index_in_parent
  

unnamed_arg2
  

child
  

properties
  



.. _org.a11y.atspi.Event.Object::VisibleDataChanged:

org.a11y.atspi.Event.Object::VisibleDataChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    VisibleDataChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::SelectionChanged:

org.a11y.atspi.Event.Object::SelectionChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    SelectionChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::ModelChanged:

org.a11y.atspi.Event.Object::ModelChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ModelChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::ActiveDescendantChanged:

org.a11y.atspi.Event.Object::ActiveDescendantChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ActiveDescendantChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      child v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

child
  

properties
  



.. _org.a11y.atspi.Event.Object::Announcement:

org.a11y.atspi.Event.Object::Announcement
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Announcement (
      unnamed_arg0 s,
      politeness i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

politeness
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::AttributesChanged:

org.a11y.atspi.Event.Object::AttributesChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    AttributesChanged (
      name s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





name
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::RowInserted:

org.a11y.atspi.Event.Object::RowInserted
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RowInserted (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::RowReordered:

org.a11y.atspi.Event.Object::RowReordered
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RowReordered (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::RowDeleted:

org.a11y.atspi.Event.Object::RowDeleted
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RowDeleted (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::ColumnInserted:

org.a11y.atspi.Event.Object::ColumnInserted
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ColumnInserted (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::ColumnReordered:

org.a11y.atspi.Event.Object::ColumnReordered
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ColumnReordered (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::ColumnDeleted:

org.a11y.atspi.Event.Object::ColumnDeleted
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ColumnDeleted (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::TextBoundsChanged:

org.a11y.atspi.Event.Object::TextBoundsChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    TextBoundsChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::TextSelectionChanged:

org.a11y.atspi.Event.Object::TextSelectionChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    TextSelectionChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::TextChanged:

org.a11y.atspi.Event.Object::TextChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    TextChanged (
      detail s,
      start_pos i,
      length i,
      text v,
      properties a{sv}
    )





detail
  

start_pos
  

length
  

text
  

properties
  



.. _org.a11y.atspi.Event.Object::TextAttributesChanged:

org.a11y.atspi.Event.Object::TextAttributesChanged
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    TextAttributesChanged (
      unnamed_arg0 s,
      unnamed_arg1 i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

unnamed_arg1
  

unnamed_arg2
  

unnamed_arg3
  

properties
  



.. _org.a11y.atspi.Event.Object::TextCaretMoved:

org.a11y.atspi.Event.Object::TextCaretMoved
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    TextCaretMoved (
      unnamed_arg0 s,
      position i,
      unnamed_arg2 i,
      unnamed_arg3 v,
      properties a{sv}
    )





unnamed_arg0
  

position
  

unnamed_arg2
  

unnamed_arg3
  

properties
  


