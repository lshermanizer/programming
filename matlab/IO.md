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

```

>>disp() #no control over the data format
>>fprintf() #full control over the data format

>>a=clock();
>>fprintf('%4.0f-%2.0f-%2.0f',a(1:3)); #Date format: yyyy-mm-dd
>>fprintf('%2.0f:%2.0f:%2.0f',a(4:6)); #Time format: hh:mm:ss

>>val=input('Data 1: ')  #Input a value
>>str=input('write : ', 's'); #Prompt user for string input: use the string notifier
  
>>ischar(a) #returns 1 if a is a character
>>iempty(a) #returns 1 if a is a empty
>>isinf(a) #returns 1 if a is infinity
>>isnan(a) #returns 1 if a is not a number (NaN)
>>isnumeric(a) #returns 1 if a is numeric
```