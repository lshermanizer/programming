## Plot a line from slope and intercept
```
def abline(ax, slope, intercept):
    """ Plot a line from slope and intercept
        Ref: https://stackoverflow.com/a/43811762
    """ 
    x_vals = np.array(ax.get_xlim())
    y_vals = intercept + slope * x_vals
    return x_vals, y_vals
```
