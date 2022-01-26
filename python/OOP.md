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


--------------

https://realpython.com/python3-object-oriented-programming/


Example code:

```
class Dog:

    # Class attributes
    species = 'mammal'
    friendly = True

    # Initialize
    def __init__(self, name, age, vac):
        self.name = name
        self.age = age
        self.vac = vac

    # instance method 1
    def description(self):
        return "{} is {} years old".format(self.name, self.age)

    # instance method 2
    def vaccinate(self):
        self.vac = True

    # instance method 3
    def speak(self, sound):
        return "{} says {}".format(self.name, sound)

# Child class (inherits from Dog class)
class Bulldog(Dog):
    def run(self, speed):
        return "{} runs {}".format(self.name, speed)

# Child class (inherits from Dog class)
class Pitbull(Dog):
    friendly = False

#----------------------------------------------

# Instantiate the Dog object
philo = Dog("Philo", 5, False)
mikey = Dog("Mikey", 6, True)
jacky = Bulldog("Jacky", 3, True)
leo = Pitbull("Leo", 8, True)

# Access the instance attributes
print("{} is {} and {} is {}.".format(
    philo.name, philo.age, mikey.name, mikey.age))

# Is Philo a mammal?
if philo.species == "mammal":
    print("{0} is a {1}!".format(philo.name, philo.species))

# Has Philo been vaccinated? If not, vaccinate him.
print(philo.vac)
if philo.vac == False:
    philo.vaccinate()
    print(philo.vac)

# What about bulldog Jacky?
print(jacky.speak('Brrr'))
print(jacky.run('slowly'))
print('Is Jacky a dog?')
print(isinstance(jacky, Dog))
print('Is Jacky a bulldog?')
print(isinstance(jacky, Bulldog))
print('Is Jacky a pitbull?')
print(isinstance(jacky, Pitbull))

# Overrides an attribute in the parent class
print('Is Leo friendly?')
print(leo.friendly)

```

class:       

   * a user-defined data structure that contains arbitrary info about something.
   * A class just provides a *structure*. It doesn't have any real content itself.
   * A class is an idea for how something should be defined.
   * Use the __init__() method to initialize an object's initial attributes.
   * Note here "initialize" is not actually giving some values, rather just claiming these attributes exist.
   * You will never have to call the __init__() method. It gets called automatically when you create a new ‘Dog’ instance.


object:

   * An *instance* of some class with actual content/values.
   * the *self* variable is also an instance of the class.


attribute:

   * there are *instance attributes* and *class attributes*.
   * instance attributes are specific to each object.
   * class attributes are the same for all instances in this class.


(instance) method:


   * an instance method may need outside input (e.g. speak)
   * an instance method may be used to modify an attribute (e.g. vaccinate)


class inheritance

   * a *child class* inherits attributes and methods of the *parent class*.
   * a child class can override and/or extend the functionality of its parent class.
   * the built-in isinstance() function determines whether an instance belongs to a class
