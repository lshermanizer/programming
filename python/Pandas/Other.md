### `.replace()` ([ref](https://www.youtube.com/watch?v=31k53iHE-yw&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=90))

The example below uses "keys" (integer coding) to repesent categories.
We can use dictionaries and the `replace` function to change this.

```
# platforms: 0=mobile, 1=public report, 2=field station
# types    : 0=regular, 1=special
df = pd.DataFrame({'Obs platform': [0, 1, 2],
                   'Temperature' : [24, 25, 27],
                   'Obs type'    : [0, 1, 1]})

platform_mapping = {0: 'mobile', 1: 'public report', 2: 'field station'}
type_mapping     = {0: 'regular', 1: 'special'}

df['Obs platform'].replace(platform_mapping, inplace=True) # replace "keys" with "values". If there's no matching key, it will be left unchanged
df['Obs type'].replace(type_mapping, inplace=True)
```

### `to_dict()` ([ref](https://stackoverflow.com/a/18695700)
```
    id    value
0    0     10.2
1    1      5.7
2    2      7.4

df.set_index('id').to_dict()
# And if you have only one column, to avoid the column name is also a level in the dict
df.set_index('id')['value'].to_dict()
```
