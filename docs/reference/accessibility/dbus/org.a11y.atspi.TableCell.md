# org.a11y.atspi.TableCell

 

## Properties[]{#org.a11y.atspi.TableCell Description} {#org.a11y.atspi.TableCell Properties}

### org.a11y.atspi.TableCell:ColumnSpan {#org.a11y.atspi.TableCell:ColumnSpan}

    ColumnSpan readable i

### org.a11y.atspi.TableCell:Position {#org.a11y.atspi.TableCell:Position}

    Position readable (ii)

### org.a11y.atspi.TableCell:RowSpan {#org.a11y.atspi.TableCell:RowSpan}

    RowSpan readable i

### org.a11y.atspi.TableCell:Table {#org.a11y.atspi.TableCell:Table}

    Table readable (so)

## Methods {#org.a11y.atspi.TableCell Methods}

### org.a11y.atspi.TableCell.GetRowColumnSpan {#org.a11y.atspi.TableCell.GetRowColumnSpan}

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

### org.a11y.atspi.TableCell.GetColumnHeaderCells {#org.a11y.atspi.TableCell.GetColumnHeaderCells}

    GetColumnHeaderCells (
      OUT unnamed_arg0 a(so)
    )

Returns a list of the table cell\'s column header cells.

unnamed_arg0

### org.a11y.atspi.TableCell.GetRowHeaderCells {#org.a11y.atspi.TableCell.GetRowHeaderCells}

    GetRowHeaderCells (
      OUT unnamed_arg0 a(so)
    )

Returns a list of the table cell\'s row header cells.

unnamed_arg0
