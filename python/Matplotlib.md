### Matplotlib transform ([ref](https://www.youtube.com/watch?v=CxsShxafkM8&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=28))

```
x = range(10)
y = [i**2 for in x]
fig = plt.figure(figsize=(10,10))
ax = plt.subplot(1, 1, 1)
ax.plot(x, y, linstyle='None', marker='o')
ax.text(4+0.1, 4**2, 'Interesting data point', fontsize=16', va='center')                # known coordinate, va=vertical alignment
ax.text(4+0.1, 80, 'Top Center Label - My plot', fontsize=16', va='center', ha=center')  # ha=horizontal alignment

# if ax.set_xlim([-1 5]) --> the label will no longer be in the center
# this is because we were using x,y coordinates
# it really should be relative to axes coordinates
# the following will make it robust, i.e. always in top center regardless of xlim or ylim

ax.text(0.5, 0.95, 'Top Center Label - My plot', fontsize=16', ...
        va='center', ha=center', transform=ax.transAxes) # 0.5, 0.95 are normalized to axes coordinates -> then transform to x,y coordinates
```

`fig.transFigure` will be relative to figure coordinate (instead of ax coordinate for a subplot)

### Matplotlib subplots ([ref](https://www.youtube.com/watch?v=JzqATjzogFs&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=29))
```
fig = plt.figure(figsize=(10,8))
ax1 = fig.subplot(3, 1, 1)
ax2 = fig.subplot(3, 1, 2)
ax3 = fig.subplot(3, 1, 3)
```

### twin axes ([ref](https://www.youtube.com/watch?v=lrREMkpHfao&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=30))
```
fig = plt.figure(figsize=(10,8))
ax1 = fig.subplot(1, 1, 1)
ax2 = ax.twin()
ax1.plot(x, y1)
ax2.plot(x, y2, color='tab:orange') # by default the color is also blue

ax1.set_ylabel('Variable 1')
ax1.yaxis.label.set_color('tab:blue')
ax1.tick_params(axis='y', colors='tab:blue')
ax2.spines['left'].set_color('tab:blue') # ax2 is on the layer on top of ax1

ax2.set_ylabel('Variable 2')
ax2.yaxis.label.set_color('tab:orange')
ax2.tick_params(axis='y', colors='tab:orange')
ax2.spines['right'].set_color('tab:orange')
```

### save multiple figures as pages in a single PDF
```
import matplotlib.pyplot as plt
from matplotlib.backends.backend_pdf import PdfPages

with PdfPages('compare_results.pdf', 'w') as pdf:
	for i, (x, y) in enumerate(zip(x_series, y_series)):
		fig = plt.figure(figsize=(6,6))
		plt.plot(x, y)
		pdf.savefig(fig)

```

### plot 45-degree line
```
x = np.linspace(*ax.get_xlim())
ax.plot(x, x, '-k')
```

## Horizontal / vertical lines
```
plt.axvline(x=0.22058956) #vertical line
horizontal lines (axhline) and rectangles (axvspan).
```

### use a colormap
```
import matplotlib.pylab as pylab

# generate N colors based on the colormap "jet" within range 0-1 
colors = pylab.cm.jet(np.linspace(0,1,N))

# get default color cycle
cmap = plt.get_cmap("tab10")
for i in range(10):
   ax.plot(x, y, color=cmap(i), linestyle = '-')
```

### add colorbar to a subplot
```
fig, axes = plt.subplots(nrows=1, ncols=2)
obj = axes[0].scatter(x, y, c=z)
fig.colorbar(obj, ax=axes[0], orientation='vertical') # the "ax" argument puts the colorbar next to the specific subplot
```
