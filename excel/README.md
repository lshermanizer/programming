


## Table of contents

- [Navigate workbook](./navigate_workbook.md)
- [logical statements](./logical_statements.md): `and`, `or`, `not`, `if`, `iferror`, `isblank`, `isnumber`, `istext`, `iserror`, `iseven`, `isodd`, `islogical`, `isformula`
- [Lookup functions](./lookup_and_references.md): `left`, `search`, `row`, `column`, `vlookup`, `hlookup`, `xlookup`, `index`, `match`, `choose`, `offset`.
- [Text functions](./text_functions.md): `trim`, `upper`, `lower`, `proper`, `&` (concatenate), `left`, `mid`, `right`, `len`, `text`, `value`, `search`, `substitute`
- [Date and time functions](./date_and_time.md): `datevalue` and `timevalue`, `today()` and `now()`, `eomonth`, `yearfrac`, `weekday`, `workday`, `networkdays`, and `datedif`
- [Dynamic arrays](./dynamic_arrays.md): spill range, `sort`, `sortby`, `filter`, `unique`, `sequence`, `randarray`, `frequency`, `transpose`, use `choose` to combine dynamic arrays, and use `let` to increase formula readability


```
Base!C4:C25   =  a vector of values

Avoidance!C10 =  target value

This formula returns the value from the vector that is cloest (in absolute) to the target:

=INDEX(Base!C4:C25, MATCH(MIN(ABS(Base!C4:C25-Avoidance!C10)),ABS(Base!C4:C25-Avoidance!C10),0))
```


## Data validation
can be used to create drop-down menus.

## Table
Formatting data as a table enables `sructured references` like columns in Pandas.


## Tips

On a cell, right click `Format Cells` -> Set data type to `;;;` to hide it.

Use `named arrays` to speed up references to a certain data block.


Use `Formulas` -> `Formula Auditing` -> `Trace Precedents` and `Trace Dependents` to identify related cells. It is also helpful to identify where error happens. `Evaluate Formula` is useful to breakdown complex/unfamiliar formulas.

`Ctrl + G` -> `Specials...` -> Toggle on `Formulas` and keep all options toggled -> This shows all cells the have formulas 


Function shortcuts:

- `F1`: (1) Launch Excel help pane, (2) If in a dialogue window, open a browser page with specific help info 
- `F2`: Go to edit mode of the active cell
- `F4`: Two functions (1) repeat the last action taken, (2) toggle between A1, $A$1, A$1, $A1
- `F9`: Calculate all workbook formula. Change `Calculation Options` can change whether formulas are automatically executed (default behavior) or only when asked.

Alt key shortcuts:
- Quick access to tools from the ribbon menu
