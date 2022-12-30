Ref: https://realpython.com/python3-object-oriented-programming/



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
