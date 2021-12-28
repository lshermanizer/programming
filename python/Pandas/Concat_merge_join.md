### Concatenation ... simpler than `merge` or `join` ([ref](https://www.youtube.com/watch?v=rj2ZEAIbg1k&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=88))


Vetical stacking:
```
df_inst1_part1 = pd.read_csv('instrument1_obs1.csv')
df_inst1_part2 = pd.read_csv('instrument1_obs2.csv')   # they have the same variables (columns), but differ in time --> let's stack them vertically

df_inst1 = pd.concat([df_inst1_part1, df_inst1_part2]) # if more than 2, more efficient to concatenate multiple parts in one go than to concatenate two in multiple goes
                                                       # the index remains the same which causes duplicates
df_inst1.reset_index(inplace=True, drop=True)          # drop the old index, and replace with a new unique index
```


Horizontal stacking:
```
df_inst2 = pd.read_csv('instrument2.csv')              # it has the same number of rows and the same index as df_inst1, but different variables --> let's stack them horizontally
df_all   = pd.concat([df_inst1, df_inst2], axis='columns')
```


### Merge and join ([ref](https://www.youtube.com/watch?v=slUGaLyLJX0&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=89))

See a visual of the merge/join logic: https://github.com/jl477/tech_tools_and_tips/issues/1

Merge:

```
winds = pd.read_csv('wind_30min.csv')
temps = pd.read_csv('temp_hourly.csv')
pd.merge(temps, winds)                  # by default, it uses "inner join"
pd.merge(temps, winds, how='outer')     # --> index is out of order, empty data is filled with "NaN"
pd.merge(temps, winds, how='left') 
pd.merge(temps, winds, how='right')
```

Join is a special function that join based on indices. By default it is a left join.
```
winds.set_index('TIME', inplace=True)
temps.set_index('TIME', inplace=True)
winds.join(temps)                       # index is preserved
```
