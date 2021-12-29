
## Interactive 
```
>>lookfor atan2
>>help elfun
  Elementary math functions.
>>demo
  Play demos
>>clf
  Clear current figure. 但是不是关闭Figure窗口
```

## Array: scalar, vector, matrix
```
>>size(A); # rows, # columns
>>length(b); # columns 
>>B=B';  #transposing, change from 1x3 to 3x1
>>D=B/A; #array right division, equivalent to B*inv(A)
>>D=A\B; #array left division, equivalent to inv(A)*B
>>D=A.\B; #element by element division (sizes must agree)

>>help elmat
  Matrix functions
>>help arith
  Arithmetic functions
>>help slash
  Matrix division
```


## 3D plots of 2D functions
```
>>[x,y]=meshgrid(-1:0.5:1);

x =

   -1.0000   -0.5000         0    0.5000    1.0000
   -1.0000   -0.5000         0    0.5000    1.0000
   -1.0000   -0.5000         0    0.5000    1.0000
   -1.0000   -0.5000         0    0.5000    1.0000
   -1.0000   -0.5000         0    0.5000    1.0000

y =

   -1.0000   -1.0000   -1.0000   -1.0000   -1.0000
   -0.5000   -0.5000   -0.5000   -0.5000   -0.5000
         0         0         0         0         0
    0.5000    0.5000    0.5000    0.5000    0.5000
    1.0000    1.0000    1.0000    1.0000    1.0000

>>z=x.*exp(-x.^2-y.^2); #Evaluate a 2-D function on the x-y mesh

Plotting a 2D function results in a 3D plot
>>plot3(x,y,z) # lines
>>mesh(x,y,z) #colored parametric mesh (by z)
>>surf(x,y,z) #colored parametric surface (by z)
>>contour(x,y,z) #plot lines on the x-y plane at constant z-values

When plotting 3D data the mesh or surface is colored by the value of the parameter z. It's identical to height above ground.
>>colorbar #get the numerical values for the colors
>>rotate3d on
>>view(-15,28); #set view angle by specifying azimuth and elevation
>>view(0,0); #side view
>>view(0,90); #top view
```