# APDL Basics

## Launch ANSYS with a script

```
ansys182 -g -d 3d    ! interactively
ansys182 -pp -np 2 -b <script.mac> output.log  ! from command line
```

Note that the ANSYS log file `jobname.log` can be used an input file `/inp,jobname,log` to rerun the analysis. It will be "messy" with many graphic commands (`/view`, `/focus`, `/dist`, etc.).  

## General info
- DB
  - ANSYS DB is a snapshot of what's in the memory at the time of save.
  - If `jobname.db` already exists and I save again, the old one will be copied to `jobname.dbb` as a back-up.

## General commands

```
fini
/clear                ! clears the current memory. Equivalent to existing and then re-entering.

/nerr, 100, 100, off  ! by default only the first 5 messages will be print. this relaxes that 

/stat, global
/stat, solu
```

## Abbreviations
Commands are separated by `$`. If `$` is used, the whole series of commands needs to be enclosed in single quotes.
```
*abbr,plot_temp,'/pbf,temp,,1$eplot'
abbsav  ! save abbreviations to an ASCII file
abbres  ! restore abbreviations
```

At start, ANSYS reads a start file `startxx.ans` (xx is revision number) following the seartch path sequence described above. Ususally abbreviation definitions can be put here.

