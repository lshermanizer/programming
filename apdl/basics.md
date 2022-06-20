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


### Check status
```
/stat, global
/stat, solu
```

### Display
```
/edge,on

/color,elem,2               ! change color of elements to 2 (magenta)
/color,defa                 ! reset to the default color setting
/color,cm,2,component_name  ! set color 2 (magenta) to a specific component (component_name)

/number,1                   ! sets behavior for /pnum. 1=display color, not number; 0=display color and number; etc.
/pnum,mat,1                 ! color by material number
/pnum,mat,0                 ! turn it off

plns,u,sum                  ! plot Usum

/cont,,10,0,,10             ! change contour
```
