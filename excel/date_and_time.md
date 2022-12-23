# Date and time functions

## `datevalue` and `timevalue`

In Excel, every time instance has an associated date value, using midnight on 1/1/1900 as the starting point.


## date formatting

On a cell, right click -> "Format Cells" -> use preset format or custom format.

When drag to fill multiple cells, Excel's "Auto Fill Options" have several options e.g. fill days, fill weekdays, months, years, etc. 

## `today()` and `now()`

These are `volatile` functions.

## `year`, `month`, `date`, `hour`, `minute`, `second`

Returns components of a datevalue/timevalue.

## `eomonth`, `yearfrac`

`=eomonth("8/3/2022",0)`: returns "8/31/2022".

`=eomonth("8/3/2022",0)+1`: returns "9/1/2022".

`=eomonth("8/3/2022",-1)`: returns "7/31/2022".

The `yearfrac` syntax:
```
=yearfrac(start_date, end_date, [basis])
```
where basis=0 (default), 1 (actual/actual; recommended), 2 (actual/360), 3 (actual/365),

## `weekday`, `workday`, `networkdays`

`weekday` returns a number either 1-7 or 0-6 depending on the "return type" argument value.

`workday` retuns a date based on a given number of days, and "holiday" argument value.

`networkdays` returns the number of days between 2 dates.

## `datedif`

`datedif` can be used to calculate the difference between 2 given dates in terms of days, months, years, etc. in different units. 