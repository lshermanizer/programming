# Pandas `agg`

[ref1](https://queirozf.com/entries/pandas-dataframe-groupby-examples)
[ref2](https://www.shanelynn.ie/summarising-aggregation-and-grouping-data-in-python-pandas/)
[ref3](https://medium.com/mastering-the-art-of-data-science-a-comprehensive/part-5-groupby-operations-and-multi-level-index-mastering-data-manipulation-with-pandas-4041d0ffe384)


### Dataframe summary statistics

```
df['income'].count()
df['income'].value_counts()
df['income'].unique()
df['income'].nunique()
df['income'].sum()
df['income'][df['category']=='Adult'].sum()
```

### Example of groupby and then agg
```
# groupby
dfgrp = df.groupby(['TR', 'Mode', 'EO'])
list_keys = list(dfgrp.groups.keys()
dfgrp.get_group(list_keys[0])
dfgrp.get_group(('TR1234', '1T', 5))

# agg
dfagg = df.groupby(['TR', 'Mode', 'EO']).agg({'%EL': 'idxmax', 'EO': 'first'})
dfagg['RPM'] = df.loc(dfagg['%EL'], 'RPM').values # get RPM that corresponds to the max %EL
dfagg['%EL'] = df.groupby(['TR', 'Mode', 'EO']).agg({'%EL': 'mean'}) # overwrite the %EL aggregration
dfagg

# access multi-index information (ref3)
dfagg.index # returns all multi-index combinations e.g. ('TR1234', '1T', 5), ('TR1234', '1F', 5), ('TR1034', '1T', 5), etc.
dfagg.index.levels # returns a list of unique values for each index level e.g. [['TR1234', TR1034'], ['1F', '1T'],[5, 7, 10]]
dfagg.index.names # returns a list of the index names e.g. ['TR', 'Mode', 'EO']

# access info in the aggregated dataframe
dfagg.loc[(('TR1234', '1T', 5)] # get one entry by using tuple
dfagg.xs(`  
dfagg.loc['TR1234']  # use the outermost index
dfagg.loc[['TR1234', 'TR3752']]  # use the outermost index, use multiple values at once

```


### Specify a `dict` to define `.agg()`
```
agg_def = {'age': 'mean', 'category': 'count'}    # get mean of `age`, get count of `category`
df.groupby('wealth').agg(agg_def)

In [155]: df.groupby('wealth').agg(agg_def)
Out[155]:
              age  category
wealth
high earner  30.5         2
low earner   21.0         3
```

### Used `pd.NamedAgg` or `tuple` to define `.agg()` with relabelling
```
df.groupby('wealth').agg(youngest=pd.NamedAgg(column='age', aggfunc=min))
df.groupby('wealth').agg(youngest=('age', min))                               # equivalent

Out[160]:
             youngest
wealth
high earner        28
low earner         13
```



### Use with `.groupby()` to get both mean and stddev of any group
```
grp = df.groupby('wealth').agg([np.mean, np.std])
grp

                   id                name             age           income               income2age
                 mean       std      mean       std  mean       std   mean          std        mean        std
wealth

high earner  3.500000  2.121320  2.500000  2.121320  30.5  3.535534   8500  2121.320344  276.515152  37.498087
low earner   5.666667  3.785939  4.666667  3.785939  21.0  9.848858   1403  2259.076581   45.464120  69.346556


grp.columns = [grp for col in grp.columns.values]    # flatten column names
grp

             (id, mean)  (id, std)  (name, mean)  ...  (income, std)  (income2age, mean)  (income2age, std)
wealth                                            ...

high earner    3.500000   2.121320      2.500000  ...    2121.320344          276.515152
 37.498087
low earner     5.666667   3.785939      4.666667  ...    2259.076581           45.464120
 69.346556
```
