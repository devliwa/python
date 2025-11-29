# The Turtle Crossing Capstone Project in Python

This capstone project combines everything learned about **Turtle graphics, OOP, and game logic**.

---

## 1. Project Overview

- Inspired by **classic Frogger game**  
- Player controls a **turtle** crossing a busy road  
- Objective: Reach the **finish line without colliding** with moving cars  
- Implements **levels, increasing difficulty, and scoring**  

---

## 2. Setting Up the Screen

```python
import turtle

screen = turtle.Screen()
screen.title("Turtle Crossing")
screen.bgcolor("white")
screen.setup(width=600, height=600)
screen.tracer(0)
```

- `tracer(0)` allows **smooth manual animation updates**  

---

## 3. Creating the Player (Turtle)

```python
class Player(turtle.Turtle):
    def __init__(self):
        super().__init__()
        self.shape("turtle")
        self.penup()
        self.goto(0, -250)
        self.setheading(90)

    def move_up(self):
        self.forward(20)

    def move_down(self):
        self.backward(20)
```

- Player starts at **bottom center**  
- Moves **upwards towards finish line**  
- Use keyboard to control movement  

```python
player = Player()
screen.listen()
screen.onkey(player.move_up, "Up")
screen.onkey(player.move_down, "Down")
```

---

## 4. Creating Cars

```python
import random

class Car(turtle.Turtle):
    def __init__(self):
        super().__init__()
        self.shape("square")
        self.shapesize(stretch_wid=1, stretch_len=2)
        self.penup()
        self.color(random.choice(["red", "blue", "green", "yellow"]))
        self.goto(300, random.randint(-250, 250))
        self.speed = random.randint(5, 15)

    def move(self):
        self.backward(self.speed)
```

- Cars spawn **on the right side** and move **left**  
- Random colors, positions, and speeds increase challenge  

---

## 5. Managing Multiple Cars

```python
cars = []

def create_cars():
    if random.randint(1, 6) == 1:  # Control frequency of cars
        new_car = Car()
        cars.append(new_car)

def move_cars():
    for car in cars:
        car.move()
```

- New cars appear randomly  
- Each frame, all cars **update their position**  

---

## 6. Collision Detection

```python
def check_collision():
    for car in cars:
        if player.distance(car) < 20:
            return True
    return False
```

- If player is **too close to a car**, game ends  

---

## 7. Leveling and Score

```python
level = 1
def level_up():
    global level
    level += 1
    print(f"Level {level}")
    # Optional: Increase car speed for higher difficulty
```

- Reaching top of the screen increases **level**  
- Can **increase game difficulty** progressively  

---

## 8. Main Game Loop

```python
import time

game_on = True

while game_on:
    screen.update()
    create_cars()
    move_cars()

    if check_collision():
        game_on = False
        print("Game Over!")

    if player.ycor() > 280:
        player.goto(0, -250)
        level_up()

    time.sleep(0.1)
```

- Continuous loop **updates screen, moves cars, and checks collisions**  

---

## 9. Optional Enhancements

- Add **scoreboard** showing levels or points  
- Add **lives** for multiple attempts  
- Include **different lanes with varying car speeds**  
- Add **sound effects** on collision or level up  
- Add **special power-ups** for the player  

---

## 10. Key Takeaways

- Capstone project combines:
  - **OOP** for player and car objects  
  - **Turtle graphics** for animation  
  - **Collision detection** using coordinates  
  - **Level progression and game difficulty**  
- Excellent project for practicing **all prior concepts** in a **complete, playable game**  

The Turtle Crossing project demonstrates **real-world game design** with **Python programming, graphics, and OOP principles**.
