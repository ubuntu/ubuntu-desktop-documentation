.. _org.a11y.atspi.EditableText:

===========================
org.a11y.atspi.EditableText
===========================

-----------
Description
-----------

.. _org.a11y.atspi.EditableText Description:





.. _org.a11y.atspi.EditableText Methods:

-------
Methods
-------

.. _org.a11y.atspi.EditableText.SetTextContents:

org.a11y.atspi.EditableText.SetTextContents
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    SetTextContents (
      IN newContents s,
      OUT unnamed_arg1 b
    )





newContents
  

unnamed_arg1
  



.. _org.a11y.atspi.EditableText.InsertText:

org.a11y.atspi.EditableText.InsertText
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    InsertText (
      IN position i,
      IN text s,
      IN length i,
      OUT unnamed_arg3 b
    )





position
  

text
  

length
  

unnamed_arg3
  



.. _org.a11y.atspi.EditableText.CopyText:

org.a11y.atspi.EditableText.CopyText
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    CopyText (
      IN startPos i,
      IN endPos i
    )





startPos
  

endPos
  



.. _org.a11y.atspi.EditableText.CutText:

org.a11y.atspi.EditableText.CutText
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    CutText (
      IN startPos i,
      IN endPos i,
      OUT unnamed_arg2 b
    )





startPos
  

endPos
  

unnamed_arg2
  



.. _org.a11y.atspi.EditableText.DeleteText:

org.a11y.atspi.EditableText.DeleteText
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    DeleteText (
      IN startPos i,
      IN endPos i,
      OUT unnamed_arg2 b
    )





startPos
  

endPos
  

unnamed_arg2
  



.. _org.a11y.atspi.EditableText.PasteText:

org.a11y.atspi.EditableText.PasteText
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    PasteText (
      IN position i,
      OUT unnamed_arg1 b
    )





position
  

unnamed_arg1
  


