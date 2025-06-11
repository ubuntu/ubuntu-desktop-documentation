.. _org.a11y.atspi.TableCell:

========================
org.a11y.atspi.TableCell
========================

-----------
Description
-----------

.. _org.a11y.atspi.TableCell Description:





.. _org.a11y.atspi.TableCell Properties:

----------
Properties
----------

.. _org.a11y.atspi.TableCell:ColumnSpan:

org.a11y.atspi.TableCell:ColumnSpan
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ColumnSpan readable i





.. _org.a11y.atspi.TableCell:Position:

org.a11y.atspi.TableCell:Position
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Position readable (ii)





.. _org.a11y.atspi.TableCell:RowSpan:

org.a11y.atspi.TableCell:RowSpan
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    RowSpan readable i





.. _org.a11y.atspi.TableCell:Table:

org.a11y.atspi.TableCell:Table
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Table readable (so)




.. _org.a11y.atspi.TableCell Methods:

-------
Methods
-------

.. _org.a11y.atspi.TableCell.GetRowColumnSpan:

org.a11y.atspi.TableCell.GetRowColumnSpan
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRowColumnSpan (
      OUT unnamed_arg0 b,
      OUT row i,
      OUT col i,
      OUT row_extents i,
      OUT col_extents i
    )





unnamed_arg0
  

row
  

col
  

row_extents
  

col_extents
  



.. _org.a11y.atspi.TableCell.GetColumnHeaderCells:

org.a11y.atspi.TableCell.GetColumnHeaderCells
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetColumnHeaderCells (
      OUT unnamed_arg0 a(so)
    )



Returns a list of the table cell's column header cells.



unnamed_arg0
  



.. _org.a11y.atspi.TableCell.GetRowHeaderCells:

org.a11y.atspi.TableCell.GetRowHeaderCells
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetRowHeaderCells (
      OUT unnamed_arg0 a(so)
    )



Returns a list of the table cell's row header cells.



unnamed_arg0
  


