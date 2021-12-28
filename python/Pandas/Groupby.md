# Pandas' `.groupby()` method

[ref1](https://www.geeksforgeeks.org/python-pandas-dataframe-groupby/)
[ref2](https://queirozf.com/entries/pandas-dataframe-groupby-examples)

`.groupby()` splits the data into groups based on some criteria

The  example dataframe `df` is also used in `Pandas_apply.md`. It has columns:  `id name  age  income category  income2age`

----------------


### `.groupby()` basic
```

df.groupby('category')                       # returns a `DataFrameGroupBy` object

df.groupby('category').describe()            # gives a summary view

df.groupby('category')['age'].hist()         # gives histogram of age for each group

df.groupby('category').groups                # returns a dictionary, keys=groups, values=axis labels in each group
In [127]: df.groupby('category').groups
Out[127]: {'Adult': [0, 1, 2, 4], 'Child': [3]}


df.groupby('category').groups.keys()         # returns group keys
In [128]: df.groupby('category').groups.keys()
Out[128]: dict_keys(['Adult', 'Child'])

df.groupby('category').get_group('Adult')    # returns a `DataFrame` object which is the `Adult` group

df.groupby('category').first()               # returns a `DataFrame` object which collects the first entry in each group

df.groupby(['category', 'wealth`])           # group by two variables; each `DataFrame` object will have multi-index
```

### `.groupby()` arguments: `as_index` and `group_keys`
```
df.groupby('wealth', as_index=False)['age'].mean()   # return a DataFrame with `wealth` as index
df.groupby('wealth')['age'].mean()                   # no index

df.groupby('wealth')['income'].apply(lambda x: x+300)
df.groupby('wealth', group_keys=False)['income'].apply(lambda x: x+300)  # `group_keys` useful only when .apply() is used
```


### Use `.size()`,  `nunique()`, `.mean()`, `.sum()`
```
df.groupby('wealth')['age'].nunique()  # returns a Pandas Series, list number of unique ages for all groups

df.groupby('wealth').size()            # get a count of memebrs in each group

df.groupby('wealth')['income'].mean()  # get mean

df.groupby('wealth')['income'].sum()   # get sum

df.groupby('wealth')['income'].sum()   # get sum
df[df['category']=='Child'].groupby('wealth')['income'].sum()   # get sum, but for `Child` only

df.groupby('wealth')['income'].sum().plot(kind='bar')           # make bar chart
```


### Use with `.apply()` to do operations
```
df['wealth'] = df['income'].apply(lambda x: 'high earner' if x>5000 else 'low earner')
grp2 = df.groupby(['category', 'wealth'])    # group by two criteria simultaneously
grp2.get_group(('Adult', 'high earner'))     # use tuple to return


df.groupby('wealth')['age']          # returns a `SeriesGroupBy` object, contains the `age` column information only

In [59]: df.groupby('wealth')['category'].apply(lambda x: ','.join(x))  # concatenate strings for all members in a group
Out[59]:
wealth
high earner          Adult,Adult
low earner     Adult,Adult,Child
Name: category, dtype: object


In [60]: df.groupby('wealth')['age'].apply(lambda x: sum(x))            # compute summation for all members in a group
Out[60]:
wealth
high earner    61
low earner     63
Name: age, dtype: int64
```


### Use `.to_frame()`, `.reset_index()`
```
df.groupby('wealth')['age'].nunique().to_frame()                  # returns a Pandas DataFrame but doesn't have index
df.groupby('wealth')['age'].nunique().to_frame().reset_index()    # returns a Pandas DataFrame, with new index
df.groupby('wealth')['age'].sum().to_frame().reset_index()        # get sum of all ages
df.groupby('wealth')['age'].sum().to_frame().reset_index().sort_values(by='age')   # use `.sort_values()` as any ordinary dataframe
```

