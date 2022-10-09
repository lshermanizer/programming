

## row/rows, column/columns

`row` retuns the row id, i.e. `row(C10)` will return 10.

`rows` returns the total number of rows.

Same concept for `column` and `columns`.


## vlookup, hlookup

`vlookup` and `hlookup` are commonly used to work with 2 different data tables with common fields (they do not have to have the same ordering of data).

Syntax: `vlookup(lookup_x, data_table_xy, col_id_y, [option])` where `option=0` is looking for an exact match or `option=1` looking for an approximate match.

Similar concept for `hlookup` if the `data_table_xy` is transposed.

Be aware of 2 things:

1. the `x` array must be the first column/row of the `data_table_xy` block.

2. if there are multiple matching instances, the first one will be returned. 

Other discussions:

1. `vlookup` can be used with `iferror` to take care of empty values, `iferror(vlookup(lookup_x, data_table_xy, col_id_y, 0), 'No data')`


## index, match

`index` returns the value of a cell identified by row and column id within a given data block (can be 2D), e.g. `index($A$1:$C$3, 2, 2)` will return cell value `aluminum`.

`match` returns the position of a cell within a given data array (cannot be a 2D data block) identified by a value. Syntax is `match("aluminmum", $B$1:$B$3, [option])` will return value `2`. `option=0` will give exact match, `-1` find largest value < or <=, `1` find smaller value > or >=.

## offset
