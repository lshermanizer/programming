### Output speed-up

Reference for speed-up: https://www.mathworks.com/matlabcentral/answers/419329-speeding-up-writing-a-very-large-text-file

```
  % header rows
row1 = var_names(ids);
    % header row format
format = '%s';
format = [format repmat(', %s', 1, Nvar-1)];
format = [format '\n'];
fprintf(fid, format, row1{:});
```
