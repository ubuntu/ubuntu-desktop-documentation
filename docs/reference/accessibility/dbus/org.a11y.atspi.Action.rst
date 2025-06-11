.. _org.a11y.atspi.Action:

=====================
org.a11y.atspi.Action
=====================

-----------
Description
-----------

.. _org.a11y.atspi.Action Description:

Allows exploring and invoking the actions of a user-actionable UI component.

For example, a button may expose a "click" action; a popup menu may expose an "open"
action.  Components which are not "passive" providers of UI information should
implement this interface, unless there is a more specialized interface for
interaction like org.a11y.atspi.Text or org.a11y.atspi.Value.



.. _org.a11y.atspi.Action Properties:

----------
Properties
----------

.. _org.a11y.atspi.Action:NActions:

org.a11y.atspi.Action:NActions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    NActions readable i


returns the number of available actions.
By convention, if there is more than one action available, the first one is
considered the "default" action of the object.



.. _org.a11y.atspi.Action Methods:

-------
Methods
-------

.. _org.a11y.atspi.Action.GetDescription:

org.a11y.atspi.Action.GetDescription
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetDescription (
      IN index i,
      OUT unnamed_arg1 s
    )



Returns: The localized description for the action at the specified ``index``.  For
example, a screen reader will read out this description when the user asks for
extra detail on an action.  For example, "Clicks the button" for the "click"
action of a button.



index
  0-based index of the action to query.

unnamed_arg1
  



.. _org.a11y.atspi.Action.GetName:

org.a11y.atspi.Action.GetName
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetName (
      IN index i,
      OUT unnamed_arg1 s
    )



Returns: Machine-readable name for the action at the specified ``index``.



index
  0-based index of the action to query.

unnamed_arg1
  



.. _org.a11y.atspi.Action.GetLocalizedName:

org.a11y.atspi.Action.GetLocalizedName
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetLocalizedName (
      IN index i,
      OUT unnamed_arg1 s
    )



Returns: A short, localized name for the action at the specified ``index``.  This is
what screen readers will read out during normal navigation.  For example, "Click"
for a button.



index
  0-based index of the action to query.

unnamed_arg1
  



.. _org.a11y.atspi.Action.GetKeyBinding:

org.a11y.atspi.Action.GetKeyBinding
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetKeyBinding (
      IN index i,
      OUT unnamed_arg1 s
    )



Gets the keybinding which can be used to activate this action, if one
exists. The string returned should contain localized, human-readable,
key sequences as they would appear when displayed on screen. It must
be in the format "mnemonic;sequence;shortcut".

- The mnemonic key activates the object if it is presently enabled onscreen.
  This typically corresponds to the underlined letter within the widget.
  Example: "n" in a traditional "New..." menu item or the "a" in "Apply" for
  a button.

- The sequence is the full list of keys which invoke the action even if the
  relevant element is not currently shown on screen. For instance, for a menu
  item the sequence is the keybindings used to open the parent menus before
  invoking. The sequence string is colon-delimited. Example: "Alt+F:N" in a
  traditional "New..." menu item.

- The shortcut, if it exists, will invoke the same action without showing
  the component or its enclosing menus or dialogs. Example: "Ctrl+N" in a
  traditional "New..." menu item.

Example: For a traditional "New..." menu item, the expected return value
would be: "N;Alt+F:N;Ctrl+N" for the English locale and "N;Alt+D:N;Strg+N"
for the German locale. If, hypothetically, this menu item lacked a mnemonic,
it would be represented by ";;Ctrl+N" and ";;Strg+N" respectively.

If there is no key binding for this action, return "".



index
  0-based index of the action to query.

unnamed_arg1
  



.. _org.a11y.atspi.Action.GetActions:

org.a11y.atspi.Action.GetActions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    GetActions (
      OUT unnamed_arg0 a(sss)
    )



Returns: an array of (localized_name, localized description, keybinding) for the
actions that an object supports.  See the GetKeyBinding method for a description
of that field's syntax.

This is equivalent to using the methods GetLocalizedName, GetDescription,
GetKeyBinding for each action, but with a single call and thus less DBus traffic.

By convention, if there is more than one action available, the first one is
considered the "default" action of the object.



unnamed_arg0
  



.. _org.a11y.atspi.Action.DoAction:

org.a11y.atspi.Action.DoAction
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    DoAction (
      IN index i,
      OUT unnamed_arg1 b
    )



Performs the specified action on the object.

Returns: true on success, false otherwise.



index
  0-based index of the action to perform.

unnamed_arg1
  


