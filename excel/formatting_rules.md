# Formatting rules

Home -> Conditional formatting -> New Rule... -> "Use a formula to determine which cells to format".




## Examples:

### highlight every other row with `mod()`

```
=mod(row(),2)=1
```

### format based on another cell

Suppose a 2D data array is C3:G7. Suppose a number is entered in E10. I want to highlight the cell in the data array which matches the number in E10. Select C3:G7, then define conditional formatting using:

```
=C3=$E$10
```

It is important to have `C3` as the relative reference (rather than $C$3) so that it is updated automatically in the selected region.

### format using statistical functions

Suppose a 1D data array in C. Select C3:G7, then define conditional formatting using:

```
=$C2=MAX($C:$C)
```
This would pick the maximum of the column C.

If there are multiple data columns, to highlight the entire row, select the entire 2D data array, and use the same formula above.


### format based on text functions and logical operators

```
=left($A2,1)='I'
```

```
=AND(left($A2,1)='I', $C2>2000)
```