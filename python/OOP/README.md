
[ref1(Chap 7)](https://www.johnny-lin.com/pyintro/), [ref2](https://gale.udemy.com/course/python-oops-beginners), [ref3](https://www.tutorialsteacher.com/python/classmethod-decorator), [ref4](https://towardsdatascience.com/8-tips-for-object-oriented-programming-in-python-3e98b767ae79)


## Philosophy / best practices
- Procedural (data vs. functions) vs. object-oriented (states and behaviors; or attributes and methods) programming
  - Implicitly many things are Python are objects of a class, e.g. after defining `a='hello`', use `a.__class__` to return its class.
  - Use `dir()` command to list an object's attributes and methods.
- Abstracton and encapsulation: Hiding details from the user.
- Polymorphism
- Best practices:
  - Declare all attributes in one place by using the `__init()__` constructor
  - Use operator overloading `__str__` to define a string representation of an instance when used in `print()`
  - Use operator overloading `__repr__` to provides the exact string that can be used to recreate the object

## Class    

- A user-defined data structure that contains arbitrary info about something... an idea for how something should be defined. It provides a *structure* and dosen't necessarily have any real content itself.
- A class can have **attriubtes** and **methods**, referrd to as **class members**.
- Class inheritance
  - A **child class** inherits attributes and methods of the **parent class**. Synatx: `class Bulldog(Dog)`.
  - A child class may have **multiple inheritance**. Syntax: `class Bulldog(Dog, EuropeanAnimal)`.
  - A chird class may also have **multi-level inheritnce**, e.g. `class Animal()`, `class Dog(Animal)`, `class Bulldog(Dog)`.
- Override parent class methods:
  - If the same method is defined again, it will override the parent's method.
  - If one desires to call the parent's method, the `super()` function removes the override: `super().vaccinate()`
- Access to class members:
  - **Public**: Accessible even from outside the class (default behavior). 
  - **Protected**: Accessible from class and child classes. Syntax is to use `_` prefix.
  - **Private**: Not accessible outside of the class. Syntax is to use `__` prefix.


```
class Car:
    def __init__():
        make = 'Honda'   # public
        _model = 'Civic' # protected
        __price = 1998   # private

car1 = Car()
print(car1.__price) # --> this will cause an error
print(car1._Car__price) # --> this would work, because Python internally renames the attribute this way when it is declared as private. This is called "name mangling".
```


## Objects (or instances)

- An **instance** of some class with actual content/values.
- `self` instance: `self` is also an instance of the class.
- The built-in `isinstance()` function determines whether an instance belongs to a class


## Attributes

- Class attributes (shared by all instances of the class) vs. instance attributes
```
class Student:
    name = 'unknown'    # class attribute

    def __init__(self):
        self.age = 20   # instance attribute
```


## Methods

- Method has access to all the attributes of a class.
- Class vs. instane methods:
    - an instance method may need outside input (e.g. speak)
    - an instance method may be used to modify an attribute (e.g. vaccinate)
- Abstract base class ("ABC"): A high-level class that only serves to enforce child classes must have something in common. Use `metaclass = ABCMeta` to declare an ABC. Uses `@abstractmethod` (this is called a **built-in decorator**) to declare an abstract method in an ABC. In the example below, if `area` method is not defined for `Square` or `Rectangle` an error will appear.

```
from abc import ABCMeta, abstractmethod
class Shape(metaclass = ABCMeta):
    @abstractmethod
    def area():
        return 0
    
class Square(Shape):
    def __init__(self, length):
        self.length = length

    def area(self):
        return self.length * 4

class Rectangle(Shape):
    def __init__(self, length, width):
        self.length = length
        self.width = width

    def area(self):
        return (self.length + self.width) * 2
```

- Static methods:
  - use `@staticmethod` decorator to declare. It knows nothing nothing about the class or instance it was called on (they were not passed to it).
- Class methods:
  - use `@classmethod` decorator to declare. It gets passed the class it was called on (`cls` rather than `self`). It does not need an instance to exist. One example is to *create* an instance from external sources.
- The `__init__` method:
    - used to initialize an object's initial attributes. Note here *initialize* is not actually giving some values, rather just claiming these attributes exist.
    - You will never have to call the `__init__()` method. It gets called automatically when you create a new instance.
- Operator overloading: e.g. define whatt `==` means for two instances. Another common usage is use `__str__` to define what `print()` does on an instance.
  
```
class Dog:
    def __init__(self, name):
        self.name = name

    def __eq__(self, dog2):
        return True if self.name == other.name else False

dog1 = Dog('Sherman')
dog2 = Dog('Duoduo')
print(dog1 == dog2) # --> will print False
```
- `@property` decorator and `setter`:
  - To make the `balance` attribute read-only, add a method called `balance` with `@property` decorator and returning the attribute’s value.
  - To make the `balance` attribute updatable, but within a certain limit, add a method called `balance` with `balance.setter` decorator to set new values with validations.

```
class BankAccount:

    __MIN_BALANCE = -10000
    
    def __init__(self, owner, account_number, balance=0):
        self._owner = owner    
        self._account_number = account_number
        self._created_at = datetime.now().date()
        if balance < self.__MIN_BALANCE:
            raise ValueError("Balance too small!")
        else:
            self._balance = balance
    
    @property
    def balance(self):
        return self._balance

    @balance.setter
    def balance(self, new_balance):
        if new_balance < self.__MIN_BALANCE:
            raise ValueError("Balance to small!")
        else:
            self._balance = new_balance
```


