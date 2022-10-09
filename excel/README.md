



```
Base!C4:C25   =  a vector of values

Avoidance!C10 =  target value

This formula returns the value from the vector that is cloest (in absolute) to the target:

=INDEX(Base!C4:C25, MATCH(MIN(ABS(Base!C4:C25-Avoidance!C10)),ABS(Base!C4:C25-Avoidance!C10),0))
```

## Functions

`left` returns the first few characters.

`search` returns the index at which the searched character is found. For example use it within the `left` function argument to find the characters before the `@` sign: i`=LEFT(J2,SEARCH("@",J2)-1)`

### Logical statements

`and(B2>0, C2=='True')` and `or` include multiple logical tests at once. They can be used together with `if`, e.g.: `if(and(B2>32, C2=='True'), 'Ok')`

`not` function is the same as the `<>` operator to test whether a logical statement is not true.

`iferror(value, value_if_error)` function replaces default error messages such as `#N/A`, `#REF!`, etc. Use it on the outer layer of a function.

Common `is` statements: `isblank`, `isnumber`, `istext`, `iserror`, `iseven`, `isodd`, `islogical`, `isformula`




## Tips

Use `named arrays` to speed up references to a certain data block.


Use `Formulas` -> `Formula Auditing` -> `Trace Precedents` and `Trace Dependents` to identify related cells. It is also helpful to identify where error happens. `Evaluate Formula` is useful to breakdown complex/unfamiliar formulas.

`Ctrl + G` -> `Specials...` -> Toggle on `Formulas` and keep all options toggled -> This shows all cells the have formulas 

Navigate a workbook:

- `Ctrl + Arrow`: jump to last cell in the direction of arrow
- `Ctrl + Shift + Arrow`: same as above but also selecting all the data
- `Ctrl + Home/End`: jump to `top left` or `bottom right` cell
- `Ctrl + .`: within an existing selection, cycle through 4 corners
- `Ctrl + PgUp/Dn`: cycle through sheets

Function shortcuts:

- `F1`: (1) Launch Excel help pane, (2) If in a dialogue window, open a browser page with specific help info 
- `F2`: Go to edit mode of the active cell
- `F4`: Two functions (1) repeat the last action taken, (2) toggle between A1, $A$1, A$1, $A1
- `F9`: Calculate all workbook formula. Change `Calculation Options` can change whether formulas are automatically executed (default behavior) or only when asked.

Alt key shortcuts:
- Quick access to tools from the ribbon menu
