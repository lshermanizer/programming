# Manipulate data in dataframe (that does not involve `.apply`)


### Create a column from another dataframe
```
df_new['BaseMode'] = df_base['Mode'] # cannot do this on a dataframe level (need to use .copy() method), but legal on column level
```

### NaN
```
df['Source'] = df['Source'].fillna('SFV')  # replace any NaN entry with 'SFV'
```
