# Manipulate data in dataframe (that does not involve `.apply`)


### Create a column from another dataframe
```
# cannot do this on a dataframe level (need to use .copy() method), but legal on column level
df_new['BaseMode'] = df_base['Mode']
```

### Set data type with `.astype()`
```
df['Name'] = 'M' + df['ModeID'].astype(str)
```

### NaN
```
df['Source'] = df['Source'].fillna('SFV')  # replace any NaN entry with 'SFV'
```
