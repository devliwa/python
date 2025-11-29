# Control Flow and Logical Operators in Python

Control flow allows your program to **make decisions and repeat actions** based on conditions. Logical operators help combine or modify these conditions.

---

## 1. Conditional Statements

Python uses `if`, `elif`, and `else` to make decisions:

```python
age = 17

if age >= 18:
    print("You are an adult.")
elif age >= 13:
    print("You are a teenager.")
else:
    print("You are a child.")
```

**Output:**
```
You are a teenager.
```

---

## 2. Comparison Operators

Comparison operators are used in conditions:

| Operator | Example      | Meaning                  |
|----------|-------------|--------------------------|
| `==`     | `x == y`    | Equal to                 |
| `!=`     | `x != y`    | Not equal to             |
| `>`      | `x > y`     | Greater than             |
| `<`      | `x < y`     | Less than                |
| `>=`     | `x >= y`    | Greater than or equal to |
| `<=`     | `x <= y`    | Less than or equal to    |

---

## 3. Logical Operators

Logical operators combine multiple conditions:

| Operator | Example         | Meaning                         |
|----------|----------------|---------------------------------|
| `and`    | `x > 0 and x < 10` | True if both conditions are true |
| `or`     | `x < 0 or x > 10`  | True if at least one condition is true |
| `not`    | `not(x > 0)`       | Inverts the condition           |

```python
x = 7

if x > 0 and x < 10:
    print("x is a positive single-digit number.")

if x < 0 or x > 5:
    print("x is either negative or greater than 5.")

if not x == 5:
    print("x is not 5.")
```

**Output:**
```
x is a positive single-digit number.
x is either negative or greater than 5.
x is not 5.
```

---

## 4. Loops

Loops let you **repeat actions**.

### `while` Loop

```python
count = 0
while count < 5:
    print("Count:", count)
    count += 1
```

**Output:**
```
Count: 0
Count: 1
Count: 2
Count: 3
Count: 4
```

### `for` Loop

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

## 5. Example: Control Flow in Action

```python
# Check if a number is even or odd
num = 8

if num % 2 == 0:
    print(f"{num} is even.")
else:
    print(f"{num} is odd.")

# Loop through numbers and check positivity
numbers = [-1, 0, 3]
for n in numbers:
    if n > 0:
        print(f"{n} is positive.")
    elif n == 0:
        print(f"{n} is zero.")
    else:
        print(f"{n} is negative.")
```

**Output:**
```
8 is even.
-1 is negative.
0 is zero.
3 is positive.
```

---

Mastering control flow and logical operators allows your Python programs to **make intelligent decisions and repeat tasks efficiently**.