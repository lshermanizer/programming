



```
Base!C4:C25   =  a vector of values

Avoidance!C10 =  target value

This formula returns the value from the vector that is cloest (in absolute) to the target:

=INDEX(Base!C4:C25, MATCH(MIN(ABS(Base!C4:C25-Avoidance!C10)),ABS(Base!C4:C25-Avoidance!C10),0))
```

## Functions

`left` returns the first few characters.

`search` returns the index at which the searched character is found. For example use it within the `left` function argument to find the characters before the `@` sign: i`=LEFT(J2,SEARCH("@",J2)-1)`


## Tips

`Ctrl + G` -> `Specials...` -> Toggle on `Formulas` and keep all options toggled -> This shows all cells the have formulas 

Use `Formulas` -> `Formula Auditing` -> `Trace Precedents` and `Trace Dependents` to identify related cells. It is also helpful to identify where error happens
