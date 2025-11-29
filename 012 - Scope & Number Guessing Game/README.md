# Scope & Number Guessing Game

This lesson covers:
- Understanding **variable scope** in Python  
- Applying scope concepts in a practical project: **Number Guessing Game**  

---

## 1. Understanding Scope in Python

**Scope** determines where a variable can be accessed in your program.

### 1.1 Global Scope

Variables declared **outside functions** have global scope — accessible **anywhere** in the file.

```python
x = 10  # Global variable

def print_x():
    print(x)

print_x()  # Output: 10
```

---

### 1.2 Local Scope

Variables declared **inside a function** can only be used **inside that function**.

```python
def my_function():
    y = 5  # Local variable
    print(y)

my_function()  # Output: 5
# print(y) -> Error: y is not defined
```

---

### 1.3 Global Keyword

You can modify a global variable inside a function using `global`:

```python
count = 0

def increment():
    global count
    count += 1

increment()
print(count)  # Output: 1
```

---

## 2. Number Guessing Game

A beginner-friendly project to practice:
- Loops  
- Conditionals  
- Randomisation  
- Scope concepts  

---

### 2.1 Import Random Module

```python
import random
```

---

### 2.2 Set Up Game Variables

```python
# Global scope
attempts = 0
number_to_guess = random.randint(1, 100)
```

---

### 2.3 Create Guessing Function

```python
def guess_number():
    global attempts
    guess = int(input("Guess a number between 1 and 100: "))
    attempts += 1
    
    if guess > number_to_guess:
        print("Too high.")
        return False
    elif guess < number_to_guess:
        print("Too low.")
        return False
    else:
        print(f"Correct! You guessed the number in {attempts} attempts.")
        return True
```

---

### 2.4 Main Game Loop

```python
game_over = False

while not game_over:
    game_over = guess_number()
```

---

## 3. Example Run

```
Guess a number between 1 and 100: 50
Too low.
Guess a number between 1 and 100: 75
Too high.
Guess a number between 1 and 100: 63
Correct! You guessed the number in 3 attempts.
```

---

## 4. Key Takeaways

1. **Variable Scope**
   - Global → accessible everywhere  
   - Local → accessible only inside function  
   - Use `global` carefully  

2. **Game Logic**
   - Random number generation: `random.randint()`  
   - Loop until user guesses correctly  
   - Track attempts using a global or enclosed variable  

3. **Functions**
   - Keep logic modular  
   - Can return True/False to control loops  

---

### Optional Enhancements

- Add difficulty levels (easy, medium, hard)  
- Limit the number of attempts  
- Give hints based on the distance to the number  
- Ask the player if they want to play again  

The Number Guessing Game is a **fun way to understand scope and build interactive Python programs**.


# scope-and-number-guessing-game

- [Text to ASCII Art Generator](https://patorjk.com/software/taag/)
- [Python Tutor: Visualize Code and Get AI Help for Python, JavaScript, C, C++, and Java](https://pythontutor.com/visualize.html#mode=edit)

#### namespaces-and-scope
```python
enemies = 1


def increase_enemies():
    enemies = 2
    print(f"enemies inside function: {enemies}")


increase_enemies()
print(f"enemies outside function: {enemies}")


# Local Scope
def drink_potion():
    potion_strength = 2
    print(potion_strength)


drink_potion()
# Can't access this potion_strength outside of its scope
# print(potion_strength)

# Global Scope
player_health = 10


def game():
    def drink_potion():
        potion_strength = 2
        print(player_health)

    drink_potion()


print(player_health)
```

#### block-scope
```python
game_level = 10
enemies = ["Skeleton", "Zombie", "Alien"]


def create_enemy():
    new_enemy = ""
    if game_level < 5:
        new_enemy = enemies[0]

    print(new_enemy)
```

#### global-vars
```python
# Modifying Global Scope

enemies = 1

# def increase_enemies():
#     global enemies
#     enemies += 1
#     print(f"enemies inside function: {enemies}")


def increase_enemies(enemy):
    print(f"enemies inside function: {enemy}")
    return enemy + 1


enemies = increase_enemies(enemies)
print(f"enemies outside function: {enemies}")
```

#### global-constants
```python
from random import randint
from art import logo


EASY_LEVEL_TURNS = 10
HARD_LEVEL_TURNS = 5


# Function to check users' guess against actual answer
def check_answer(user_guess, actual_answer, turns):
    """Checks answer against guess, returns the number of turns remaining."""
    if user_guess > actual_answer:
        print("Too high.")
        return turns - 1
    elif user_guess < actual_answer:
        print("Too low.")
        return turns - 1
    else:
        print(f"You got it! The answer was {actual_answer}")


# Function to set difficulty
def set_difficulty():
    level = input("Choose a difficulty. Type 'easy' or 'hard': ")
    if level == "easy":
        return EASY_LEVEL_TURNS
    else:
        return HARD_LEVEL_TURNS


def game():
    print(logo)
    # Choosing a random number between 1 and 100.
    print("Welcome to the Number Guessing Game!")
    print("I'm thinking of a number between 1 and 100.")
    answer = randint(1, 100)
    print(f"Pssst, the correct answer is {answer}")

    turns = set_difficulty()

    # Repeat the guessing functionality if they get it wrong.
    guess = 0
    while guess != answer:
        print(f"You have {turns} attempts remaining to guess the number.")
        # Let the user guess a number
        guess = int(input("Make a guess: "))
        # Track the number of turns and reduce by 1 if they get it wrong
        turns = check_answer(guess, answer, turns)
        if turns == 0:
            print("You've run out of guesses, you lose.")
            return
        elif guess != answer:
            print("Guess again.")




game()
```
#### number-guessing-project

art.py
```python
logo = r"""
  / _ \_   _  ___  ___ ___  /__   \ |__   ___    /\ \ \_   _ _ __ ___ | |__   ___ _ __ 
 / /_\/ | | |/ _ \/ __/ __|   / /\/ '_ \ / _ \  /  \/ / | | | '_ ` _ \| '_ \ / _ \ '__|
/ /_\\| |_| |  __/\__ \__ \  / /  | | | |  __/ / /\  /| |_| | | | | | | |_) |  __/ |   
\____/ \__,_|\___||___/___/  \/   |_| |_|\___| \_\ \/  \__,_|_| |_| |_|_.__/ \___|_| 
"""
```
main.py
```python
from random import randint
from art import logo


EASY_LEVEL_TURNS = 10
HARD_LEVEL_TURNS = 5


# Function to check users' guess against actual answer
def check_answer(user_guess, actual_answer, turns):
    """Checks answer against guess, returns the number of turns remaining."""
    if user_guess > actual_answer:
        print("Too high.")
        return turns - 1
    elif user_guess < actual_answer:
        print("Too low.")
        return turns - 1
    else:
        print(f"You got it! The answer was {actual_answer}")


# Function to set difficulty
def set_difficulty():
    level = input("Choose a difficulty. Type 'easy' or 'hard': ")
    if level == "easy":
        return EASY_LEVEL_TURNS
    else:
        return HARD_LEVEL_TURNS


def game():
    print(logo)
    # Choosing a random number between 1 and 100.
    print("Welcome to the Number Guessing Game!")
    print("I'm thinking of a number between 1 and 100.")
    answer = randint(1, 100)
    print(f"Pssst, the correct answer is {answer}")

    turns = set_difficulty()

    # Repeat the guessing functionality if they get it wrong.
    guess = 0
    while guess != answer:
        print(f"You have {turns} attempts remaining to guess the number.")
        # Let the user guess a number
        guess = int(input("Make a guess: "))
        # Track the number of turns and reduce by 1 if they get it wrong
        turns = check_answer(guess, answer, turns)
        if turns == 0:
            print("You've run out of guesses, you lose.")
            return
        elif guess != answer:
            print("Guess again.")




game()
```

