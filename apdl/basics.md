# APDL Basics

## Command line arguments
```
ansys182 -g -d 3d
ansys182 -pp -np 2 -b <script.mac> output.log
```

Note that the ANSYS log file `jobname.log` can be used an input file `/inp,jobname,log` to rerun the analysis. It will be "messy" with many graphic commands (`/view`, `/focus`, `/dist`, etc.).  

---------------

## Commands through ANSYS GUI

```
/input, mac_name, mac                   # execute a macro
*use, mac_name.mac, 'comp_name`, 1, 360 # use a macro as a function and passes arguments
```

--------------------------

## DB
ANSYS DB is a snapshot of what's in the memory at the time of save.

If `jobname.db` already exists and I save again, the old one will be copied to `jobname.dbb` as a back-up.

`fini` then `/clear` clears the current memory. It is equivalent to existing and then re-entering.

------------------

## File management
```
/filname,my_job_name              ! define jobname. defaults to `file` and cannot exceed 32 characters
/assign,emat,my_job_name,my_emat  ! define name and extension of an ANSYS file away from default
*get,jname,active,,jobnam         ! get current jobname

```

Good practice to use descriptive job name. Good practice to keep `.log`, `.db`, `.rst`, and `.s01`, `.s02`, ... (load step files).


--------------------

## Useful commands

```
/nerr, 100, 100, off  ! by default only the first 5 messages will be print. this relaxes that 

/stat, global
/stat, solu

*ask,Par,Query,Dval
*ask,tref,reference temperature,70 ! prompt user to enter reference temperature (default to 70)
```

---------------

## APDL language: parameters
Parameter name must begin with a letter (underscore as starting character is reserved for ANSYS use), cannot exceed 32 characters, and are not case-sensitive. 
```
Rin=2
Rout=3
dr=Rout-Rin
pi=acos(-1)
dArea=pi*dr**2
jobname='project_name'

nid=192302
nsel,s,node,,nid              ! use of parameter in a command
*get,xval_nid,node,nid,loc,x  ! retrieve x coordinate value of node # nid to parameter xval_nid
*stat,xval_nid                ! display
*vwrite,nid,xval_nid
('X location for node ', F4.0, ' is ', F8.2)  ! this will be printed in the output window
```

-----------

## APDL macro search path
Sequence:
- ANSYS installation APDL dir
- dir(s) in `ANSYS_MACROLIB` env var
- home dir
- current working dir
If search finds both upper- and lowercase files of the same name, the uppercase file is used.

----------------

## Abbreviations
Commands are separated by `$`. If `$` is used, the whole series of commands needs to be enclosed in single quotes.
```
*abbr,plot_temp,'/pbf,temp,,1$eplot'
abbsav  ! save abbreviations to an ASCII file
abbres  ! restore abbreviations
```

At start, ANSYS reads a start file `startxx.ans` (xx is revision number) following the seartch path sequence described above. Ususally abbreviation definitions can be put here.

