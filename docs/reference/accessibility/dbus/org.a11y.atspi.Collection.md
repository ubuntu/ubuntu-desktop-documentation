# org.a11y.atspi.Collection

## Description

An ordered list of accessible objects, used to avoid iteration or client-side search of the object tree.

## Methods

### org.a11y.atspi.Collection.GetMatches

Gets all objects from the collection matching a given `rule`.



    GetMatches (
      IN rule (aiia{ss}iaiiasib),
      IN sortby u,
      IN count i,
      IN traverse b,
      OUT unnamed_arg4 a(so)
    )

### org.a11y.atspi.Collection.GetMatchesTo 

Gets all objects from the collection, after `current_object`, matching a given `rule`.



    GetMatchesTo (
      IN current_object o,
      IN rule (aiia{ss}iaiiasib),
      IN sortby u,
      IN tree u,
      IN limit_scope b,
      IN count i,
      IN traverse b,
      OUT unnamed_arg7 a(so)
    )

### org.a11y.atspi.Collection.GetMatchesFrom 

Gets all objects from the collection, before `current_object`, matching a given `rule`.



    GetMatchesFrom (
      IN current_object o,
      IN rule (aiia{ss}iaiiasib),
      IN sortby u,
      IN tree u,
      IN count i,
      IN traverse b,
      OUT unnamed_arg6 a(so)
    )

### org.a11y.atspi.Collection.GetActiveDescendant 

Get an active descendant of the given object.



    GetActiveDescendant (
      OUT unnamed_arg0 (so)
    )

