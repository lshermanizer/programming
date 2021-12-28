### Get line count
`nLine = sum(1 for line in open(filename, 'r'))`

### open, read/write and close a file in one line:
```
with open(filename, 'r') as f:
   data = f.readlines()
   for l in range(nLine):
      if "[Faces]" in data[l]:
         lbeg = l

with open(filename, 'w') as f:
   for l in range(lbeg, nLine, 1):
       f.writelines(data[l])
       
# skip empty lines
with open(seqv_file, 'rU') as f:
   lines = [line for line in f.readlines() if line.strip()] # remove empty lines in the end
        
```

### Get relative path names
```
pattern = r"D:\Dir1\Dir1.2\Dir1.2.1\Dir1.2.1.5\DOE_1\*"
case_dirs = [path.basename(x) for x in glob(pattern)]
```
