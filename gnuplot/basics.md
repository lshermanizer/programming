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

## separator
```
Set datafile separator ","
Plot "gnuplot_example_datafile.cvs" using 1:2 tile "x^3", \"gnuplot_example_datafile.cvs" title "x^5" using 1:3, \
"gnuplot_example_datafile.cvs" title "x^7" using 1:4
```

## Basic plotting commands
```
Set terminal png picsize 512 512	
Set output "convergence.png"	
Set size ratio 1	 #Graph's aspect ratio
Set size ratio -1 #Units' aspect ratio (equals to axis equal in MATLAB)
Set xrange [-1:2]	
Set yrange [-1:*] #-1 to data maximum
Set xtics 0.1 #The tick interval
Set ytics -1.0,0.1,1.0 #Set the tick interval and range
Set mxtics 5 #Set the number of minor ticks for each major tick
Set zeroaxis #Zero axes x=0 and y=0
Set xzeroaxis/yzeroaxis #Only x or y zero axis
Set key top left/bottom right # Location of the key (name of the file being plotted)
Unset key	 #Do not print the key
Plot "d.con" title "Convergence" #Replace the key with the specified title for a curve
Set title "Convergence History" #This is a standalone command, setting title for the graph
Set xlabel "x"	
Set border N	
Set xticks nomirror
```