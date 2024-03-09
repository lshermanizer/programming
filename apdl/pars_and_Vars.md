# Parameters and variables


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


## Specify parameters/variables
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

## get all parameters
```
parsav,all,par,sav      ! save all parameters
parres,change,par,sav   ! read parameters to add to / replace current ones
```

## get components
```
cmlist
cmwrite,components,txt
```

## get model parameters
```
*get,nnode,node,,count      ! get node count, store in "nnode"
*get,Ux_node1,node,1,u,x    ! get Ux at node #1, store in "Ux_node1"
```

## get X's of all elements into array
```
*get,nelem,elem,,count
*dim,xelem,array,nelem
old_elid = -1
cnt = 0
*do,j,1,nelem,1
    elid = elnext(old_elid)
    old_elid = elid
    *get,xelem(j),elem,elid,cent,x
*enddo

output_file='output'
/delete,output_file,txt
*cfopen,output_file,txt,,apend
*vwrite,xelem(1)
(1G)
*cfclose
```
