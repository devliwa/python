# Turtle & the Graphical User Interface (GUI) in Python

This lesson covers:
- Using **Turtle** to create graphics in Python  
- Understanding the basics of a **Graphical User Interface (GUI)**  

---

## 1. Introduction to Turtle

- `turtle` is a Python library that allows you to **draw shapes and patterns**  
- Great for beginners to learn **loops, functions, and coordinates** visually  

### 1.1 Importing Turtle

```python
import turtle
```

### 1.2 Creating a Screen and Turtle

```python
wn = turtle.Screen()  # Create a window
wn.bgcolor("lightblue")  # Set background color
wn.title("Turtle Demo")

pen = turtle.Turtle()  # Create turtle object
pen.speed(2)           # Set drawing speed
```

---

## 2. Basic Turtle Commands

| Command                 | Description                       |
|-------------------------|-----------------------------------|
| `forward(100)`           | Move forward by 100 units         |
| `backward(50)`           | Move backward by 50 units        |
| `right(90)`              | Turn right 90 degrees            |
| `left(45)`               | Turn left 45 degrees             |
| `penup()`                | Lift pen (no drawing)            |
| `pendown()`              | Put pen down (start drawing)     |
| `color("red")`           | Change pen color                 |
| `fillcolor("yellow")`    | Set fill color                   |
| `begin_fill()` / `end_fill()` | Fill a shape with color      |

---

## 3. Drawing Shapes

### 3.1 Square

```python
for _ in range(4):
    pen.forward(100)
    pen.right(90)
```

### 3.2 Triangle

```python
for _ in range(3):
    pen.forward(100)
    pen.right(120)
```

### 3.3 Circle

```python
pen.circle(50)
```

---

## 4. Functions with Turtle

```python
def draw_square(size, color):
    pen.color(color)
    pen.begin_fill()
    for _ in range(4):
        pen.forward(size)
        pen.right(90)
    pen.end_fill()

draw_square(100, "red")
```

- Functions allow **reusable shapes**  
- Can combine **loops and parameters** for complex patterns  

---

## 5. Introduction to GUI in Python

- GUI allows **interaction with users visually**  
- Common libraries:  
  - `tkinter` (built-in)  
  - `PyQt`, `Kivy` (advanced)  

### 5.1 Creating a Simple Tkinter Window

```python
import tkinter as tk

window = tk.Tk()            # Create window
window.title("My GUI App")  # Set title
window.geometry("300x200")  # Set size

label = tk.Label(window, text="Hello, GUI!")
label.pack()

window.mainloop()            # Keep window open
```

---

## 6. Combining Turtle with GUI

- Turtle can run inside a **Tkinter window**  
- Example: Use buttons to control Turtle movement  

```python
import turtle
import tkinter as tk

def move_forward():
    t.forward(50)

root = tk.Tk()
root.title("Turtle GUI")

canvas = tk.Canvas(master=root, width=400, height=400)
canvas.pack()

t = turtle.RawTurtle(canvas)
t.speed(1)

button = tk.Button(root, text="Move Forward", command=move_forward)
button.pack()

root.mainloop()
```

---

## 7. Key Takeaways

- **Turtle** helps beginners visualize loops, coordinates, and functions  
- **GUI programming** introduces user interaction  
- Combining Turtle and GUI makes projects **interactive and fun**  
- Great stepping stone for **games or visual applications** in Python  

---

Optional Enhancements:
- Draw **complex patterns or spirals** with Turtle  
- Add **buttons and inputs** in GUI for interactive apps  
- Integrate **score counters or animations** for games  

Turtle and GUI projects are **fun, visual, and highly educational** for learning Python concepts.
