
## visualize
```
/pbc,all,0      ! do not show
/pbc,ce,,1      ! show constrained equations (CE)
/pbf,temp,,1    ! show temperature load
/psf,pres,1,1,on    ! show pressure load
/psym,ndir,1    ! show locl cs
cplist          ! list couplings (CP)
celist
dlist           ! list DOF constraints
bflist          ! list body force
sflist          ! list pressure mapped to nodes
sfelist         ! list pressure mapped to elements
```

## set 
```
cmsel,s,elem_comp
cmsel,a,node_comp
cedel,all,all       ! remove all existing CE
ceintf,,all         ! apply CE in all 3 directions

cmsel,s,node_comp
d,all,all           ! apply DOF constraint in all 3 directions

nsel,s,node,,1
csys,201
nrotate,all
f,all,FZ,0          ! apply FZ force on selecte node
```