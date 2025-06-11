.. _org.a11y.atspi.Table:

====================
org.a11y.atspi.Table
====================

-----------
Description
-----------

.. _org.a11y.atspi.Table Description:





.. _org.a11y.atspi.Table Properties:

----------
Properties
----------

.. _org.a11y.atspi.Table:NRows:

org.a11y.atspi.Table:NRows
^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NRows readable i





.. _org.a11y.atspi.Table:NColumns:

org.a11y.atspi.Table:NColumns
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NColumns readable i





.. _org.a11y.atspi.Table:Caption:

org.a11y.atspi.Table:Caption
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Caption readable (so)





.. _org.a11y.atspi.Table:Summary:

org.a11y.atspi.Table:Summary
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Summary readable (so)





.. _org.a11y.atspi.Table:NSelectedRows:

org.a11y.atspi.Table:NSelectedRows
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NSelectedRows readable i





.. _org.a11y.atspi.Table:NSelectedColumns:

org.a11y.atspi.Table:NSelectedColumns
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NSelectedColumns readable i




.. _org.a11y.atspi.Table Methods:

-------
Methods
-------

.. _org.a11y.atspi.Table.GetAccessibleAt:

org.a11y.atspi.Table.GetAccessibleAt
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetAccessibleAt (
      IN row i,
      IN column i,
      OUT unnamed_arg2 (so)
    )





row
  

column
  

unnamed_arg2
  



.. _org.a11y.atspi.Table.GetIndexAt:

org.a11y.atspi.Table.GetIndexAt
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetIndexAt (
      IN row i,
      IN column i,
      OUT unnamed_arg2 i
    )





row
  

column
  

unnamed_arg2
  



.. _org.a11y.atspi.Table.GetRowAtIndex:

org.a11y.atspi.Table.GetRowAtIndex
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRowAtIndex (
      IN index i,
      OUT unnamed_arg1 i
    )





index
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.GetColumnAtIndex:

org.a11y.atspi.Table.GetColumnAtIndex
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetColumnAtIndex (
      IN index i,
      OUT unnamed_arg1 i
    )





index
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.GetRowDescription:

org.a11y.atspi.Table.GetRowDescription
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRowDescription (
      IN row i,
      OUT unnamed_arg1 s
    )





row
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.GetColumnDescription:

org.a11y.atspi.Table.GetColumnDescription
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetColumnDescription (
      IN column i,
      OUT unnamed_arg1 s
    )





column
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.GetRowExtentAt:

org.a11y.atspi.Table.GetRowExtentAt
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRowExtentAt (
      IN row i,
      IN column i,
      OUT unnamed_arg2 i
    )





row
  

column
  

unnamed_arg2
  



.. _org.a11y.atspi.Table.GetColumnExtentAt:

org.a11y.atspi.Table.GetColumnExtentAt
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetColumnExtentAt (
      IN row i,
      IN column i,
      OUT unnamed_arg2 i
    )





row
  

column
  

unnamed_arg2
  



.. _org.a11y.atspi.Table.GetRowHeader:

org.a11y.atspi.Table.GetRowHeader
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRowHeader (
      IN row i,
      OUT unnamed_arg1 (so)
    )





row
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.GetColumnHeader:

org.a11y.atspi.Table.GetColumnHeader
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetColumnHeader (
      IN column i,
      OUT unnamed_arg1 (so)
    )





column
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.GetSelectedRows:

org.a11y.atspi.Table.GetSelectedRows
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetSelectedRows (
      OUT unnamed_arg0 ai
    )





unnamed_arg0
  



.. _org.a11y.atspi.Table.GetSelectedColumns:

org.a11y.atspi.Table.GetSelectedColumns
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetSelectedColumns (
      OUT unnamed_arg0 ai
    )





unnamed_arg0
  



.. _org.a11y.atspi.Table.IsRowSelected:

org.a11y.atspi.Table.IsRowSelected
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    IsRowSelected (
      IN row i,
      OUT unnamed_arg1 b
    )





row
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.IsColumnSelected:

org.a11y.atspi.Table.IsColumnSelected
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    IsColumnSelected (
      IN column i,
      OUT unnamed_arg1 b
    )





column
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.IsSelected:

org.a11y.atspi.Table.IsSelected
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    IsSelected (
      IN row i,
      IN column i,
      OUT unnamed_arg2 b
    )





row
  

column
  

unnamed_arg2
  



.. _org.a11y.atspi.Table.AddRowSelection:

org.a11y.atspi.Table.AddRowSelection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    AddRowSelection (
      IN row i,
      OUT unnamed_arg1 b
    )





row
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.AddColumnSelection:

org.a11y.atspi.Table.AddColumnSelection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    AddColumnSelection (
      IN column i,
      OUT unnamed_arg1 b
    )





column
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.RemoveRowSelection:

org.a11y.atspi.Table.RemoveRowSelection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RemoveRowSelection (
      IN row i,
      OUT unnamed_arg1 b
    )





row
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.RemoveColumnSelection:

org.a11y.atspi.Table.RemoveColumnSelection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RemoveColumnSelection (
      IN column i,
      OUT unnamed_arg1 b
    )





column
  

unnamed_arg1
  



.. _org.a11y.atspi.Table.GetRowColumnExtentsAtIndex:

org.a11y.atspi.Table.GetRowColumnExtentsAtIndex
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRowColumnExtentsAtIndex (
      IN index i,
      OUT unnamed_arg1 b,
      OUT row i,
      OUT col i,
      OUT row_extents i,
      OUT col_extents i,
      OUT is_selected b
    )





index
  

unnamed_arg1
  

row
  

col
  

row_extents
  

col_extents
  

is_selected
  


