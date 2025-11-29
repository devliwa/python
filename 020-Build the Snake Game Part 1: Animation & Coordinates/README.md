# Build the Snake Game: Animation & Coordinates in Python

This lesson covers:
- Creating a **Snake Game** in Python  
- Using **animation**, **coordinates**, and **game logic**  
- Applying **OOP and functions** for interactive gameplay  

---

## 1. Introduction to the Snake Game

- Classic arcade game where the player controls a **snake**  
- Snake moves around the screen eating **food**  
- Each time the snake eats, it **grows longer**  
- Game ends if the snake **hits the wall or itself**  

---

## 2. Using Turtle for Animation

- `turtle` library allows **animated movement using coordinates**  
- The **screen updates** to show movement  

```python
import turtle

screen = turtle.Screen()
screen.setup(width=600, height=600)
screen.bgcolor("black")
screen.title("Snake Game")
screen.tracer(0)  # Turn off automatic screen updates
```

- `tracer(0)` lets us **manually update the screen** for smoother animation  
- Use `screen.update()` after drawing  

---

## 3. Creating the Snake

```python
segments = []

def create_snake():
    for i in range(3):
        segment = turtle.Turtle("square")
        segment.color("white")
        segment.penup()
        segment.goto(x=-20*i, y=0)  # Set initial coordinates
        segments.append(segment)

create_snake()
```

- Each segment is a **turtle object**  
- Use `penup()` to prevent drawing lines  
- `goto(x, y)` positions each segment  

---

## 4. Moving the Snake

```python
def move():
    for i in range(len(segments)-1, 0, -1):
        x = segments[i-1].xcor()
        y = segments[i-1].ycor()
        segments[i].goto(x, y)
    segments[0].forward(20)
```

- **Segments follow the head**  
- Head moves forward, body segments move to the previous segment’s position  

---

## 5. Controlling the Snake

```python
def go_up():
    if segments[0].heading() != 270:
        segments[0].setheading(90)

def go_down():
    if segments[0].heading() != 90:
        segments[0].setheading(270)

def go_left():
    if segments[0].heading() != 0:
        segments[0].setheading(180)

def go_right():
    if segments[0].heading() != 180:
        segments[0].setheading(0)

screen.listen()
screen.onkey(go_up, "Up")
screen.onkey(go_down, "Down")
screen.onkey(go_left, "Left")
screen.onkey(go_right, "Right")
```

- `heading()` gets the current direction in degrees  
- Prevents snake from **reversing into itself**  

---

## 6. Adding Food

```python
food = turtle.Turtle("circle")
food.color("red")
food.penup()
food.goto(100, 100)

# Check collision with food
if segments[0].distance(food) < 20:
    food.goto(random.randint(-280, 280), random.randint(-280, 280))
    # Add a new segment
```

- Use `distance()` to detect **collision between snake and food**  
- Randomly reposition food when eaten  

---

## 7. Detecting Collisions

```python
# Wall collision
if abs(segments[0].xcor()) > 290 or abs(segments[0].ycor()) > 290:
    game_over = True

# Self collision
for segment in segments[1:]:
    if segments[0].distance(segment) < 10:
        game_over = True
```

- Game ends if snake **hits walls** or **its own body**  

---

## 8. Main Game Loop

```python
import time

game_over = False

while not game_over:
    screen.update()
    move()
    # check for food collision
    # check for wall or self collision
    time.sleep(0.1)  # Controls snake speed
```

- Use `time.sleep()` to **control animation speed**  
- `screen.update()` redraws all objects  

---

## 9. Optional Enhancements

- Add **scoreboard**  
- Increase **speed** as snake grows  
- Add **levels or obstacles**  
- Change snake and food **colors or shapes**  
- Add **sound effects**  

---

## 10. Key Takeaways

- **Coordinates** are essential for snake movement and collision detection  
- **Turtle objects** can act as moving segments  
- **Animation** is achieved using `screen.update()` and `time.sleep()`  
- **OOP and functions** help organize code for snake creation, movement, and collision handling  
- The Snake Game demonstrates **interactive graphics, user input, and real-time updates**  

Building the Snake Game is an **excellent project** to learn **animation, game logic, and coordinate management in Python**.
