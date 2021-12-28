# Pandas multi-index dataframe

[ref1](https://www.youtube.com/watch?v=yQ5IxnZouKo&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=87)


### Example: weather data time series at multiple stations

```
df.set_index(['STID', 'TIME'], inplace=True)     # pass a list of station ID and time
df.loc['BIXB']
df.loc[('BIXB', 0)]                              # use a tuple to do slicing
df.loc[('BIXB', 0), 'TAIR']                      # do indexing, then return 'TAIR' data

df.xs(0, level='TIME')                           # use xs to get a time level (or so-called cross-section)
```


## A multi-index indexing example [ref](https://stackoverflow.com/questions/45967702/loc-and-iloc-with-multiindexd-dataframe)
```
np.random.seed(123)
iterables = [['bar', 'baz', 'foo', 'qux'], ['one', 'two']]
idx = pd.MultiIndex.from_product(iterables, names=['first', 'second'])
df = pd.DataFrame(np.random.randn(8, 4), index=idx)
df.info(verbose=True)
print('')

    <class 'pandas.core.frame.DataFrame'>
    MultiIndex: 8 entries, ('bar', 'one') to ('qux', 'two')
    Data columns (total 4 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   0       8 non-null      float64
     1   1       8 non-null      float64
     2   2       8 non-null      float64
     3   3       8 non-null      float64
    dtypes: float64(4)
    memory usage: 669.0+ bytes

print(df)
print('')

                         0         1         2         3
    first second                                        
    bar   one    -1.085631  0.997345  0.282978 -1.506295
          two    -0.578600  1.651437 -2.426679 -0.428913
    baz   one     1.265936 -0.866740 -0.678886 -0.094709
          two     1.491390 -0.638902 -0.443982 -0.434351
    foo   one     2.205930  2.186786  1.004054  0.386186
          two     0.737369  1.490732 -0.935834  1.175829
    qux   one    -1.253881 -0.637752  0.907105 -1.428681
          two    -0.140069 -0.861755 -0.255619 -2.798589
    
print(df.index)
print('')

    MultiIndex([('bar', 'one'),
                ('bar', 'two'),
                ('baz', 'one'),
                ('baz', 'two'),
                ('foo', 'one'),
                ('foo', 'two'),
                ('qux', 'one'),
                ('qux', 'two')],
               names=['first', 'second'])

# .loc is primarily label-based ... .loc does take into account the level behavior ... df.loc['two'] would throw KeyError
print(df.loc['qux'])
print('')

                   0         1         2         3
    second                                        
    one    -1.253881 -0.637752  0.907105 -1.428681
    two    -0.140069 -0.861755 -0.255619 -2.798589

# .iloc is primarily integer position based ... .iloc is a strict positional indexer, it does not regard the structure at all
print(df.iloc[-1])
print('')

    0   -0.140069
    1   -0.861755
    2   -0.255619
    3   -2.798589
    Name: (qux, two), dtype: float64

# this is equivalenet to df.loc['qux']
print(  df.loc[[df.index.get_level_values(0)[-1]]]  )
print('')

                         0         1         2         3
    first second                                        
    qux   one    -1.253881 -0.637752  0.907105 -1.428681
          two    -0.140069 -0.861755 -0.255619 -2.798589
      
# this is to get those rows whose value of "second" is two"      
print(  df.swaplevel(0,-1).loc['two']  )

                  0         1         2         3
    first                                        
    bar   -0.578600  1.651437 -2.426679 -0.428913
    baz    1.491390 -0.638902 -0.443982 -0.434351
    foo    0.737369  1.490732 -0.935834  1.175829
    qux   -0.140069 -0.861755 -0.255619 -2.798589

```

### Average every `n` rows for a multi-index dataframe
The dataframe has 2 indices in which the 0-th level is `datetime` (6480 values) and the 1-st level is `height` (100 values). There are 648000 rows. The time interval is `20/s [s]`. I'd like to get 10-min averaged wind speed profiles (the `wspd` column). I didn't find a very elegant way to do it... below is what I did:

```
# Get 10-min averages
wrf_dt = 20/3.
rows = int(10*60 / wrf_dt) # every how many rows is a 10min interval
wrf_t10 = wrf_t[rows:-1:rows] # 10min interval
N_10min = len(wrf_t10)

wspd_profiles = np.zeros([len(wrf_z), N_10min])
for i in range(N_10min):
    if i != N_10min - 1:
        ilocs = (wrf.index.get_level_values(wrf.index.names[0]) >= wrf_t10[i]) & (wrf.index.get_level_values(wrf.index.names[0]) < wrf_t10[i+1])
    else:
        ilocs = (wrf.index.get_level_values(wrf.index.names[0]) >= wrf_t10[i]) & (wrf.index.get_level_values(wrf.index.names[0]) < wrf_t[-1])
    wrf10 = wrf[ilocs]
    df_tmp = wrf10.groupby(level=1).agg(['mean'])
    wspd_profiles[:,i] = df_tmp['wspd'].to_numpy().ravel()

# Confirm by plotting time series
wspd1 = wrf.loc[wrf.index.get_level_values('height') == 5.]['wspd'].to_numpy()
wspd2 = wspd_profiles[0,:]
plt.plot(wrf_t, wspd1)
plt.plot(wrf_t10, wspd2, '.')
```

