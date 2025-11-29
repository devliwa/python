# Debugging: How to Find and Fix Errors in Your Code

Debugging is an essential skill in programming. It helps you **identify, understand, and fix errors** so your code runs as expected.

---

## 1. Types of Errors in Python

Python errors can be grouped into three main types:

### 1.1 Syntax Errors
- Occur when the code **does not follow Python rules**  
- Usually easy to spot because Python highlights them

```python
# SyntaxError: Missing colon
if 5 > 2
    print("Hello")
```

---

### 1.2 Runtime Errors
- Happen **while the program is running**  
- Cause the program to stop unexpectedly

```python
# ZeroDivisionError
x = 10 / 0
```

---

### 1.3 Logic Errors
- The program **runs without crashing** but produces **wrong results**  
- Often the hardest to detect

```python
# Logic error: calculates area incorrectly
length = 5
width = 3
area = length + width  # Should be length * width
print(area)  # Output: 8 (incorrect)
```

---

## 2. Common Debugging Techniques

### 2.1 Read Error Messages Carefully
- Python tells you:
  - **Type of error**  
  - **Line number**  
  - Sometimes **reason**  

### 2.2 Use Print Statements
- Print variable values at different points to check if the program is behaving as expected

```python
x = 10
y = 0
print("x:", x, "y:", y)
```

### 2.3 Check Logic Step by Step
- Break down the program into small parts  
- Test each part separately  

### 2.4 Use a Debugger
- IDEs like VS Code or PyCharm have debuggers  
- You can **set breakpoints** and **inspect variables**  

### 2.5 Rubber Duck Debugging
- Explain your code line by line to someone else (or an imaginary "rubber duck")  
- Often you find mistakes just by talking through the logic  

---

## 3. Example: Debugging a Function

### Problem Code

```python
def add_numbers(a, b):
    result = a - b  # Logic error
    return result

print(add_numbers(5, 3))  # Output: 2 (wrong)
```

### Steps to Debug
1. Read the code  
2. Notice the `-` instead of `+`  
3. Fix it:

```python
def add_numbers(a, b):
    result = a + b
    return result

print(add_numbers(5, 3))  # Output: 8 (correct)
```

---

## 4. Tips to Avoid Common Errors

- **Indent properly** (Python is indentation-sensitive)  
- **Check spelling** of variables and functions  
- **Use consistent data types**  
- **Comment your code** for clarity  
- **Test frequently** as you build programs  

---

## 5. Practice Debugging

### Exercise
```python
# This code should calculate the area of a rectangle
length = 10
width = 5
area = length + width  # Bug here
print("Area:", area)
```
- Find and fix the error  

### Solution
```python
area = length * width
print("Area:", area)  # Correct output: 50
```

---

## 6. Summary

- Debugging is **finding and fixing errors**  
- Types of errors: **Syntax, Runtime, Logic**  
- Techniques:
  - Read error messages  
  - Use print statements  
  - Test small pieces of code  
  - Use a debugger  
  - Talk through your logic  

Debugging is a **critical skill for every programmer**, helping you write **correct and reliable code**.

# debugging-how-to-find-and-fix-errors-in-your-code

- [python-questions](https://stackoverflow.com/questions/tagged/python)

#### describe-the-problem
```python
def my_function():
    for i in range(1, 21):
        if i == 20:
            print("You got it")


my_function()
```

#### reproduce-the-bug
```python
from random import randint
dice_images = ["❶", "❷", "❸", "❹", "❺", "❻"]
dice_num = randint(0, 5)
print(dice_images[dice_num])

```

#### play-computer
```python
year = int(input("What's your year of birth?"))

if year > 1980 and year < 1994:
    print("You are a millennial.")
elif year >= 1994:
    print("You are a Gen Z.")

```

#### fix-the-errors
```python
try:
    age = int(input("How old are you?"))
except ValueError:
    print("You have typed in a an invalid number. Please try again with a numerical response such as 15.")
    age = int(input("How old are you?"))

if age > 18:
    print(f"You can drive at age {age}.")

```
#### use-print
```python
pages = int(input("Number of pages: "))
word_per_page = int(input("Number of words per page: "))
total_words = pages * word_per_page

print(f"pages = {pages}")
print(f"words_per_page = {word_per_page}")
print(total_words)

```

#### use-a-debugger

math.py
```python
def add(n1, n2):
    return n1 + n2
```

main.py
```python
import random
import maths


def mutate(a_list):
    b_list = []
    new_item = 0
    for item in a_list:
        new_item = item * 2
        new_item += random.randint(1, 3)
        new_item = maths.add(new_item, item)
        b_list.append(new_item)
    print(b_list)


mutate([1, 2, 3, 5, 8, 13])
```

