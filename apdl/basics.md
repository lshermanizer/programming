### Command line arguments
```
ansys182 -g -d 3d
ansys182 -pp -np 2 -b <script.mac> output.log
```

### Commands through ANSYS GUI

```
/input, mac_name, mac                   # execute a macro
*use, mac_name.mac, 'comp_name`, 1, 360 # use a macro as a function and passes arguments
```


### DB
ANSYS DB is a snapshot of what's in the memory at the time of save.

If `jobname.db` already exists and I save again, the old one will be copied to `jobname.dbb` as a back-up.

`fini` then `/clear` clears the current memory. It is equivalent to existing and then re-entering.


### File management
```
/filname,my_job_name              ! define jobname. defaults to `file` and cannot exceed 32 characters
/assign,emat,my_job_name,my_emat  ! define name and extension of an ANSYS file away from default
*get,jname,active,,jobnam         ! get current jobname

```

Good practice to use descriptive job name. Good practice to keep `.log`, `.db`, `.rst`, and `.s01`, `.s02`, ... (load step files).


### Useful commands

```
/nerr, 100, 100, off ! by default only the first 5 messages will be print. this relaxes that 

/stat, global
/stat, solu
```
