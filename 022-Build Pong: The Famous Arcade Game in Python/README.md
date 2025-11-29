# Build Pong: The Famous Arcade Game in Python

This lesson covers:
- Creating the classic **Pong game**  
- Using **Turtle for graphics**  
- Handling **user input, collision detection, and scoring**  
- Applying **OOP and functions** for gameplay  

---

## 1. Introduction to Pong

- Pong is a classic **2D arcade game**  
- Players control **paddles** to bounce a **ball**  
- Ball bounces off walls and paddles  
- Each missed ball gives a **point to the opponent**  

---

## 2. Setting Up the Screen

```python
import turtle

screen = turtle.Screen()
screen.title("Pong")
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.tracer(0)  # Turn off automatic updates
```

- `tracer(0)` allows **manual screen updates** for smooth animation  

---

## 3. Creating the Paddles

```python
class Paddle(turtle.Turtle):
    def __init__(self, position):
        super().__init__()
        self.shape("square")
        self.color("white")
        self.shapesize(stretch_wid=5, stretch_len=1)
        self.penup()
        self.goto(position)

    def move_up(self):
        y = self.ycor() + 20
        self.sety(y)

    def move_down(self):
        y = self.ycor() - 20
        self.sety(y)

left_paddle = Paddle((-350, 0))
right_paddle = Paddle((350, 0))
```

- Stretch paddles with `shapesize()`  
- Movement controlled by **up/down methods**  

---

## 4. Creating the Ball

```python
class Ball(turtle.Turtle):
    def __init__(self):
        super().__init__()
        self.shape("circle")
        self.color("white")
        self.penup()
        self.goto(0, 0)
        self.dx = 0.2  # x movement
        self.dy = 0.2  # y movement

    def move(self):
        self.setx(self.xcor() + self.dx)
        self.sety(self.ycor() + self.dy)
```

- `dx` and `dy` control **ball speed and direction**  

---

## 5. Paddle Movement Control

```python
screen.listen()
screen.onkeypress(left_paddle.move_up, "w")
screen.onkeypress(left_paddle.move_down, "s")
screen.onkeypress(right_paddle.move_up, "Up")
screen.onkeypress(right_paddle.move_down, "Down")
```

- Use `onkeypress()` to handle **keyboard input**  

---

## 6. Ball Collision Logic

### 6.1 Wall Collision

```python
if ball.ycor() > 290 or ball.ycor() < -290:
    ball.dy *= -1  # Reverse vertical direction
```

### 6.2 Paddle Collision

```python
if (ball.dx > 0 and 340 < ball.xcor() < 350 and 
    right_paddle.ycor() - 50 < ball.ycor() < right_paddle.ycor() + 50):
    ball.dx *= -1

if (ball.dx < 0 and -350 < ball.xcor() < -340 and 
    left_paddle.ycor() - 50 < ball.ycor() < left_paddle.ycor() + 50):
    ball.dx *= -1
```

- Reverse `dx` when hitting a paddle  

### 6.3 Scoring

```python
left_score = 0
right_score = 0

if ball.xcor() > 390:
    left_score += 1
    ball.goto(0, 0)
    ball.dx *= -1

if ball.xcor() < -390:
    right_score += 1
    ball.goto(0, 0)
    ball.dx *= -1
```

- Reset ball to the **center after a score**  

---

## 7. Displaying Score

```python
score_display = turtle.Turtle()
score_display.speed(0)
score_display.color("white")
score_display.penup()
score_display.hideturtle()
score_display.goto(0, 260)
score_display.write("0 : 0", align="center", font=("Courier", 24, "normal"))

def update_score():
    score_display.clear()
    score_display.write(f"{left_score} : {right_score}", align="center", font=("Courier", 24, "normal"))
```

- Update score **after each point**  

---

## 8. Main Game Loop

```python
while True:
    screen.update()
    ball.move()

    # Wall collision
    if ball.ycor() > 290 or ball.ycor() < -290:
        ball.dy *= -1

    # Paddle collision
    # (Include paddle collision logic here)

    # Score update
    # (Include scoring logic here)

    update_score()
```

- Continuous loop keeps game **running and responsive**  

---

## 9. Optional Enhancements

- Add **increasing ball speed** after each hit  
- Include **sound effects** when ball hits paddle or wall  
- Add **start/restart menu**  
- Track **high score**  

---

## 10. Key Takeaways

- Pong teaches:
  - **Animation and real-time movement**  
  - **Collision detection using coordinates**  
  - **Keyboard input handling**  
  - **OOP for organizing paddles and ball**  
  - **Score tracking and game loop logic**  
- This project is an **excellent introduction to arcade game development** in Python  

Pong combines **graphics, interaction, and logic** into a fun, playable game.
