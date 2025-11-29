# Instances, State, and Higher-Order Functions in Python

This lesson covers:
- Understanding **instances** and **state** in OOP  
- Learning about **higher-order functions** in Python  

---

## 1. Instances and State

### 1.1 What is an Instance?

- An **instance** is a **specific object** created from a class  
- Each instance can have **its own unique attributes**  

```python
class Car:
    def __init__(self, make, color):
        self.make = make
        self.color = color

car1 = Car("Toyota", "Red")
car2 = Car("Honda", "Blue")

print(car1.make, car1.color)  # Toyota Red
print(car2.make, car2.color)  # Honda Blue
```

---

### 1.2 What is State?

- **State** refers to the **current values of an object’s attributes**  
- Each instance can have **different state**  

```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount

account1 = BankAccount(100)
account2 = BankAccount(200)

account1.deposit(50)
print(account1.balance)  # 150
print(account2.balance)  # 200
```

- `account1` and `account2` maintain **independent states**  

---

### 1.3 Modifying State with Methods

```python
class Light:
    def __init__(self):
        self.is_on = False

    def toggle(self):
        self.is_on = not self.is_on

light = Light()
print(light.is_on)  # False
light.toggle()
print(light.is_on)  # True
```

- Methods can **change the state** of an instance  

---

## 2. Higher-Order Functions

### 2.1 Definition

- A **higher-order function** is a function that can:
  1. **Take other functions as arguments**  
  2. **Return a function**  

---

### 2.2 Examples

#### Passing Function as Argument

```python
def square(x):
    return x * x

def apply_function(func, value):
    return func(value)

result = apply_function(square, 5)
print(result)  # 25
```

#### Returning a Function

```python
def make_multiplier(n):
    def multiplier(x):
        return x * n
    return multiplier

times3 = make_multiplier(3)
print(times3(10))  # 30
```

---

### 2.3 Built-in Higher-Order Functions

Python provides many higher-order functions:

| Function | Description |
|----------|-------------|
| `map(func, iterable)` | Apply a function to each item |
| `filter(func, iterable)` | Filter items based on a condition |
| `reduce(func, iterable)` | Apply function cumulatively (from `functools`) |

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)    # [2, 4]

product = reduce(lambda x, y: x * y, numbers)
print(product)  # 120
```

---

## 3. Combining Instances and Higher-Order Functions

```python
class Player:
    def __init__(self, name, score):
        self.name = name
        self.score = score

players = [Player("Alice", 10), Player("Bob", 15), Player("Charlie", 12)]

# Use higher-order function to sort players by score
sorted_players = sorted(players, key=lambda p: p.score, reverse=True)
for p in sorted_players:
    print(p.name, p.score)
```

- Instances hold **state**, and higher-order functions can **operate on collections of instances**  

---

## 4. Key Takeaways

1. **Instances** are individual objects created from classes  
2. **State** is the current attribute values of an instance  
3. **Methods** can change an instance’s state  
4. **Higher-order functions** make code more flexible and reusable  
5. Combining OOP and higher-order functions allows **powerful, modular designs**  

---

Optional Enhancements:
- Practice creating **stateful objects** for a game or simulation  
- Use **map/filter/reduce** to analyze data in lists of instances  
- Create **factory functions** that return customized objects  

Understanding instances, state, and higher-order functions is **crucial for building scalable Python programs**.
