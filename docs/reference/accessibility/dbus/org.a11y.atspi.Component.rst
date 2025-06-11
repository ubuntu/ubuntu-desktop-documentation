.. _org.a11y.atspi.Component:

========================
org.a11y.atspi.Component
========================

-----------
Description
-----------

.. _org.a11y.atspi.Component Description:

Interface for GUI components like widgets or other visible elements.



.. _org.a11y.atspi.Component Methods:

-------
Methods
-------

.. _org.a11y.atspi.Component.Contains:

org.a11y.atspi.Component.Contains
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    Contains (
      IN x i,
      IN y i,
      IN coord_type u,
      OUT unnamed_arg3 b
    )




component's top level window; see the description.

Queries whether a point (x, y) is inside the component.

The ``coord_type`` values are as follows, and correspond to AtkCoordType:

0 - Coordinates are relative to the screen.
1 - Coordinates are relative to the component's toplevel window.
2 - Coordinates are relative to the component's immediate parent.



x
  X coordinate of point.

y
  Y coordinate of point.

coord_type
  Whether the coordinates are relative to the screen or to the

unnamed_arg3
  



.. _org.a11y.atspi.Component.GetAccessibleAtPoint:

org.a11y.atspi.Component.GetAccessibleAtPoint
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetAccessibleAtPoint (
      IN x i,
      IN y i,
      IN coord_type u,
      OUT unnamed_arg3 (so)
    )




component's top level window; see the description.

Gets a reference to the accessible object that contains an (x, y) pair of
coordinates.

The ``coord_type`` values are as follows, and correspond to AtkCoordType:

0 - Coordinates are relative to the screen.
1 - Coordinates are relative to the component's toplevel window.
2 - Coordinates are relative to the component's immediate parent.

Returns: A DBus name and object reference (so) for the sought object, or a null
object reference "/org/a11y/atspi/null" if there is no object at the specified
coordinates.



x
  X coordinate of point.

y
  Y coordinate of point.

coord_type
  Whether the coordinates are relative to the screen or to the

unnamed_arg3
  



.. _org.a11y.atspi.Component.GetExtents:

org.a11y.atspi.Component.GetExtents
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetExtents (
      IN coord_type u,
      OUT unnamed_arg1 (iiii)
    )




component's top level window; see the description.

Queries the pixel extents of a component.

The ``coord_type`` values are as follows, and correspond to AtkCoordType:

0 - Coordinates are relative to the screen.
1 - Coordinates are relative to the component's toplevel window.
2 - Coordinates are relative to the component's immediate parent.

Returns: a tuple (x, y, width, height) corresponding to the rectangle for the
component's extents.



coord_type
  Whether the coordinates are relative to the screen or to the

unnamed_arg1
  



.. _org.a11y.atspi.Component.GetPosition:

org.a11y.atspi.Component.GetPosition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetPosition (
      IN coord_type u,
      OUT x i,
      OUT y i
    )




component's top level window; see the description.

Queries the upper-left position of a component.

The ``coord_type`` values are as follows, and correspond to AtkCoordType:

0 - Coordinates are relative to the screen.
1 - Coordinates are relative to the component's toplevel window.
2 - Coordinates are relative to the component's immediate parent.

Returns: (x, y) coordinates of the component's upper-left corner.



coord_type
  Whether the coordinates are relative to the screen or to the

x
  

y
  



.. _org.a11y.atspi.Component.GetSize:

org.a11y.atspi.Component.GetSize
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetSize (
      OUT width i,
      OUT height i
    )




Queries the pixel size of a component.

Returns: (width, height) of the component's rectangular area.



width
  

height
  



.. _org.a11y.atspi.Component.GetLayer:

org.a11y.atspi.Component.GetLayer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetLayer (
      OUT unnamed_arg0 u
    )



Queries the UI layer at which a component is rendered, which can help in
determining when components occlude one another.

The layer of a component indicates its relative stacking order with respect to the
onscreen visual representation of the UI.  The layer index, in combination
with the component's extents, can be used to compute the visibility of
all or part of a component.  This is important in programmatic determination of
region-of-interest for magnification, and in flat screen review models of the
screen, as well as for other uses.  Objects residing in two of the
Layer categories support further z-ordering information, with
respect to their peers in the same layer: namely, WINDOW and
MDI.  Relative stacking order for other objects within the same layer
is not available; the recommended heuristic is first child paints first. In other
words, assume that the first siblings in the child list are subject to being
overpainted by later siblings if their bounds intersect. The order of layers, from
bottom to top, is as follows:

0 - INVALID: Error condition.

1 - BACKGROUND: Reserved for the desktop background; this is the bottom-most
layer, over which everything else is painted.

2 - CANVAS: The 'background' layer for most content renderers and UI component containers.

3 - WIDGET: The layer in which the majority of ordinary 'foreground' widgets reside.

4 - MDI: A special layer between CANVAS and WIDGET, in which the 'pseudo-windows'
(e.g. the Multiple-Document Interface frames) reside.  See the GetMDIZOrder
method.

5 - POPUP: Layer for popup window content, above WIDGET.

6 - OVERLAY: The topmost layer.

7 - WINDOW: The layer in which a toplevel window background usually resides.



unnamed_arg0
  



.. _org.a11y.atspi.Component.GetMDIZOrder:

org.a11y.atspi.Component.GetMDIZOrder
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetMDIZOrder (
      OUT unnamed_arg0 n
    )



Queries the Z stacking order of a component which is in the MDI or WINDOW layer,
per the GetLayer method.  Bigger z-order numbers are nearer the top.

Returns: The z order of the component, or -1 if it is not in the MDI layer.



unnamed_arg0
  



.. _org.a11y.atspi.Component.GrabFocus:

org.a11y.atspi.Component.GrabFocus
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GrabFocus (
      OUT unnamed_arg0 b
    )



Attempts to set the keyboard input focus to the component.

Returns: true if successful, or false otherwise.



unnamed_arg0
  



.. _org.a11y.atspi.Component.GetAlpha:

org.a11y.atspi.Component.GetAlpha
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetAlpha (
      OUT unnamed_arg0 d
    )



Gets the opacity/alpha value of a component, if alpha blending is in use.

Returns: opacity value in the [0.0, 1.0] range.  0 is fully transparent and 1 is fully opaque.



unnamed_arg0
  



.. _org.a11y.atspi.Component.SetExtents:

org.a11y.atspi.Component.SetExtents
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    SetExtents (
      IN x i,
      IN y i,
      IN width i,
      IN height i,
      IN coord_type u,
      OUT unnamed_arg5 b
    )




component's top level window; see the description.

Moves and resizes the component.

The ``coord_type`` values are as follows, and correspond to AtkCoordType:

0 - Coordinates are relative to the screen.
1 - Coordinates are relative to the component's toplevel window.
2 - Coordinates are relative to the component's immediate parent.

Returns: true if successful, or false otherwise.



x
  the new horizontal position to which the component should be moved.

y
  the new vertical position to which the component should be moved.

width
  the width to which the component should be resized.

height
  the height to which the component should be resized.

coord_type
  Whether the coordinates are relative to the screen or to the

unnamed_arg5
  



.. _org.a11y.atspi.Component.SetPosition:

org.a11y.atspi.Component.SetPosition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    SetPosition (
      IN x i,
      IN y i,
      IN coord_type u,
      OUT unnamed_arg3 b
    )




component's top level window; see the description.

Moves the component to the specified position.

The ``coord_type`` values are as follows, and correspond to AtkCoordType:

0 - Coordinates are relative to the screen.
1 - Coordinates are relative to the component's toplevel window.
2 - Coordinates are relative to the component's immediate parent.

Returns: true if successful, or false otherwise.



x
  the new horizontal position to which the component should be moved.

y
  the new vertical position to which the component should be moved.

coord_type
  Whether the coordinates are relative to the screen or to the

unnamed_arg3
  



.. _org.a11y.atspi.Component.SetSize:

org.a11y.atspi.Component.SetSize
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    SetSize (
      IN width i,
      IN height i,
      OUT unnamed_arg2 b
    )



Resizes the component to the given pixel dimensions.

Returns: true if successful, or false otherwise.



width
  the width to which the component should be resized.

height
  the height to which the component should be resized.

unnamed_arg2
  



.. _org.a11y.atspi.Component.ScrollTo:

org.a11y.atspi.Component.ScrollTo
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ScrollTo (
      IN type u,
      OUT unnamed_arg1 b
    )



Makes the component visible on the screen by scrolling all necessary parents.

The ``type`` corresponds to AtkScrollType:

0 - TOP_LEFT: Scroll the object vertically and horizontally to bring
its top left corner to the top left corner of the window.

1 - BOTTOM_RIGHT: Scroll the object vertically and horizontally to
bring its bottom right corner to the bottom right corner of the window.

2 - TOP_EDGE: Scroll the object vertically to bring its top edge to
the top edge of the window.

3 - BOTTOM_EDGE: Scroll the object vertically to bring its bottom
edge to the bottom edge of the window.

4 - LEFT_EDGE: Scroll the object vertically and horizontally to bring
its left edge to the left edge of the window.

5 - RIGHT_EDGE: Scroll the object vertically and horizontally to
bring its right edge to the right edge of the window.

6 - ANYWHERE: Scroll the object vertically and horizontally so that
as much as possible of the object becomes visible. The exact placement is
determined by the application.

Returns: true if successful, or false otherwise.



type
  How to position the component within its parent; see the description.

unnamed_arg1
  



.. _org.a11y.atspi.Component.ScrollToPoint:

org.a11y.atspi.Component.ScrollToPoint
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    ScrollToPoint (
      IN coord_type u,
      IN x i,
      IN y i,
      OUT unnamed_arg3 b
    )




component's top level window; see the description.
``x``: X coordinate within the component to make visible.
``y``: Y coordinate within the component to make visible.

Similar to the ScrollTo method, but makes a specific point from the component
visible in its parent.

The ``coord_type`` values are as follows, and correspond to AtkCoordType:

0 - Coordinates are relative to the screen.
1 - Coordinates are relative to the component's toplevel window.
2 - Coordinates are relative to the component's immediate parent.

Returns: true if successful, or false otherwise.



coord_type
  Whether the coordinates are relative to the screen or to the

x
  

y
  

unnamed_arg3
  


