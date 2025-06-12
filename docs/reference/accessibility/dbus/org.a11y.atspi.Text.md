# org.a11y.atspi.Text

 

## Properties

### org.a11y.atspi.Text:CharacterCount {#org.a11y.atspi.Text:CharacterCount}

    CharacterCount readable i

### org.a11y.atspi.Text:CaretOffset {#org.a11y.atspi.Text:CaretOffset}

    CaretOffset readable i

## Methods {#org.a11y.atspi.Text Methods}

### org.a11y.atspi.Text.GetStringAtOffset {#org.a11y.atspi.Text.GetStringAtOffset}

    GetStringAtOffset (
      IN offset i,
      IN granularity u,
      OUT unnamed_arg2 s,
      OUT startOffset i,
      OUT endOffset i
    )

offset

granularity

unnamed_arg2

startOffset

endOffset

### org.a11y.atspi.Text.GetText {#org.a11y.atspi.Text.GetText}

    GetText (
      IN startOffset i,
      IN endOffset i,
      OUT unnamed_arg2 s
    )

startOffset

endOffset

unnamed_arg2

### org.a11y.atspi.Text.SetCaretOffset {#org.a11y.atspi.Text.SetCaretOffset}

    SetCaretOffset (
      IN offset i,
      OUT unnamed_arg1 b
    )

offset

unnamed_arg1

### org.a11y.atspi.Text.GetTextBeforeOffset {#org.a11y.atspi.Text.GetTextBeforeOffset}

    GetTextBeforeOffset (
      IN offset i,
      IN type u,
      OUT unnamed_arg2 s,
      OUT startOffset i,
      OUT endOffset i
    )

offset

type

unnamed_arg2

startOffset

endOffset

### org.a11y.atspi.Text.GetTextAtOffset {#org.a11y.atspi.Text.GetTextAtOffset}

    GetTextAtOffset (
      IN offset i,
      IN type u,
      OUT unnamed_arg2 s,
      OUT startOffset i,
      OUT endOffset i
    )

Returns the text at the given offset. Deprecated: Use GetStringAtOffset.

offset

type

unnamed_arg2

startOffset

endOffset

### org.a11y.atspi.Text.GetTextAfterOffset {#org.a11y.atspi.Text.GetTextAfterOffset}

    GetTextAfterOffset (
      IN offset i,
      IN type u,
      OUT unnamed_arg2 s,
      OUT startOffset i,
      OUT endOffset i
    )

offset

type

unnamed_arg2

startOffset

endOffset

### org.a11y.atspi.Text.GetCharacterAtOffset {#org.a11y.atspi.Text.GetCharacterAtOffset}

    GetCharacterAtOffset (
      IN offset i,
      OUT unnamed_arg1 i
    )

offset

unnamed_arg1

### org.a11y.atspi.Text.GetAttributeValue {#org.a11y.atspi.Text.GetAttributeValue}

    GetAttributeValue (
      IN offset i,
      IN attributeName s,
      OUT unnamed_arg2 s
    )

offset

attributeName

unnamed_arg2

### org.a11y.atspi.Text.GetAttributes {#org.a11y.atspi.Text.GetAttributes}

    GetAttributes (
      IN offset i,
      OUT unnamed_arg1 a{ss},
      OUT startOffset i,
      OUT endOffset i
    )

offset

unnamed_arg1

startOffset

endOffset

### org.a11y.atspi.Text.GetDefaultAttributes {#org.a11y.atspi.Text.GetDefaultAttributes}

    GetDefaultAttributes (
      OUT unnamed_arg0 a{ss}
    )

unnamed_arg0

### org.a11y.atspi.Text.GetCharacterExtents {#org.a11y.atspi.Text.GetCharacterExtents}

    GetCharacterExtents (
      IN offset i,
      IN coordType u,
      OUT x i,
      OUT y i,
      OUT width i,
      OUT height i
    )

offset

coordType

x

y

width

height

### org.a11y.atspi.Text.GetOffsetAtPoint {#org.a11y.atspi.Text.GetOffsetAtPoint}

    GetOffsetAtPoint (
      IN x i,
      IN y i,
      IN coordType u,
      OUT unnamed_arg3 i
    )

x

y

coordType

unnamed_arg3

### org.a11y.atspi.Text.GetNSelections {#org.a11y.atspi.Text.GetNSelections}

    GetNSelections (
      OUT unnamed_arg0 i
    )

unnamed_arg0

### org.a11y.atspi.Text.GetSelection {#org.a11y.atspi.Text.GetSelection}

    GetSelection (
      IN selectionNum i,
      OUT startOffset i,
      OUT endOffset i
    )

selectionNum

startOffset

endOffset

### org.a11y.atspi.Text.AddSelection {#org.a11y.atspi.Text.AddSelection}

    AddSelection (
      IN startOffset i,
      IN endOffset i,
      OUT unnamed_arg2 b
    )

startOffset

endOffset

unnamed_arg2

### org.a11y.atspi.Text.RemoveSelection {#org.a11y.atspi.Text.RemoveSelection}

    RemoveSelection (
      IN selectionNum i,
      OUT unnamed_arg1 b
    )

selectionNum

unnamed_arg1

### org.a11y.atspi.Text.SetSelection {#org.a11y.atspi.Text.SetSelection}

    SetSelection (
      IN selectionNum i,
      IN startOffset i,
      IN endOffset i,
      OUT unnamed_arg3 b
    )

selectionNum

startOffset

endOffset

unnamed_arg3

## org.a11y.atspi.Text.GetRangeExtents {#org.a11y.atspi.Text.GetRangeExtents}

    GetRangeExtents (
      IN startOffset i,
      IN endOffset i,
      IN coordType u,
      OUT x i,
      OUT y i,
      OUT width i,
      OUT height i
    )

startOffset

endOffset

coordType

x

y

width

height

### org.a11y.atspi.Text.GetBoundedRanges {#org.a11y.atspi.Text.GetBoundedRanges}

    GetBoundedRanges (
      IN x i,
      IN y i,
      IN width i,
      IN height i,
      IN coordType u,
      IN xClipType u,
      IN yClipType u,
      OUT unnamed_arg7 a(iisv)
    )

x

y

width

height

coordType

xClipType

yClipType

unnamed_arg7

### org.a11y.atspi.Text.GetAttributeRun {#org.a11y.atspi.Text.GetAttributeRun}

    GetAttributeRun (
      IN offset i,
      IN includeDefaults b,
      OUT unnamed_arg2 a{ss},
      OUT startOffset i,
      OUT endOffset i
    )

offset

includeDefaults

unnamed_arg2

startOffset

endOffset

### org.a11y.atspi.Text.GetDefaultAttributeSet {#org.a11y.atspi.Text.GetDefaultAttributeSet}

    GetDefaultAttributeSet (
      OUT unnamed_arg0 a{ss}
    )

unnamed_arg0

### org.a11y.atspi.Text.ScrollSubstringTo {#org.a11y.atspi.Text.ScrollSubstringTo}

    ScrollSubstringTo (
      IN startOffset i,
      IN endOffset i,
      IN type u,
      OUT unnamed_arg3 b
    )

startOffset

endOffset

type

unnamed_arg3

### org.a11y.atspi.Text.ScrollSubstringToPoint {#org.a11y.atspi.Text.ScrollSubstringToPoint}

    ScrollSubstringToPoint (
      IN startOffset i,
      IN endOffset i,
      IN type u,
      IN x i,
      IN y i,
      OUT unnamed_arg5 b
    )

startOffset

endOffset

type

x

y

unnamed_arg5
