
```
cfx5solve -def run.def -part-only 10 -parfile-write parfile.par     # write a partition file

cfx5interp -results prior_soln.res -mesh run.def > interp.log       # interpolate a prior solution onto a mesh

cfx5cmds -def run.res -text run.ccl -read                           # write a .ccl configuration file based on a .rest (or a .def file)

cfx5cmds -def run.def -text run.ccl -write                          # modify the .def based on a .ccl

```