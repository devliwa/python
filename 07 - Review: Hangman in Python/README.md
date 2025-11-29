# Review: Hangman in Python

Hangman is a classic Python beginner project that teaches:
- Randomisation  
- Lists  
- Loops  
- Conditionals  
- Functions  
- String manipulation  

This review breaks down the logic behind building the game.

---

## 1. What Hangman Teaches You

Before writing code, Hangman helps practice key Python concepts:

| Concept | How Hangman Uses It |
|--------|----------------------|
| Randomisation | Picking a random word from a list |
| Lists | Storing letters of the word and guesses |
| Loops | Repeating gameplay until the player wins or loses |
| Conditionals | Checking correct/incorrect guesses |
| Functions | Organizing code into reusable blocks |
| Strings | Comparing letters and building the output display |

---

## 2. Basic Structure of Hangman

A simple Hangman game involves:

1. **Choosing a random word**
2. **Creating a display** (e.g., `_ _ _ _`)
3. **Tracking correct & wrong guesses**
4. **Looping until:**
   - The word is fully guessed (player wins), OR  
   - The player runs out of lives (player loses)
5. **Ending the game with a message**

---

## 3. Key Components Explained

### 1. Random Word Selection

```python
import random

words = ["python", "hangman", "coding", "banana"]
chosen_word = random.choice(words)
```

---

### 2. Create the Display

```python
display = ["_" for _ in chosen_word]
print(" ".join(display))
```

---

### 3. Main Game Loop

```python
lives = 6
guessed_letters = []

while lives > 0 and "_" in display:
    guess = input("Guess a letter: ").lower()
    
    if guess in guessed_letters:
        print("You've already guessed that!")
        continue

    guessed_letters.append(guess)

    if guess in chosen_word:
        for i, letter in enumerate(chosen_word):
            if letter == guess:
                display[i] = guess
        print("Correct:", " ".join(display))
    else:
        lives -= 1
        print(f"Wrong! Lives left: {lives}")
```

---

### 4. Win or Lose

```python
if "_" not in display:
    print("You win!")
else:
    print("Game over! The word was:", chosen_word)
```

---

## 4. Hangman ASCII Stages (Optional)

A list is often used to show the hangman drawing:

```python
stages = [
    "  +---+\n  |   |\n      |\n      |\n      |\n      |\n=========",
    "  +---+\n  |   |\n  O   |\n      |\n      |\n      |\n=========",
    "  +---+\n  |   |\n  O   |\n  |   |\n      |\n      |\n=========",
    ...
]
```

Shows a new stage every time the player loses a life.

---

## 5. Final Clean Version (Simplified)

```python
import random

words = ["python", "hangman", "coding", "banana"]
chosen_word = random.choice(words)

display = ["_" for _ in chosen_word]
guessed = []
lives = 6

print("HANGMAN GAME")
print(" ".join(display))

while lives > 0 and "_" in display:
    guess = input("Guess a letter: ").lower()

    if guess in guessed:
        print("Already guessed!")
        continue

    guessed.append(guess)

    if guess in chosen_word:
        for i, letter in enumerate(chosen_word):
            if letter == guess:
                display[i] = guess
        print("Correct:", " ".join(display))
    else:
        lives -= 1
        print(f"Wrong guess! Lives left: {lives}")

if "_" not in display:
    print("You win!")
else:
    print("Game over! The word was:", chosen_word)
```

---

## 6. What You Should Understand After Reviewing Hangman

- How to **track game state**  
- How to **process user input** safely  
- How to **update a list based on conditions**  
- How to **organize logic inside loops**  
- How randomisation affects gameplay  

Hangman is one of the best beginner projects because it uses **almost every fundamental Python skill** in one program.