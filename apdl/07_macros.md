# Macros

## General
```
/input, mac_name, mac                   # execute a macro
*use, mac_name.mac, 'comp_name`, 1, 360 # use a macro as a function and passes arguments
```

## APDL macro search path
Sequence:
- ANSYS installation APDL dir
- dir(s) in `ANSYS_MACROLIB` env var
- home dir
- current working dir
If search finds both upper- and lowercase files of the same name, the uppercase file is used.


## Use a macro, but check if it exists first
```
my_file='my_file.mac'
/inquire,if_file,exist,my_file
*if,if_file,EQ,1,THEN
        /input,my_file
*endif
```

## Arguments
Assume a component is named "cyclic_m01l". The user will specify: `arg1='cyclic'`, `arg2='m01'`, `arg3='1'`:

```
_comp_name1 = arg1
_comp_name2 = arg2
_comp_name3 = arg3

cmsel,s,%_comp_name1%%_comp_name2%%_comp_name3%
```

