# Pandas' `.apply()` method

## `Lambda` function

### `Lambda` vs. regular functions
```
# a regular function (keyword is def)
def add3(x):
  return x+3
  
# a lambda function (keyword is lambda)
lambda x: x+3

adder = lambda a, b: a+b  # define a lambda function "adder"
adder(40, 2)              # call the function

# use a lambda function as an "immediately invoked function expression"
a = (lambda x: x+3)(2) # a=5
```

### Use a `lambda` function within a function ... a `function generator`
```
def custom_exponent(power):
  return lambda base : base ** power
  
square = custom_exponent(2) # returns a function 
a = square(2) # returns 4
```

### Some use cases
```
# Use with `filter`
list(filter(lambda x: x>18, df['age']))                   # return a list of ages above 18

# Use with `map`
df['income'] = list(map(lambda x: x*1.2), df['income']))  # update the `income` column ... this is very similar to what Pandas' `.apply()` method

# Use `functools.reduce` 
import functools
functools.reduce(lambda a,b: a+b,df['income'])            # return sum of all values in the `income` column (reduce the list to a value)
```

### Use lambda function together with `apply` in dataframes
```
# act on a Pandas dataframe:
df['age']  = df.apply(lambda x: x['age']+3, axis=1)     # use `axis=1` to apply function along the column `age`
df.iloc[0] = df.apply(lambda x: x.iloc[0]+3, axis=0)    # use `axis=0` to apply function along the 0-th row

# act on a Pandas series:
df['age'] = df['age'].apply(lambda x: x+3)

# create a new column `category` based on value in `age` with if/else statement
df['category'] = df['age'].apply(lambda x: 'Adult' if x>=18 else 'Child')

# create a new column `income2age` based on values from 2 columns
df['income2age'] = df.apply(lambda x: x['income']/x['age'], axis=1)
```

## Standard function
```
def fnc_age_descriptor(age):
  if age < 18:
    descr = 'juvenile'
  else:
    descr = 'adult'
return descr

def fnc_income_to_age(income, age):
  return income/age

# one argument
df['ageDescrip'] = df['age'].apply(fnc_age_descriptor)
df['ageDescrip'] = df.apply(lambda x: fnc_age_descriptor(x['age']), axis=1) # equivalent to above. "axis=1" is necessary.

# more than one argument
df['income2age'] = df.apply(lambda x: fnc_income_to_age(x['income'], x['age']), axis=1)

```

