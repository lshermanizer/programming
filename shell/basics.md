## Shell script

### beginning
```
#!/bin/sh
#
```

### variables, loop
```
xs=(1.00 2.00)
ys=(200 300)
dir=./

for x in "${xs[@]}"; do
    for y in "${ys[@]}"; do
      echo "x=$x, y=$y"
    done
done
```

### find
Find a file whose name match a certain pattern, and then return the name of directory it's in:
```
file=`find $hashdir -name "*$x*$y*.dwm*" -exec dirname {} \; |head -n1`
```
