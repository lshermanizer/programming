# Dynamic arrays

- Legacy Excel: one formula in a cell -> returns one cell.
- Dynamic Excel: one formula in a cell -> returns array of variable sizes i.e. "spills" to many cells.
- Available only in Office 365 subscriptions.
- Backward incompatible - They won't work in older Excel versions.

## spill range

e.g. if the full range is in E2:E10, in a formula it can be referred to as `E2#`. This syntax works in formulas, defined naems, conditional formatting, etc. (Note that it does work directly in charts, but a workaround is to use defined names for a chart.)

Excel does not overwrite by default, so if a spill is blocked it will give a `#SPILL!` error.

Appending a new row does not automatically update the spill range, unless the data is formatted as a `table`.


## `sort`, `sortby`
```
=sort(array, start_index, sort_order, by_col)
```

```
=sort(A2:D10, (3,4), (1,-1))
```
will sort 2D array A2:D10 by the 3rd column in ascending order, and then again sort by 4th column in descending order for rows that have the same value in 3rd column.

The `sortby` works similar to `sort`, except that the sort-by column doesn't live within the 2D array.

```
=sortby(array, sort_by_array, sort_order)
```


## `filter`, `unique`
```
=filter(array, include_logical_test, if_empty)
```

```
=filter(A2:D10, (B2:B10='Clothing')*(C2:C10>5000))
```
By multiplying two logical tests it creates an `and` condition. Similary, use `+` creates an `or` condition.

The `unique` dynamic array function can be used on a single column or multiple data columns.
```
=unique(A2:B10)
```
will return 2 columns with unique combinations of A-B column entries.

The `sort`, `fitler`, and `unique` (and sometimes like `large` to list top N entries) can be combined to slice data.

## `sequence`, `randarray`

```
=sequence(rows, columns, start, step)
```

e.g. `=sequence(10,6,0,5)` will create a 10x6 2D data array starting at 0 and grows with interval of 5. It will go left to right first, then down.

e.g. to list top 3 values from a data column: `=large(A2:A10, sequence(3))`

## `frequency`

```
=frequency(data_array, bins_array)
```
returns occurrences of values within a bin in a dataset. The `bins_array` argument defines the upper limit of the bin.


## `transpose` 

use `transpose()` function to return a dynamic array from a column to a row.


## use `choose` to join dynamic arrays
```
=choose({1,2},F2#,G2#)
```
takes a dynamic array in `F2#` and another dynamic array `G2#` and combine them into a single 2D data array.

This is useful if subsequent operations are necessary on dynamic arrays, for example:
```
=sort(choose({1,2},F2#,G2#),2,-1)
```

## use `let()` to increase formula readability
`let()` is used to declare variable names, assign values, and use within formulas.

```
=let(name1, val1, name2, val2, ..., calculation)
```

```
=let(
industry, UNIQUE(A3:A10),
avgSalary, AVERAGEIFS(D3:D10, A3:A10, industry),
array, CHOOSE({1,2}, industry, avgSalaray),
SORT(array,2,-1)
)
```