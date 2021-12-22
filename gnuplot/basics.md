# GNUPLOT

#### Run gunplot directly from the command line:
Do `gnuplot 'scriptname.txt' -p`. The `-p` argument will keep the graphic open.

#### Example 1
```
  plot "dir1/file1.txt" using 1:4 lt rgb 'black' title 'Line 1 - AVG'
replot "dir1/file2.txt" using 1:5 lt rgb 'black' title 'Line 2 - STD'
set logscale y
rep
```
