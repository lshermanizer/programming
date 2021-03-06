

### Quickly inspect a dataframe
```
print(df.info(verbose = True))
df.columns # get columns
df.index   # get index
col_names = list(df.columns.levels[0]) # get level-1 column names for a multi-index dataframe
df.head()
```

### Data selection [ref](https://www.shanelynn.ie/pandas-iloc-loc-select-rows-and-columns-dataframe/)
```
df.iloc[0]     # 0th row
df.iloc[:,0]   # 0th col
df.iloc[0:3,0] # rows 0 through 3, 0th col

df.loc['CASE_0_0'] 
df.loc[['CASE_0_0', 'CASE_0_10'], ['Success', 'Weight', 'CoG', 'Round']]
df.loc[df['Success'] == True, ['Weight', 'CoG']] # use boolean to select data
df.loc[df['Round'].str.endswith("5")]
df.loc[df['company_name'].apply(lambda x: len(x.split(' ')) == 4)]  # Use lambda function to select rows where the company name has 4 words in it.

```

Note that `.iloc` returns a Pandas Series when one row is selected, and a Pandas DataFrame when multiple rows are selected, or if any column in full is selected. To counter this, pass a single-valued list if you require DataFrame output.


### Randomly select, and get what's left
```
df_train = df_data.groupby('seed').sample(frac=5/6, random_state=1)
df_test = df_data[~df_data.index.isin(df_train.index)]
```


### Drop column data [ref](https://www.youtube.com/watch?v=ncpYohRYG3I)
```
df.drop(['Humidity', 'Pressure', 'Salinity'], axis='columns', inplace=True) 
```

### Rename column names [ref](https://www.youtube.com/watch?v=ncpYohRYG3I)
```
df.columns --> get a list of names, for example 'TIME', 'TAIR', 'WSPD'
name_mapping = {'TIME': 'Time',
                'TAIR': 'Air temperature',
                'WSPD': 'Wind speed',
                'WDIR': 'Wind direction' # having an extra key that's not in the column names is okay
               }
df.rename(columns=name_mapping, inplace=True) # update names
df.columns = [col.upper() for col in df.columns] # use list comprehension to update the column names to be all uppercase

```


### Index
```
del = pd.DataFrame(del) # list to dataframe
del.columns = ['channel', 'downstream_spacing', 'freestream', 'wake'] # give names
del = lifetime_DEL.set_index(['downstream_spacing', 'channel']) # set indices

del.loc[(3.33, slice(None)), :] # get a slice of the dataframe for spacing=3.33
del.loc[(slice(None), 'tower_top_Mx'), 'wake']  # get a slice of the dataframe for channel=tower_top_Mx and for the column "wake"

del.loc[(slice(None), 'tower_top_Mx'), :].index.values[0:3] # return multi-index
array([(3.33, 'tower_top_Mx'),
       (5.0, 'tower_top_Mx'),
       (6.0, 'tower_top_Mx')], dtype=object)

del.loc[(slice(None), 'tower_top_Mx'), 'wake'].index.get_level_values(0)[0:3] # return 0th-level index only
Float64Index([3.33, 5.0, 6.0], dtype='float64', name='downstream_spacing')

```


```

df.set_index("Weight", inplace=True)     # set index of rows to be based on the "Weight" col


# rename column
wrf = wrf.rename(columns={'Time':'datetime'})


# interpolate
wrf['k'] = wrf['k'].unstack().interpolate(method='linear').stack()

# The first index name is not set. Give it a name
wrf.index.set_names('datetime', level=0, inplace=True)

# len(wrf_t) = len(wrf)
wrf_t = wrf.index.get_level_values(wrf.index.names[0]).to_numpy()

# len(wrf_t) = Ntimes
Ntimes = len(wrf.index.levels[0])
wrf_t = wrf.index.unique(level=wrf.index.names[0])

# remove the height index
wrf.reset_index(level ='height')

```
