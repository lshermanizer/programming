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

/eshape,1     ! The /ESHAPE command allows beams, shells, current sources, and certain special-purpose elements
              ! or elements with special options to be displayed as solids with the shape
              ! determined from the real constants, section types, or other information.

/view,1,1,1,1               ! isometric view
```

## change background color to white
```
/RGB,INDEX,100,100,100, 0
/RGB,INDEX, 80, 80, 80,13
/RGB,INDEX, 60, 60, 60,14
/RGB,INDEX, 0, 0, 0,15
```
