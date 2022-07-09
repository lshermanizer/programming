# Coordinate systems (cs)

Forces, displacements, stresses, etc. direction dependent input and output nodal quantities are interpreted in the nodal coordinate system (nodal csys). Every node has its own nodal csys. The default is paralelle to the global Cartesian csys.

Note that every `element` have its own cs too, for example for composites which may have directionally different properties.

In `/post1`, solutions are reported in results coordinate systems (`rsys`). The default `rsys` is `0` regardless of the nodal cs.

## ANSYS cs

`csys,6`: z is radial, x is axial pointing downstream


## Change the cs of nodes ("rotate the nodes")
```
/psymb,ndir,1   ! visualize cs of selected nodes
csys,201        ! select/activate cs # 201
nrotat,all      ! rotate selected nodes into this cs
```

At symmetric or anti-symmetric boundaries, the nodes are automatically rotated.