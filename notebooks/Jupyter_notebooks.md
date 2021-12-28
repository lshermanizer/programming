
### - set up environment
```
%load_ext autoreload
%autoreload 2

%matplotlib inline
%matplotlib widget
```

### - set up default plotting style
```
import matplotlib.pylab as pylab
params = {'legend.fontsize': 'x-large', \
          'figure.figsize': (8, 8), \
          'axes.labelsize': 'x-large', \
          'axes.titlesize':'x-large', \
          'xtick.labelsize':'x-large', \
          'ytick.labelsize':'x-large', \
          'axes.labelsize': 'x-large'}
pylab.rcParams.update(params)
```

## time an execution
