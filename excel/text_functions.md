# Text functions

## Formatting: `trim`, `upper`, `lower`, `proper`

`trim`: remove leading or trailing spaces 

`lower`, `upper`, `proper`: capitlization


## `concatenante` (`&`)
```
=A2&" "&A3
```
will concatenate A2 and A3 with a space in between.


## `left`, `mid`, `right`, `len`
`len` returns the total number of characters of a string.

`left`, `righ`, `mid` returns selected characters of a string based on position and length.


## `text`, `value`

`text` converts a value to text with a specified formatting. `value` converts a text to value.

## `substitute`
Syntax: `substitute(full_text, old_text, new_text, instance_number)` The last argument controls which instance it works on if there are multiple.

## `search`

`search` returns the position at which a specific character or string is first found.

```
=search('%',A11,10)
```
searches for '%' starting from the 10th position (i.e. ignores the first 9 characters, defined by the last argument) and returns its position in the string. If nothing is found it returns a `value error`.



`if(isnumber(search(find_text, within_text)), value_if_true, value_if_false)` combination can be used to classify data based on string data. The `isnumber()` part just avoids the `value error` outcome. Example:

```
=if(isnumber(search('gmail', A1)), 'gmail', if(isnumber(search('outlook', A1)), 'outlook', if(isnumber(search('hotmail', A1)), 'hotmail', 'other')))
```
