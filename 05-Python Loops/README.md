# Python Loops

Loops allow you to repeat actions without rewriting code. They are essential for automation, iteration, and working with lists, strings, and data.

Python has two main types of loops:
- **`for` loops** — used to iterate over a sequence
- **`while` loops** — used to repeat actions while a condition is true

---

## 1. `for` Loops

A `for` loop goes through each item in a sequence (like a list, string, or range).

### Looping Through a List

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
```

**Output:**
```
apple
banana
cherry
```

---

### Looping Through a String

```python
for letter in "Python":
    print(letter)
```

---

### Using `range()`

`range()` generates a sequence of numbers.

```python
for number in range(5):
    print(number)
```

**Output:**  
```
0
1
2
3
4
```

### Start and End Range

```python
for num in range(2, 7):
    print(num)
```

**Output:**
```
2
3
4
5
6
```

---

## 2. `while` Loops

A `while` loop runs **as long as the condition is true**.

```python
count = 0

while count < 3:
    print("Count:", count)
    count += 1
```

**Output:**
```
Count: 0
Count: 1
Count: 2
```

---

## 3. Loop Control Statements

### `break` — Stop the Loop

```python
for num in range(10):
    if num == 5:
        break
    print(num)
```

**Stops at 4.**

---

### `continue` — Skip Current Iteration

```python
for num in range(5):
    if num == 2:
        continue
    print(num)
```

**Skips 2.**

---

### `pass` — Placeholder

```python
for num in range(3):
    pass  # Do nothing (placeholder)
```

---

## 4. Nested Loops

You can put a loop inside another loop.

```python
for i in range(3):
    for j in range(2):
        print(i, j)
```

**Output:**
```
0 0
0 1
1 0
1 1
2 0
2 1
```

---

## 5. Example Projects Using Loops

### Example 1: Countdown

```python
count = 5
while count > 0:
    print(count)
    count -= 1
print("Go!")
```

---

### Example 2: Sum of Numbers 1–100

```python
total = 0
for num in range(1, 101):
    total += num

print(total)
```

---

### Example 3: Loop Through a List and Capitalize Items

```python
names = ["charles", "maya", "john"]

for name in names:
    print(name.capitalize())
```

---

Loops are one of the most powerful tools in Python—they help you automate work, process data, and build real projects efficiently.