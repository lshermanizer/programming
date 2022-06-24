`/graph,power` power graphics is default. Plots only the visible surfaces, not the interior.


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
