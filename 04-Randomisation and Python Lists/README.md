# Randomisation and Python Lists

Randomisation lets your programs generate **unpredictable results**, such as random numbers or random choices. Python lists help you store and organize multiple items. Together, they’re powerful tools for building games, simulations, and more.

---

## 1. Using the `random` Module

Before using randomisation features, you must import Python’s built-in `random` module:

```python
import random
```

---

## 2. Random Numbers

### Generate a Random Integer

```python
import random

random_number = random.randint(1, 10)
print(random_number)
```

This prints a random number between **1 and 10** (inclusive).

### Generate a Random Float

```python
random_float = random.random()
print(random_float)
```

This prints a random float between **0.0 and 1.0**.

### Random Float in a Range

```python
random_range = random.uniform(1, 5)
print(random_range)
```

---

## 3. Introduction to Python Lists

Lists store multiple items in a single variable:

```python
fruits = ["apple", "banana", "cherry"]
```

### Accessing List Items

```python
print(fruits[0])   # apple
print(fruits[-1])  # cherry
```

### Changing List Items

```python
fruits[1] = "mango"
print(fruits)   # ['apple', 'mango', 'cherry']
```

---

## 4. Common List Operations

### Adding Items

```python
fruits.append("orange")  # Add to end
fruits.insert(1, "grape")  # Add at position
```

### Removing Items

```python
fruits.remove("apple")   # Remove by value
fruits.pop(0)            # Remove by index
```

### Getting the Length of a List

```python
print(len(fruits))
```

---

## 5. Using Randomisation With Lists

### Choose a Random Item From a List

```python
import random

names = ["Alice", "Bob", "Charlie", "David"]
random_person = random.choice(names)
print(random_person)
```

### Shuffle a List

```python
random.shuffle(names)
print(names)
```

### Pick Multiple Random Items

```python
sample_pick = random.sample(names, 2)
print(sample_pick)
```

---

## 6. Example: Simple Random Generator

### Random Winner Selector

```python
import random

players = ["charles", "john", "maya", "sophia"]

winner = random.choice(players)
print(f"The winner is: {winner}")
```

### Random Dice Roll

```python
import random

dice = random.randint(1, 6)
print(f"You rolled a {dice}!")
```

---

Randomisation and lists are essential tools for building **games, decision-makers, simulations, and creative programs** in Python.