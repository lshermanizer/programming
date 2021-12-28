## create a datetime sequence by using `TimedeltaIndex` [1](https://www.youtube.com/watch?v=lGZCP_3uN2U&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=84)
```
df['time'] = pd.datetime(2019, 8, 17) + pd.TimedeltaIndex(df['time'], unit='m')
```
