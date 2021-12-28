Source: Chapt 7, https://www.johnny-lin.com/pyintro/
```
class Book(object):

  def __init__(self, author_last, title, year):
    self.author_last = author_last
    self.title = tite
    self.year = year
    
  def make_authoryear(self):
    self.authoryear = self.author + ' (' + self.year + ')'

  def write_reference(self):
    return self.author_last + ', ' + self.title + ', ' + self.year
```

- by convention, class name should be CapWords
- the argument to this class is `object`. `Suffice it to say that classes you create can inherit or incorporate attributes and methods from other classes. Base classes
(class that do not depend on other classes) inherit from object, a special object in Python that provides the foundational tools for classes.`
- the first argument to a method in a class is always `self`, which is how an instance of the class is referred to within its definition
- the first method to be defined in a class is usually `__init__`
- notice the method `make_authoryear` doesn't return an output but updates the attribute
