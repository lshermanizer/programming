### number of elements in an array that match a certain condition:
```
  locations = np.arrray([-4, -1, 1, 4, 6, 8, 10, 12]) #location indices
  nloc = sum(i < 0 for i in locations)  #number of stations with negative indices
  nloc = sum(i >= 4 and i < 8 for i in locations)
```
