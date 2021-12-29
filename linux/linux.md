
## General

Look at current users: `w`

Check host information: `top`, `cat /proc/cpuinfo`

## View image

`gthumb` or `animate`


## Split/merge files

```
tar -cvf folder.tar folder/             # create a tar ball
split -b 1G folder.tar folder.tar.part  # split it to several parts, 1G each
cat folder.tar.part* > folder.tar       # merge parts back into one
```

## File transfer

GUI: `winscp`

Command line: `scp username@hostname:/file/path/on/host.txt /local/locaton/.`

