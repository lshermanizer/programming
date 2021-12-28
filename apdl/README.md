### Parameters
```
# specify a parameter
run_analysis=1 
analysis_name='analysis'

# specify an array
Nnd=20 
*dim,nodal_dimater,array,Nnd,1
nodal_diameter( 1,1)=1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18 ! up to 18 values every single
nodal_diameter(19,1)=19,20

```

### Misc
```
parsav,all,par,sav ! save all parameters
parres,change,par,sav ! read parameters to add to / replace current ones

/filname,my_file_name ! change jobname for the analysis (default is file)
*get,jname,active,,jobnam ! get current jobname


my_file='my_file.mac'
/inquire,if_file,exist,my_file
*if,if_file,EQ,1,THEN
        /input,my_file
*endif

```


### Arguments
Assume a component is named "cyclic_m01l". The user will specify: `arg1='cyclic'`, `arg2='m01'`, `arg3='1'`:

```
_comp_name1 = arg1
_comp_name2 = arg2
_comp_name3 = arg3

cmsel,s,%_comp_name1%%_comp_name2%%_comp_name3%

```

### Load solution
```
/post1
file,modal_solution,rst
set,first
```


### Get a specific result from solution
```
etable, tab01, s, eqv !create a table with elemental von Mises stress
esort, etab, tab01, 1 !1/0=sort in ascending/descending order
pretab, tab01         !print the table
*get, max_seqv_val, sort,, max ! read max stress into parameter "max_seqv_val"
*get, max_seqv_elm, sort,,imax ! read element ID at which the max stress occurs into parameter "max_seqv_elm"

/output, max_seqv_loc, out     ! direct the following output to a file "max_seqv_loc.out"
*get, max_seqv_x, elem, max_seqv_elem, cent, x    ! xloc
*get, max_seqv_y, elem, max_seqv_elem, cent, y    ! xloc
*get, max_seqv_z, elem, max_seqv_elem, cent, z    ! xloc
/output
```


### Coordinates
`csys,6`: z is radial, x is axial pointing downstream
