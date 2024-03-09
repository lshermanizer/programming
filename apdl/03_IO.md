
## read a CDB
```
cdread, db, cdb_name, cdb
```


### Read a solution
```
/post1
file,modal_solution,rst
set,first
```

### warning message print control
```
/nerr, 100, 100, off ! by default only the first 5 messages will be print. this relaxes that 
``` 


## set and get job name
```
/filname,my_file_name       ! change jobname for the analysis (default is file)
*get,jname,active,,jobnam   ! get current jobname
```


## Use a macro, but check if it exists first
```
my_file='my_file.mac'
/inquire,if_file,exist,my_file
*if,if_file,EQ,1,THEN
        /input,my_file
*endif
```
