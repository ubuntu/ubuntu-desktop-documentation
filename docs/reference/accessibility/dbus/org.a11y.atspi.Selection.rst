.. _org.a11y.atspi.Selection:

========================
org.a11y.atspi.Selection
========================

-----------
Description
-----------

.. _org.a11y.atspi.Selection Description:





.. _org.a11y.atspi.Selection Properties:

----------
Properties
----------

.. _org.a11y.atspi.Selection:NSelectedChildren:

org.a11y.atspi.Selection:NSelectedChildren
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NSelectedChildren readable i




.. _org.a11y.atspi.Selection Methods:

-------
Methods
-------

.. _org.a11y.atspi.Selection.GetSelectedChild:

org.a11y.atspi.Selection.GetSelectedChild
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetSelectedChild (
      IN selectedChildIndex i,
      OUT unnamed_arg1 (so)
    )





selectedChildIndex
  

unnamed_arg1
  



.. _org.a11y.atspi.Selection.SelectChild:

org.a11y.atspi.Selection.SelectChild
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    SelectChild (
      IN childIndex i,
      OUT unnamed_arg1 b
    )





childIndex
  

unnamed_arg1
  



.. _org.a11y.atspi.Selection.DeselectSelectedChild:

org.a11y.atspi.Selection.DeselectSelectedChild
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    DeselectSelectedChild (
      IN selectedChildIndex i,
      OUT unnamed_arg1 b
    )





selectedChildIndex
  

unnamed_arg1
  



.. _org.a11y.atspi.Selection.IsChildSelected:

org.a11y.atspi.Selection.IsChildSelected
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    IsChildSelected (
      IN childIndex i,
      OUT unnamed_arg1 b
    )





childIndex
  

unnamed_arg1
  



.. _org.a11y.atspi.Selection.SelectAll:

org.a11y.atspi.Selection.SelectAll
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    SelectAll (
      OUT unnamed_arg0 b
    )





unnamed_arg0
  



.. _org.a11y.atspi.Selection.ClearSelection:

org.a11y.atspi.Selection.ClearSelection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ClearSelection (
      OUT unnamed_arg0 b
    )





unnamed_arg0
  



.. _org.a11y.atspi.Selection.DeselectChild:

org.a11y.atspi.Selection.DeselectChild
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    DeselectChild (
      IN childIndex i,
      OUT unnamed_arg1 b
    )





childIndex
  

unnamed_arg1
  


