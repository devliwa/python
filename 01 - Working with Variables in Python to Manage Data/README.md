# Working with Variables in Python to Manage Data

Variables are used in Python to store and manage data. They act as **containers** for information that your program can manipulate.

## 1. Creating Variables

To create a variable, assign a value using the `=` operator:

```python
# Examples
name = "Alice"       # String
age = 25             # Integer
height = 5.7         # Float
is_student = True    # Boolean
```

**Rules for Variable Names:**
- Must start with a letter or underscore (`_`)
- Can only contain letters, numbers, and underscores
- Cannot be a Python reserved keyword (like `for`, `if`, `while`)

---

## 2. Using Variables

You can use variables in operations, print them, or modify their values:

```python
# Using variables
print(name)          # Output: Alice
age += 1             # Increment age by 1
print(age)           # Output: 26

# Combining variables
info = name + " is " + str(age) + " years old."
print(info)          # Output: Alice is 26 years old.
```

---

## 3. Data Types

Python variables can store different **data types**:

| Type      | Example           |
|-----------|-----------------|
| String    | `"Hello"`        |
| Integer   | `10`             |
| Float     | `3.14`           |
| Boolean   | `True` / `False` |
| List      | `[1, 2, 3]`      |
| Dictionary | `{"key": "value"}` |

---

## 4. Dynamic Typing

Python is **dynamically typed**, which means you can change the type of a variable:

```python
value = 10
print(value)        # Output: 10

value = "Ten"
print(value)        # Output: Ten
```

---

## 5. Best Practices

- Use descriptive variable names: `age` is better than `a`
- Keep variable names lowercase with underscores: `first_name`
- Avoid using single letters except in loops or temporary variables

---

## 6. Example: Managing Data with Variables

```python
# Store user information
username = "charles"
user_age = 17
user_score = 95.5

# Calculate new score
user_score += 4.5

# Print user details
print(f"{username} is {user_age} years old and scored {user_score} points.")
```

**Output:**
```
charles is 17 years old and scored 100.0 points.
```

---

Variables are the **building blocks** for managing and manipulating data in Python. Once you understand how to use them, you can start creating more complex programs.