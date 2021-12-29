
## General

Look at current users: `w`

Check host information: `top`, `cat /proc/cpuinfo`

## View image

`gthumb` or `animate`

## Command line
- Ctrl+K: delete from the cursor to the end of the line.
- Ctrl+U: delete from the cursor to the beginning of the line.
- Ctrl + a: go to the start of the command line
- Ctrl + e: go to the end of the command line
- Ctrl + k: delete from cursor to the end of the command line
- Ctrl + u: delete from cursor to the start of the command line
- Ctrl + w: delete from cursor to start of word (i.e. delete backwards one word)
- Ctrl + y: paste word or text that was cut using one of the deletion shortcuts (such as the one above) after the cursor
- Ctrl-Y: undo a deletion
- Ctrl + xx: move between start of command line and current cursor position (and back again)
- Alt + b: move backward one word (or go to start of word the cursor is currently on)
- Alt + f:  move forward one word (or go to end of word the cursor is currently on)
- Alt + d: delete to end of word starting at cursor (whole word if cursor is at the beginning of word)


## Split/merge files

```
tar -cvf folder.tar folder/             # create a tar ball
split -b 1G folder.tar folder.tar.part  # split it to several parts, 1G each
cat folder.tar.part* > folder.tar       # merge parts back into one
```

## File transfer

GUI: `winscp`

Command line: `scp username@hostname:/file/path/on/host.txt /local/locaton/.`

