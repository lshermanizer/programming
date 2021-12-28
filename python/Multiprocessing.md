
[source](https://www.youtube.com/watch?v=5TINkCci_W4&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=34)

```
import multiprocessing as mp

with mp.Pool(processes=4) as pool:
  pool.map(plot_datase, cat.datasets[-10:])
  pool.close() # close a worker once it's done
  pool.join() # error handling
```
