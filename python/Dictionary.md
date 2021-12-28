# Combining dictionaries [1](https://www.youtube.com/watch?v=0lwXJFTqLLw&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=183)
```
a = {'UCLA': 'Los Angeles',  'UCSF': 'San Francisco'}
b = {'UCSB': 'Santa Babara', 'UCSF': 'Santa Fe'}

a.update(b) # uses b to update a, returns a changed b
c = {**a, **b} # create a new dictionary
c = a | b # new syntax in Python 3.9
```
