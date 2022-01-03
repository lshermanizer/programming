
```
# define bins, and bin the whole dataset by the bin, and get the mean
wd_bins = np.arange(-180, 180, 10)
ds_binned = ds.groupby_bins('wind_direction', wd_bins).mean()
```