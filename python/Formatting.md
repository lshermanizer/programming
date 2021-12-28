Reference: https://pyformat.info/


### Strings: padding, aligning, truncating

| What | How |
|:----|:---|
| Align left:   | `'{:<10}'.format('test')` |
| Align right:  | `'{:>10}'.format('test')` |
| Align center: | `'{:^10}'.format('test')` |
| Choose paddig character: | use `_` in this example: `'{:_<10}'.format('test')` |
| Truncating long strings: | `'{:.5}'.format('xylophone')` |
| Combining truncating and padding: | `'{:10.5}'.format('xylophone')`|

### Numbers:
| What | How |
|:----|:---|
| Padding: | `'{:4d}'.format(42)` --> pad with spaces (or equivalent to right align) |
| Padding: | `'{:04d}'.format(42)` --> pad with 0 |
| Combining truncating and padding: | `'{:06.2f}'.format(3.141592653589793)` --> 6 characteristcs in total, 2 significant digits, pad with 0 |
| Use `+` in front of positive numbers: | `'{:+d}'.format(42)`, the behavior to add `-` in front of negative numbers is unchanged|
| Use ` ` in front of positive numbers: | `'{: d}'.format(42)`, the behavior to add `-` in front of negative numbers is unchanged|
| Combing padding with signing: | `'{:=+5d}'.format(23)` --> use 5 characteristics in tota, the first is a positive sign, padded the rest with spaces |
