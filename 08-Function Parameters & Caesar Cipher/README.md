# Function Parameters & Caesar Cipher

This lesson covers:
- What function parameters are  
- How to use parameters effectively  
- How to build a Caesar Cipher using functions  

The Caesar Cipher is a beginner-friendly encryption technique that helps you practice functions, loops, and string manipulation.

---

# 1. Function Parameters in Python

Parameters allow your functions to **receive information**.

### Basic Example

```python
def greet(name):
    print(f"Hello, {name}!")
```

Calling the function:

```python
greet("Charles")
```

**Why parameters matter:**
- They make functions flexible  
- You can reuse the same function with different values  
- They help break down complex tasks  

---

# 2. Functions With Multiple Parameters

```python
def add(a, b):
    return a + b
```

```python
result = add(5, 3)
print(result)
```

---

# 3. Keyword Arguments

You can call functions using parameter names:

```python
def power(base, exponent):
    return base ** exponent

print(power(exponent=3, base=2))
```

---

# 4. Default Parameters

Default values are used if the user doesn't provide one.

```python
def greet(name="friend"):
    print(f"Hello, {name}!")
```

```python
greet()  
greet("Charles")
```

---

# 5. Introducing the Caesar Cipher

The **Caesar Cipher** shifts each letter in a message by a chosen number.

Example (shift of 3):  
A → D  
B → E  
C → F  
z → c

It's a great project to practice:
- Loops  
- Lists  
- Strings  
- Function parameters  

---

# 6. Creating the Caesar Cipher Function

### Alphabet Setup

```python
alphabet = ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m",
            "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"]
```

---

# 7. Building the `caesar()` Function

The function should accept:
- `text` → the message  
- `shift` → how many positions to move letters  
- `direction` → `"encode"` or `"decode"`  

### Full Function

```python
def caesar(text, shift, direction):
    result = ""

    # Reverse shift for decoding
    if direction == "decode":
        shift *= -1

    for letter in text:
        if letter in alphabet:
            position = alphabet.index(letter)
            new_position = (position + shift) % 26
            result += alphabet[new_position]
        else:
            # Keep symbols, numbers, or spaces as they are
            result += letter

    print(f"Here is your {direction}d text: {result}")
```

---

# 8. Using the Function

```python
direction = input("Type 'encode' or 'decode': ")
text = input("Enter your message: ").lower()
shift = int(input("Shift amount: "))

caesar(text, shift, direction)
```

---

# 9. Example Run

Input:
```
encode  
hello  
3
```

Output:
```
Khoor
```

---

# 10. Improvements You Can Add

- Allow repeating the program  
- Large shift values (e.g., shift = 100)  
- Handle uppercase letters  
- Add error messages  
- Add symbols/emojis support  

---

# 11. Summary

**Function Parameters**  
- Make functions flexible and reusable  
- Can have defaults  
- Can be used as keywords

**Caesar Cipher**  
- Uses loops, lists, strings  
- Great project for practicing function parameters  
- Helps build coding logic step by step

## Project Caesar Cipher
```python
logo = """           
 ,adPPYba, ,adPPYYba,  ,adPPYba, ,adPPYba, ,adPPYYba, 8b,dPPYba,  
a8"     "" ""     `Y8 a8P_____88 I8[    "" ""     `Y8 88P'   "Y8  
8b         ,adPPPPP88 8PP"""""""  `"Y8ba,  ,adPPPPP88 88          
"8a,   ,aa 88,    ,88 "8b,   ,aa aa    ]8I 88,    ,88 88          
 `"Ybbd8"' `"8bbdP"Y8  `"Ybbd8"' `"YbbdP"' `"8bbdP"Y8 88   
            88             88                                 
           ""             88                                 
                          88                                 
 ,adPPYba, 88 8b,dPPYba,  88,dPPYba,   ,adPPYba, 8b,dPPYba,  
a8"     "" 88 88P'    "8a 88P'    "8a a8P_____88 88P'   "Y8  
8b         88 88       d8 88       88 8PP""""""" 88          
"8a,   ,aa 88 88b,   ,a8" 88       88 "8b,   ,aa 88          
 `"Ybbd8"' 88 88`YbbdP"'  88       88  `"Ybbd8"' 88          
              88                                             
              88           
"""
import art

print(art.logo)

alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u',
            'v', 'w', 'x', 'y', 'z']


def caesar(original_text, shift_amount, encode_or_decode):
    output_text = ""
    if encode_or_decode == "decode":
        shift_amount *= -1

    for letter in original_text:

        if letter not in alphabet:
            output_text += letter
        else:
            shifted_position = alphabet.index(letter) + shift_amount
            shifted_position %= len(alphabet)
            output_text += alphabet[shifted_position]
    print(f"Here is the {encode_or_decode}d result: {output_text}")


should_continue = True

while should_continue:

    direction = input("Type 'encode' to encrypt, type 'decode' to decrypt:\n").lower()
    text = input("Type your message:\n").lower()
    shift = int(input("Type the shift number:\n"))

    caesar(original_text=text, shift_amount=shift, encode_or_decode=direction)

    restart = input("Type 'yes' if you want to go again. Otherwise, type 'no'.\n").lower()
    if restart == "no":
        should_continue = False
        print("Goodbye")


```
