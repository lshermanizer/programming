# `Lambda` function and Pandas' `.apply()` method

[ref1](https://www.analyticsvidhya.com/blog/2020/03/what-are-lambda-functions-in-python/), 
[ref2](https://www.datacamp.com/community/tutorials/pandas-apply)
[ref3](https://www.youtube.com/watch?v=3k2TEVqBh6M&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=59)

Use `lambda` function and `.apply()` method in Pandas without using for loops

------------

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

# call a function
def fnc_income_to_age(income, age):
  return income/age
df['income2age'] = df.apply(lambda x: fnc_income_to_age(x['income'], x['age']), axis=1)

```

