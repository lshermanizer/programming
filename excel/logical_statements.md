
## Logical statements

`and(B2>0, C2=='True')` and `or` include multiple logical tests at once. They can be used together with `if`, e.g.: `if(and(B2>32, C2=='True'), 'Ok')`

`not` function is the same as the `<>` operator to test whether a logical statement is not true.

`iferror(value, value_if_error)` function replaces default error messages such as `#N/A`, `#REF!`, etc. Use it on the outer layer of a function.

Common `is` statements: `isblank`, `isnumber`, `istext`, `iserror`, `iseven`, `isodd`, `islogical`, `isformula`
