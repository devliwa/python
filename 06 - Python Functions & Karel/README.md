# Python Functions & Karel

Functions help you organize code into reusable blocks. When learning Python, many beginners practice functions using **Karel the Robot**, a simple programming environment where you control a robot using commands.

This lesson teaches:
- What functions are  
- How to define and call them in Python  
- How Karel uses functions to break down tasks  

---

## 1. What Is a Function?

A **function** is a reusable chunk of code that performs a specific task.

### Why use functions?
- Avoid repeating code  
- Make programs easier to read and maintain  
- Break big problems into smaller steps  

---

## 2. Defining a Function in Python

Use `def` to define a function:

```python
def greet():
    print("Hello!")
```

### Calling the function:

```python
greet()
```

---

## 3. Functions With Parameters

Parameters allow you to pass information into a function.

```python
def greet(name):
    print(f"Hello, {name}!")
```

Call it like this:

```python
greet("Charles")
```

---

## 4. Functions With Return Values

Some functions send information back using `return`.

```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)   # Output: 8
```

---

## 5. Why Functions Matter in Karel

Karel uses simple commands:
- `move()`
- `turn_left()`
- `pick_beeper()`
- `put_beeper()`

But complex tasks require **combining commands**.

Functions allow you to build higher-level actions.

---

## 6. Creating Functions in Karel

### Example: Define and use a function to turn right

Karel doesn’t have a built-in `turn_right()`, so you define one:

```python
def turn_right():
    turn_left()
    turn_left()
    turn_left()
```

Now you can use:

```python
turn_right()
```

---

## 7. Example: Make Karel Build a Square

```python
def move_square():
    move()
    turn_left()
    move()
    turn_left()
    move()
    turn_left()
    move()
    turn_left()
```

Call it:

```python
move_square()
```

---

## 8. Combining Python Logic and Karel Functions

### Example: Pick 5 beepers

```python
def pick_five_beepers():
    for _ in range(5):
        pick_beeper()
```

### Example: Move forward 3 steps

```python
def move_steps(steps):
    for _ in range(steps):
        move()
```

Call it:

```python
move_steps(3)
```

---

## 9. Best Practices for Functions

- Use **clear names**: `turn_right()`, not `tr()`
- Keep each function focused on one task  
- Reuse functions inside bigger functions  
- Break long tasks into small pieces  

---

## 10. Full Example: Karel Goes to the Wall and Picks a Beeper

```python
def move_to_wall():
    while front_is_clear():
        move()

def pick_beeper_and_return():
    pick_beeper()
    turn_left()
    turn_left()
    move_to_wall()

# Main program
move_to_wall()
pick_beeper_and_return()
```

---

Functions make both Python programming and Karel tasks **clean, organized, and easy to expand**.

If you want, I can also create:
- A full **Karel project assignment**
- A **beginner Python functions worksheet**
- A **combined PDF lesson**