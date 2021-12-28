### Basics ([ref](https://www.youtube.com/watch?v=_9j7Y1-lk-o&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=46&t=103s))
```
import xarray as xr

## open an xr dataset
ds = xr.open_dataset('example.nc')
# <xarray.DataSet>
# dimensions : isobaric, lat, long, time (their dimensions)
# coordinates: isobaric, lat, long, time (their values) + other coordinates not having a dimension specified, or dependent on multiple dimensions
# data variables: arrays
# attributes

## create an xr data array
ds = xr.DataArray(range(7), name='index', dims=['index']

## create an xr dataset
Niso, Nlat, Nlon = 5, 6, 7
data_temp = np.linspace(250, 300, Niso*Nlat*Nlon).reshape([Niso, Nlat, Nlon])
data_rh   = np.linspace(0,     1, Niso*Nlat*Nlon).reshape([Niso, Nlat, Nlon])
ds = xr.DataSet(

  {'temperature':  (['isobaric', 'lat', 'lon'], data_temp),
   'rel_humidity': (['isobaric', 'lat', 'lon'], data_rh)
  },
  
  coords = {
    'isobaric': xr.DataArray(np.linspace(1000, 500, Niso), name='isobaric', dims=['isobaric'], attrs={'units':'hPa'}),
    'lat':      xr.DataArray(np.linspace(30,   40 , Nlat), name='lat',      dims=['lat'],      attrs={'units':'degree_north'}),
    'lon':      xr.DataArray(np.linspace(255,  275, Nlon), name='lon',      dims=['lon'],      attrs={'units':'degree_east'})
  }
)   
   
## slice dataset
ds['isobaric'] # returns an xr data array

## add attributes
ds['temperature'].attrs['units'] = 'degree Kelvin' 

## write to a NetCDF file
ds.to_netcdf('saved_data.nc')
```

### Data slicing and indexing ([ref](https://www.youtube.com/watch?v=_9j7Y1-lk-o&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=46&t=103s))
```
ds = xr.open_dataset('example.nc')
heights = ds['variable1']                       # 4-D array, time x isobar x lat x lon

heights[0, -1]                                  # integer-based positional indexing
heights.loc['2018-01-01T06:00', 85000]          # label-based positional indexing
heights.isel[time=-1, isobar=10]                # integer-based dimension name indexing
heights.sel[time='2018-01-01T06:00', lat=30]    # label-based dimension name indexing
heights.sel[time='2018-01-01T06:00', lat=30, long=278, method='nearest']  # label-based dimension name indexing, with nearest neighbour search (find the [lat, lon] combination that is closest to specified)
ds.sel[time='2018-01-01T06:00', lat=30, long=278, method='nearest']       # do the above on the whole dataset

heights.sel[time=slice('2018-01-01T06:00', '2018-01-31T06:00'), lat=30]   # select a range 

heights.sel[{'lon': heights['lon']>270}]                                  # specify upper/lower bound
```

### Arithmetic ([ref](https://www.youtube.com/watch?v=_9j7Y1-lk-o&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=46&t=103s))
```
wspd = np.hypot(ds['u'], ds['v'])                                     # compute horizontal wind speed
ds['temperature'].mean(('time', 'lat', 'lon'))                        # compute mean of temperature across time, lat, and lon -> gives a vertical profile
ds['temperature'] - ds['temperature'].mean(('time', 'lat', 'lon'))    # a broadcast is done automatically by xarray

```
