
### list
```
nlist
elist
etlist      ! list all element types
rlist,5     ! list all real constants with element type 5 
mplist      ! list all materials
```

### visualize
```
/pnum,mat,1 ! display material numbers
```

### make selection
```
esel,s,,,comp_name
esel,s,mat,,1
esel,s,type,,5
esel,s,ename

cmsel,s,comp_name

nsel,r,corner   ! select corner nodes only
nsel,r,ext      ! select external nodes only
```

### make selection interactively
```
nsel,p
ndist,p             ! pick 2 nodes to meausre distance
nid=node(1, 0, 1)   ! this will return node id that is closest to the given coordinates
```

### this sequence of selections
```
alls
nsle ! select all physical nodes
esln ! select all elements associated with the notes, including virtual elements if any
nsle ! select all nodes associated with the elements, now including both physical and virtual nods
```

### delete nodes and elements
```
esel,s,type,,5
edel,all
ndel,all
etdele,5 ! delete element type 5
```

### make modifications
```
rmodif  ! real constants
emodif  ! element 
keyopt  ! key option
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
