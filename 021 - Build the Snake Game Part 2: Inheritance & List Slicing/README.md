# Build the Snake Game: Inheritance & List Slicing in Python

This lesson focuses on enhancing the **Snake Game** using:
- **Inheritance** to organize classes  
- **List slicing** to manage the snake’s body  

---

## 1. Recap: Snake Game Structure

- **Snake** is made of multiple segments (turtle objects)  
- **Head** controls direction  
- **Body** follows the head  
- **Food** appears randomly on the screen  
- **Collisions** end the game  

---

## 2. Using Inheritance

### 2.1 Why Inheritance?

- Avoid repeating code for multiple objects  
- Create a **base class** for common properties/methods  
- Extend behavior with **child classes**  

---

### 2.2 Base Class: `GameObject`

```python
import turtle

class GameObject:
    def __init__(self, shape, color, position):
        self.obj = turtle.Turtle(shape)
        self.obj.color(color)
        self.obj.penup()
        self.obj.goto(position)
```

- `GameObject` handles **basic setup for a turtle object**  

---

### 2.3 Snake Segment as Child Class

```python
class SnakeSegment(GameObject):
    def __init__(self, position):
        super().__init__("square", "white", position)
```

- Inherits **position, shape, and color initialization** from `GameObject`  
- Can later add **movement or collision methods**  

---

### 2.4 Food as Child Class

```python
import random

class Food(GameObject):
    def __init__(self):
        x = random.randint(-280, 280)
        y = random.randint(-280, 280)
        super().__init__("circle", "red", (x, y))

    def refresh(self):
        x = random.randint(-280, 280)
        y = random.randint(-280, 280)
        self.obj.goto(x, y)
```

- `Food` can **reposition itself** when eaten  
- Inherits base setup from `GameObject`  

---

## 3. Using List Slicing for the Snake Body

- Snake body is stored as a **list of segments**  
- **List slicing** helps move the body efficiently  

### 3.1 Moving the Snake

```python
def move_snake(snake):
    # Move body segments to follow the head
    for idx in range(len(snake)-1, 0, -1):
        new_x = snake[idx-1].obj.xcor()
        new_y = snake[idx-1].obj.ycor()
        snake[idx].obj.goto(new_x, new_y)
    # Move the head forward
    snake[0].obj.forward(20)
```

- `snake[1:]` or `snake[:-1]` can be used for **body slicing**  
- Example: Update all segments **except the head**  

---

### 3.2 Growing the Snake

```python
def add_segment(snake):
    tail_position = snake[-1].obj.position()
    new_segment = SnakeSegment(tail_position)
    snake.append(new_segment)
```

- New segments are **added at the tail**  
- List slicing ensures **movement logic remains consistent**  

---

## 4. Combining Inheritance and List Slicing

```python
snake = [SnakeSegment((0,0)), SnakeSegment((-20,0)), SnakeSegment((-40,0))]
food = Food()

# Main game loop
while True:
    move_snake(snake)
    if snake[0].obj.distance(food.obj) < 15:
        add_segment(snake)
        food.refresh()
```

- Head (index 0) is controlled separately  
- Body segments follow using **list slicing or loop through `snake[1:]`**  

---

## 5. Optional Enhancements

- Add **different types of food** with points  
- Create **Obstacle** class inheriting from `GameObject`  
- Track **high score** and display on the screen  
- Animate **snake color changes** as it grows  

---

## 6. Key Takeaways

- **Inheritance** reduces code repetition and makes game objects modular  
- **List slicing** efficiently handles **snake body movement**  
- Combining both concepts makes the Snake Game:
  - Easier to **maintain**  
  - Easier to **expand** with new features  
- Good practice for **OOP, animation, and real-time game logic**  

This approach allows you to build a **scalable Snake Game** suitable for learning **advanced Python concepts**.
