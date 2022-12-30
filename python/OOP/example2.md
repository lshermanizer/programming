
ref: Chapt 7, https://www.johnny-lin.com/pyintro/


```
class Book:
  def __init__(self, author_last, author_first, year, title):
    self.author_last = author_last
    self.author_first = author_first
    self.year = year
    self.title = tite

  def make_authoryear(self):
    self.authoryear = self.author_last + ' (' + self.year + ')'

  def write_reference(self):
    return self.author_last + ', ' + self.title + ', ' + self.year

class Article:
  def __init__(self, author_last, author_first, year, journal_title):
    self.author_last = author_last
    self.author_first = author_first
    self.year = year
    self.journal_title = journal_title

  def make_authoryear(self):
    self.authoryear = self.author_last + ' (' + self.year + ')'

  def write_reference(self):
    return self.author_last + ', ' + self.journal_title + ', ' + self.year

import operator

class Bibliography:
  def __init__(self, entireslist):
    self.entireslist = entireslist

  def sort_entries_alpha(self):
    tmp = sorted(self.entireslist, key=operator.attrgetter('author_last', 'author_first'))
    self.entireslist = tmp
    del tmp

  def write_bibliorg_alpha(self):
    self.sort_entries_alpha()
    output = ''
    for ientry in self.entireslist:
      output = output + ientry.write_reference() + '\n\n'
    return output[:-2]
```

- By convention, class name should be CapWords
- The first argument to a method in a class is always `self`, which is how an instance of the class is referred to within its definition
- The first method to be defined in a class is usually `__init__`
- Notice the method `make_authoryear` doesn't return an output but updates the attribute

