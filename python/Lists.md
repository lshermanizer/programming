### List comprehension [ref](https://www.youtube.com/watch?v=q_JWpPv-6mA&list=PLQut5OXpV-0ir4IdllSt1iEZKTwFBa7kO&index=27)
```
x = range(10)
y1 = [i**2 for i in x]                    # -> [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
y2 = [i**2 for i in x if i%2 == 0 ]       # -> with if, [0, 4, 16, 36, 64]
y3 = [y for y in y1 if y%2==0]            # -> with if, [0, 4, 16, 36, 64]
y4 = [i**2 if i%2==0 else 0 for i in x]   # -> with if/else, [0, 0, 4, 0, 16, 0, 36, 0, 64, 0]

data = [[1,2,3],[4,5,6],[7,8,9]]
flattened = [el for row in data for el in row]    # -> embedded for loops, [1, 2, 3, 4, 5, 6, 7, 8, 9]
# my intuition is to write: flattened = [el for el in row for row in data] (inner loop first, then outer loop)
# but in fact it is outer loop first, then inner loop
```
