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
