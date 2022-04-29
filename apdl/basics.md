### Run an analysis
```
ansys182 -pp -np 2 -b <script.mac> output.log
```

### Commands through ANSYS GUI

```
/input, mac_name, mac                   # execute a macro
*use, mac_name.mac, 'comp_name`, 1, 360 # use a macro as a function and passes arguments
```


### Check status
```
/stat, global
/stat, solu
```

### Display
```
/edge,on

/color,elem,1    ! change color of elements

plns,u,sum      ! plot Usum

/cont,,10,0,,10 ! change contour
```
