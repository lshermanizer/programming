# Pandas `agg`

[ref1](https://queirozf.com/entries/pandas-dataframe-groupby-examples)
[ref2](https://www.shanelynn.ie/summarising-aggregation-and-grouping-data-in-python-pandas/)


### Dataframe summary statistics

```
df['income'].count()
df['income'].value_counts()
df['income'].unique()
df['income'].nunique()
df['income'].sum()
df['income'][df['category']=='Adult'].sum()

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
