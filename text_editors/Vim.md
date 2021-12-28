
### Commands
```
i     -> insert
A     -> append to the end of line
ESC   -> return to normal mode
x     -> delete a character
dw    -> delete (cut) a word
d3w   -> delete 3 words (d: operator, 3: repeat the motion 3 times, w: motion)
de    -> delete to the end of current word
d$    -> delete to end of line
dd    -> delete a line
u     -> undo
U     -> undo all changes on a line
ctrl+R -> undo the undo's
p     -> paste after cursor
r(*)  -> e.g. rq will replace the current character with "q"
ce    -> remove the current word & await user input to replace
c$    -> remove to end of line & await user input
Ctrl+G -> open file status
G     -> go to bottom of file
gg    -> go to beginning of file
100G  -> go to line #100 jof file
/     -> followed by keyword to search. "n" to go to next. "N" to go backward.
?     -> search backward
Ctrl+O -> go back to last point in file
Ctrl+I -> go forward to 
%       -> find matching half of the parathesis
:s/old/new/g        -> change all instances of "old" to "new" on current line
:%s/old/new/g       -> whole file
:100,200s/old/new/g -> from line # 100 to # 200
:%s/old/new/gc      -> whole file with prompt
```

### Change color scheme:

Syntax = `:colo [colorscheme_name]` e.g. `:colo slate`

### .vimrc setting
```
" color scheme
colorscheme slate

" syntax highlighting
syntax on

" show line numbers
set number
```
