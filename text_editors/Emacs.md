```
Ctrl 	e.g. C-f	Ctrl + f
Meta	e.g. M-s	Meta + s (Alt)
```

## Emacs commands

- C-x C-c : end the Emacs session
- Ctrl+K: delete from the cursor to the end of the line.
- C-0 C-k: delete from the cursor to the beginning of the line.
- http://physics.clarku.edu/sip/tutorials/intro_emacs.html
- delete from the cursor to the end of the file: (1) C-space (set-mark), (2) M-> (end-of-buffer), (3) C-w (kill-region)
- C-u M-! : enter current time stamp


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
