# Pandas multi-index dataframe

[ref1](https://www.youtube.com/watch?v=yQ5IxnZouKo&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=87)


### Indexing ([ref](https://stackoverflow.com/questions/45967702/loc-and-iloc-with-multiindexd-dataframe))

```
df.set_index(['STID', 'TIME'], inplace=True) 
df.loc['BIXB']
df.loc[('BIXB', 0)]                # use a tuple to do slicing
df.loc[('BIXB', 0), 'TAIR']        # do indexing, then return 'TAIR' column

df.xs(0, level='TIME')             # use xs to get a time level (or so-called cross-section)

df.index                           # return a list of indices, each entry is a tuple

df.index.get_level_values(0)
df.index.get_level_values(0).unique()
df.loc[[df.index.get_level_values(0)[-1]]]

## use `try; except` to deal with cases where a combination of {modename, ieo} does not exist
with open('out.txt', 'w') as f:
for j, modename in enumerate(df.index.get_level_values(0).unique()):
    for i, ieo in enumerate(df.index.get_level_values(1).unique()):
        try:
            f.write('{:.2f},'.format(df.loc[(modename, ieo)]['%EL']))
        except TypeError:
            f.write(',')
        f.write('\n')
      
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

