

## pivot data cache

When creating pivot tables, Excel creates a "cache" of the original data in the memory and works off of it to create pivot tables for better speed.

Do the following:

    Pivot Tables -> Analyze -> Options -> "Data" tab -> under "PivotTable Data", check "Save source data with file", check "enable show details", and uncheck "refresh data when opening the file". 

This way, even if the original data is accidentally deleted, we can continue to edit the pivot table by using the cache, and the original data can be restored by: first, clear all filters; then, double click on the "Grand Total" value.

## group

One can create groups within a pivot table, which will create a new outer layer: right click -> group/ungroup.

By default, for date/time values, Excel automatically creates groups of year, quarter, and month. To remove, right click -> ungroup. To change this behavior, Pivot Table -> Analyze -> Group Field -> make changes. 

## "Show Report Filter Pages..."

This will create multiple tabs for each value of a given filter.


## conditional formatting

Conditional formating can be applied to pivot tables just like normal data ranges.

## calculated fields

Pivot Table -> Analyze -> Fields, Items, & Sets -> Calculated Field... -> Define a name and a formula.
