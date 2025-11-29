# Understanding Data Types and How to Manipulate Strings

In Python, **data types** define the type of data a variable can hold. Understanding them is essential for data management and manipulation.

---

## 1. Common Data Types in Python

| Data Type | Example | Description |
|-----------|---------|-------------|
| `int`     | `10`    | Whole numbers |
| `float`   | `3.14`  | Decimal numbers |
| `str`     | `"Hello"` | Text or string |
| `bool`    | `True` / `False` | Boolean values |
| `list`    | `[1, 2, 3]` | Ordered collection of items |
| `tuple`   | `(1, 2, 3)` | Immutable collection of items |
| `dict`    | `{"key": "value"}` | Key-value pairs |

---

## 2. Working with Strings

Strings (`str`) are sequences of characters. They can be manipulated in many ways:

```python
# Creating strings
greeting = "Hello, World!"
name = "Alice"

# Accessing characters
print(greeting[0])      # Output: H
print(greeting[-1])     # Output: !

# Slicing strings
print(greeting[0:5])    # Output: Hello
print(greeting[7:12])   # Output: World
```

---

## 3. String Manipulation Methods

Python provides built-in methods to manipulate strings:

```python
text = " python programming "

# Remove whitespace
print(text.strip())          # Output: python programming

# Convert to uppercase or lowercase
print(text.upper())          # Output:  PYTHON PROGRAMMING 
print(text.lower())          # Output:  python programming

# Replace a word
print(text.replace("python", "Java"))  # Output:  Java programming

# Check content
print(text.startswith(" python"))      # Output: True
print(text.endswith("programming "))   # Output: True
```

---

## 4. String Formatting

Combine variables and strings easily using **f-strings**:

```python
name = "Alice"
age = 17

# Using f-string
info = f"{name} is {age} years old."
print(info)           # Output: Alice is 17 years old.
```

---

## 5. Combining Strings

```python
# Concatenation
greeting = "Hello, " + name + "!"
print(greeting)       # Output: Hello, Alice!

# Repeating strings
laugh = "Ha" * 3
print(laugh)          # Output: HaHaHa
```

---

## 6. Example: Data Types and Strings in Action

```python
# User profile
username = "charles"
age = 17
status = "active"

# Display profile
profile = f"User {username} is {age} years old and currently {status}."
print(profile)

# Manipulate string
profile_upper = profile.upper()
print(profile_upper)
```

**Output:**
```
User charles is 17 years old and currently active.
USER CHARLES IS 17 YEARS OLD AND CURRENTLY ACTIVE.
```

---

Understanding data types and string manipulation allows you to **handle and format data effectively** in Python, which is essential for real-world programming.