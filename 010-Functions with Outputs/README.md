# Review: Functions with Outputs in Python

Functions in Python can **perform tasks** and optionally **return results**. Using outputs makes your functions reusable and allows data to flow through your program.

---

## 1. Basics of Function Outputs

- Functions that **return a value** use the `return` keyword.
- The value can be stored in a variable or used directly.

### Example

```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)  # Output: 8
```

---

## 2. Returning Values vs Printing

- `return` → gives a value back to the caller
- `print` → only displays output, does not pass data

```python
def greet(name):
    return f"Hello, {name}!"

message = greet("Charles")
print(message)  # Output: Hello, Charles!
```

---

## 3. Multiple Parameters and Return

Functions can take multiple inputs and return a single output:

```python
def multiply(x, y):
    return x * y

product = multiply(4, 6)
print(product)  # Output: 24
```

---

## 4. Returning Multiple Values

Python allows returning **multiple outputs** as a tuple:

```python
def calculate(a, b):
    sum_ = a + b
    difference = a - b
    return sum_, difference

s, d = calculate(10, 5)
print(s)  # 15
print(d)  # 5
```

---

## 5. Example: Functions with Outputs in Action

### Example 1: Check Even or Odd

```python
def is_even(number):
    return number % 2 == 0

print(is_even(10))  # True
print(is_even(7))   # False
```

### Example 2: Caesar Cipher (Returning Encrypted Text)

```python
def caesar(text, shift):
    result = ""
    alphabet = "abcdefghijklmnopqrstuvwxyz"
    for letter in text:
        if letter in alphabet:
            position = alphabet.index(letter)
            new_position = (position + shift) % 26
            result += alphabet[new_position]
        else:
            result += letter
    return result

encoded = caesar("hello", 3)
print(encoded)  # khoor
```

---

## 6. Benefits of Functions with Outputs

- **Reuse code** without rewriting  
- **Pass results** to other parts of the program  
- **Test parts of your program independently**  
- Make programs **modular and organized**

---

## 7. Best Practices

- Use descriptive function names: `calculate_area`, `encrypt_text`  
- Keep functions **focused on a single task**  
- Return values instead of printing inside the function if possible  
- Use **docstrings** to describe the function  

```python
def multiply(x, y):
    """Return the product of x and y."""
    return x * y
```

---

Functions with outputs are a **core concept in Python**—mastering them allows you to build modular, flexible, and reusable code.

# functions-with-outputs

- [How to convert string to Title Case in Python?](https://stackoverflow.com/questions/8347048/how-to-convert-string-to-title-case-in-python)

#### functions-with-outputs
```python
def format_name(f_name, l_name):
    formated_f_name = f_name.title()
    formated_l_name = l_name.title()
    return f"{formated_f_name} {formated_l_name}"


print(format_name("AnGeLa", "YU"))


def function_1(text):
    return text + text


def function_2(text):
    return text.title()


output = function_2(function_1("hello"))
print(output)
```
#### multiple-return-values
```python
def format_name(f_name, l_name):
    if f_name == "" or l_name == "":
        return "You did not provide valid inputs"
    formated_f_name = f_name.title()
    formated_l_name = l_name.title()
    return f"Result: {formated_f_name} {formated_l_name}"


print(format_name(input("What is your first name?"), input("What is your last name?")))
```
#### docstrings
```python
def format_name(f_name, l_name):
    """Take a first and last name and format it to return the
    title case version of the name."""
    formated_f_name = f_name.title()
    formated_l_name = l_name.title()
    return f"{formated_f_name} {formated_l_name}"


formatted_name = format_name("AnGeLa", "YU")

length = len(formatted_name)
```

#### calculator-project

art.py
```python
logo = r"""
 _____________________
|  _________________  |
| | Pythonista   0. | |  .----------------.  .----------------.  .----------------.  .----------------. 
| |_________________| | | .--------------. || .--------------. || .--------------. || .--------------. |
|  ___ ___ ___   ___  | | |     ______   | || |      __      | || |   _____      | || |     ______   | |
| | 7 | 8 | 9 | | + | | | |   .' ___  |  | || |     /  \     | || |  |_   _|     | || |   .' ___  |  | |
| |___|___|___| |___| | | |  / .'   \_|  | || |    / /\ \    | || |    | |       | || |  / .'   \_|  | |
| | 4 | 5 | 6 | | - | | | |  | |         | || |   / ____ \   | || |    | |   _   | || |  | |         | |
| |___|___|___| |___| | | |  \ `.___.'\  | || | _/ /    \ \_ | || |   _| |__/ |  | || |  \ `.___.'\  | |
| | 1 | 2 | 3 | | x | | | |   `._____.'  | || ||____|  |____|| || |  |________|  | || |   `._____.'  | |
| |___|___|___| |___| | | |              | || |              | || |              | || |              | |
| | . | 0 | = | | / | | | '--------------' || '--------------' || '--------------' || '--------------' |
| |___|___|___| |___| |  '----------------'  '----------------'  '----------------'  '----------------' 
|_____________________|
"""
```
main.py
```python
import art


def add(n1, n2):
    return n1 + n2


def subtract(n1, n2):
    return n1 - n2


def multiply(n1, n2):
    return n1 * n2


def divide(n1, n2):
    return n1 / n2


operations = {
    "+": add,
    "-": subtract,
    "*": multiply,
    "/": divide,
}

# print(operations["*"](4, 8))


def calculator():
    print(art.logo)
    should_accumulate = True
    num1 = float(input("What is the first number?: "))

    while should_accumulate:
        for symbol in operations:
            print(symbol)
        operation_symbol = input("Pick an operation: ")
        num2 = float(input("What is the next number?: "))
        answer = operations[operation_symbol](num1, num2)
        print(f"{num1} {operation_symbol} {num2} = {answer}")

        choice = input(f"Type 'y' to continue calculating with {answer}, or type 'n' to start a new calculation: ")

        if choice == "y":
            num1 = answer
        else:
            should_accumulate = False
            print("\n" * 20)
            calculator()


calculator()
```


