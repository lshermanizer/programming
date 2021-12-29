`M` = `Alt`, `C` = `Ctrl`

## Add

Add `stuff` to end of all lines: `M-< M-x replace-regexp $ stuff`

Add `stuff` to beginning of all lines: `M-< M-x replace-regexp ^ stuff`

## Delete

Delete from cursor to the beginning of line: `C-0 C-k`

Delete from cursor to the end of line: `C-k`

## Move

Move cursor to the beginning/end of file: `Esc <`, `Esc >`

## Replace

Query replace: `Cltr + Alt + 5`

Bulk replace: `M-x`

## Select and cut

Select a region of text to cut: Move cursor to beginning, `C-space` to set mark, move cursor to the end, `C-w` to cut

Select a box region to cut: Set marker on one corner, move cursor to another corner, `C-x r k` to cut (i.e. rectangle kill)