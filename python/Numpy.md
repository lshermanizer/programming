### make a list into a numpy array

```
a = [1, 2, 3]
b = np.array(a)
c = type(a) is np.ndarray # False
c = type(b) is np.ndarray # True

if not isinstance(a,(pd.core.series. Series, np.ndarray)):
   return np.array(a)
```

### atan2
```
theta = np.arctan2(x, y) # opposite to Excel atan2
```

### `np.c_`, `np.r_` operator
`np.c_` concetenate objects along the second axis. 
```
df_coor = pd.DataFrame(np.c_[nodeid, x, y, z], columns=['ID', 'X', 'Y', 'Z'])
df_coor['ID'] = df['ID'].astype('int64')
```

Oppositely, `np.r_` operator concetenate objects along the first axis. 
```
np.r_[np.array([1,2,3], np.array[4,5,6]) # will produce array([1,2,3,4,5,6])
```

### `np.savetxt`
Use `np.savetxt` to save arrays to a text file, no need to do for loops among lines
```
with open('output.txt', 'w', newline='') as f:
   df_coor = pd.DataFrame(np.c_[nodeid, x, y, z], columns=['ID', 'X', 'Y', 'Z'])
   df_coor['ID'] = df['ID'].astype('int64')
   np.savetxt(f, df_coor, fmt='%5d, %10.3e, %10.3e, %10.3e`)
```

### `np.where`
