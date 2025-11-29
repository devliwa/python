# Object-Oriented Programming (OOP) in Python

Object-Oriented Programming (OOP) is a programming paradigm that **organizes code into objects**, which represent real-world entities. Python supports OOP, allowing you to create **classes** and **objects**.

---

## 1. Key Concepts in OOP

1. **Class** – Blueprint for creating objects  
2. **Object** – Instance of a class  
3. **Attributes** – Variables that belong to an object  
4. **Methods** – Functions that belong to an object  
5. **Encapsulation** – Keeping data safe inside objects  
6. **Inheritance** – One class can inherit attributes and methods from another  
7. **Polymorphism** – Using a single interface for different types of objects  

---

## 2. Creating a Class

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print(f"{self.name} says woof!")
```

- `__init__` is the **constructor** that runs when an object is created  
- `self` refers to the **instance of the object**

---

## 3. Creating Objects

```python
my_dog = Dog("Buddy", 3)
print(my_dog.name)  # Output: Buddy
print(my_dog.age)   # Output: 3

my_dog.bark()       # Output: Buddy says woof!
```

---

## 4. Instance vs Class Attributes

### Instance Attribute
- Unique to each object
```python
dog1 = Dog("Max", 2)
dog2 = Dog("Bella", 4)
print(dog1.name)  # Max
print(dog2.name)  # Bella
```

### Class Attribute
- Shared among all instances
```python
class Dog:
    species = "Canis familiaris"  # Class attribute
    def __init__(self, name):
        self.name = name

dog1 = Dog("Max")
dog2 = Dog("Bella")
print(dog1.species)  # Canis familiaris
print(dog2.species)  # Canis familiaris
```

---

## 5. Methods with Parameters

```python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

circle1 = Circle(5)
print(circle1.area())  # Output: 78.5
```

---

## 6. Inheritance

```python
class Animal:
    def speak(self):
        print("Some sound")

class Cat(Animal):
    def speak(self):
        print("Meow")

my_cat = Cat()
my_cat.speak()  # Output: Meow
```

- `Cat` **inherits** from `Animal`  
- Can **override methods** for custom behavior  

---

## 7. Encapsulation

- Use `_` or `__` to **protect variables**  
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

account = BankAccount(100)
account.deposit(50)
print(account.get_balance())  # Output: 150
```

---

## 8. Polymorphism Example

```python
class Dog:
    def speak(self):
        print("Woof")

class Cat:
    def speak(self):
        print("Meow")

animals = [Dog(), Cat()]
for animal in animals:
    animal.speak()
```

Output:  
```
Woof
Meow
```

- Same method name, different implementation  

---

## 9. Summary

- **OOP** helps organize code into **real-world objects**  
- Core concepts:
  - Classes & Objects  
  - Attributes & Methods  
  - Encapsulation  
  - Inheritance  
  - Polymorphism  
- Makes code **modular, reusable, and easier to maintain**  

---

Optional Enhancements:
- Create a **small OOP project**, e.g., a **bank system**, **inventory system**, or **simple game**  
- Practice combining **inheritance** and **polymorphism** in real projects  

OOP is a **foundational concept** for building larger, more structured Python programs.

# object-oriented-programming(OOP)

- [Turtle graphics](https://docs.python.org/3/library/turtle.html)
- [Turtle Colors](https://cs111.wellesley.edu/reference/colors)
- [X & Y Pokédex](https://pokemondb.net/pokedex/game/x-y)
- [The Python Package Index (PyPI)](https://pypi.org/)
- [Pretty Table](https://pypi.org/project/prettytable/)
- [prettytable - Tutorial.wiki](https://code.google.com/archive/p/prettytable/wikis/Tutorial.wiki)
- [Steve Jobs on Object Oriented Programming (OOP)](https://www.rollingstone.com/culture/culture-news/steve-jobs-in-1994-the-rolling-stone-interview-231132/)

coffee_maker.py
```python
class CoffeeMaker:
    """Models the machine that makes the coffee"""
    def __init__(self):
        self.resources = {
            "water": 300,
            "milk": 200,
            "coffee": 100,
        }

    def report(self):
        """Prints a report of all resources."""
        print(f"Water: {self.resources['water']}ml")
        print(f"Milk: {self.resources['milk']}ml")
        print(f"Coffee: {self.resources['coffee']}g")

    def is_resource_sufficient(self, drink):
        """Returns True when order can be made, False if ingredients are insufficient."""
        can_make = True
        for item in drink.ingredients:
            if drink.ingredients[item] > self.resources[item]:
                print(f"Sorry there is not enough {item}.")
                can_make = False
        return can_make

    def make_coffee(self, order):
        """Deducts the required ingredients from the resources."""
        for item in order.ingredients:
            self.resources[item] -= order.ingredients[item]
        print(f"Here is your {order.name} ☕️. Enjoy!")

```
menu.py
```python
class MenuItem:
    """Models each Menu Item."""
    def __init__(self, name, water, milk, coffee, cost):
        self.name = name
        self.cost = cost
        self.ingredients = {
            "water": water,
            "milk": milk,
            "coffee": coffee
        }


class Menu:
    """Models the Menu with drinks."""
    def __init__(self):
        self.menu = [
            MenuItem(name="latte", water=200, milk=150, coffee=24, cost=2.5),
            MenuItem(name="espresso", water=50, milk=0, coffee=18, cost=1.5),
            MenuItem(name="cappuccino", water=250, milk=50, coffee=24, cost=3),
        ]

    def get_items(self):
        """Returns all the names of the available menu items"""
        options = ""
        for item in self.menu:
            options += f"{item.name}/"
        return options

    def find_drink(self, order_name):
        """Searches the menu for a particular drink by name. Returns that item if it exists, otherwise returns None"""
        for item in self.menu:
            if item.name == order_name:
                return item
        print("Sorry that item is not available.")
```
money_machine.py
```python
class MoneyMachine:

    CURRENCY = "$"

    COIN_VALUES = {
        "quarters": 0.25,
        "dimes": 0.10,
        "nickles": 0.05,
        "pennies": 0.01
    }

    def __init__(self):
        self.profit = 0
        self.money_received = 0

    def report(self):
        """Prints the current profit"""
        print(f"Money: {self.CURRENCY}{self.profit}")

    def process_coins(self):
        """Returns the total calculated from coins inserted."""
        print("Please insert coins.")
        for coin in self.COIN_VALUES:
            self.money_received += int(input(f"How many {coin}?: ")) * self.COIN_VALUES[coin]
        return self.money_received

    def make_payment(self, cost):
        """Returns True when payment is accepted, or False if insufficient."""
        self.process_coins()
        if self.money_received >= cost:
            change = round(self.money_received - cost, 2)
            print(f"Here is {self.CURRENCY}{change} in change.")
            self.profit += cost
            self.money_received = 0
            return True
        else:
            print("Sorry that's not enough money. Money refunded.")
            self.money_received = 0
            return False
```
main.py
```python
from menu import Menu
from coffee_maker import CoffeeMaker
from money_machine import MoneyMachine

money_machine = MoneyMachine()
coffee_maker = CoffeeMaker()
menu = Menu()

is_on = True

while is_on:
    options = menu.get_items()
    choice = input(f"What would you like? ({options}): ")
    if choice == "off":
        is_on = False
    elif choice == "report":
        coffee_maker.report()
        money_machine.report()
    else:
        drink = menu.find_drink(choice)
        
        if coffee_maker.is_resource_sufficient(drink) and money_machine.make_payment(drink.cost):
          coffee_maker.make_coffee(drink)
```
  
### [coffee-machine-project](https://github.com/devliwa/coffee-machine)

