# GNUPLOT

### Execute a script:
Do `gnuplot 'scriptname.txt' -p`. The `-p` argument will keep the graphic open.


### Color names
See [the picture](colornames.png) [ref](https://ayapin-film.sakura.ne.jp/Gnuplot/Primer/Misc/colornames.png)

### Example 1
```
  plot "dir1/file1.txt" using 1:4 lt rgb 'black' title 'Line 1 - AVG'
replot "dir1/file2.txt" using 1:5 lt rgb 'black' title 'Line 2 - STD'
set logscale y
rep
```

### Example 2
```
plot "file.txt" using ($1):($10)  lt  rgb 'black'  title 'analysis'

## If only selected rows
plot "<(sed -n '1,460p' file.txt)"  using ($1):($10) lt rgb 'black'

## Set range, label
set xzeroaxis lt -1
set xlabel "Iteration number"
set ylabel "Variable"
set yrange [-0.001:0.001]
```

