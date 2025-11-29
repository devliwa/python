# The Blackjack Capstone Project

The **Blackjack Capstone Project** is a comprehensive Python project that combines everything you’ve learned:
- Variables  
- Data types  
- Functions  
- Loops  
- Conditionals  
- Lists  
- Randomisation  

The project simulates the popular card game **Blackjack**, helping you practice building a complete program.

---

## 1. What is Blackjack?

- Goal: Get a hand value **closest to 21** without going over  
- Number cards = face value  
- Face cards (Jack, Queen, King) = 10  
- Ace = 1 or 11  

Players compete against the computer (dealer).

---

## 2. Key Components in the Program

1. **Deck of Cards** → a list of card values  
2. **Player Hand** → a list storing player cards  
3. **Dealer Hand** → a list storing dealer cards  
4. **Random Selection** → using `random.choice()` to draw cards  
5. **Score Calculation** → sum cards, handle Ace as 1 or 11  
6. **Game Loop** → continue until player stands or busts  
7. **Winner Determination** → compare player and dealer scores  

---

## 3. Example Setup: Cards and Hands

```python
import random

cards = [2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10, 11]  # 10 = J, Q, K, 11 = Ace

player_hand = []
dealer_hand = []

# Draw two cards for player
for _ in range(2):
    player_hand.append(random.choice(cards))

# Draw two cards for dealer
for _ in range(2):
    dealer_hand.append(random.choice(cards))

print(f"Your cards: {player_hand}, current score: {sum(player_hand)}")
print(f"Dealer's first card: {dealer_hand[0]}")
```

---

## 4. Handling the Ace (1 or 11)

```python
def calculate_score(hand):
    """Return the score. Adjust for Aces if score > 21."""
    score = sum(hand)
    if 11 in hand and score > 21:
        hand[hand.index(11)] = 1
        score = sum(hand)
    return score
```

---

## 5. Player’s Turn

- Player can **hit** (draw another card) or **stand**  
- Loop continues until player stands or busts  

```python
while True:
    player_score = calculate_score(player_hand)
    print(f"Your hand: {player_hand}, score: {player_score}")
    
    if player_score > 21:
        print("You went over. You lose!")
        break
    
    action = input("Type 'hit' to get another card, 'stand' to pass: ")
    if action == "hit":
        player_hand.append(random.choice(cards))
    else:
        break
```

---

## 6. Dealer’s Turn

- Dealer must **hit until score ≥ 17**  

```python
dealer_score = calculate_score(dealer_hand)
while dealer_score < 17:
    dealer_hand.append(random.choice(cards))
    dealer_score = calculate_score(dealer_hand)
```

---

## 7. Determine the Winner

```python
player_score = calculate_score(player_hand)
dealer_score = calculate_score(dealer_hand)

print(f"Your final hand: {player_hand}, final score: {player_score}")
print(f"Dealer's final hand: {dealer_hand}, final score: {dealer_score}")

if player_score > 21:
    print("You went over. Dealer wins!")
elif dealer_score > 21 or player_score > dealer_score:
    print("You win!")
elif player_score < dealer_score:
    print("Dealer wins!")
else:
    print("Draw!")
```

---

## 8. Tips for the Capstone Project

- Use **functions** for repeated tasks:
  - `deal_card()` → draw a card  
  - `calculate_score()` → sum hand, handle Ace  
  - `compare()` → determine winner  
- Use **loops** for the game flow  
- Keep the **UI simple**: display hands and scores clearly  
- Test **edge cases**, like multiple Aces or ties  

---

## 9. What You’ll Learn

- Full program structure in Python  
- Combining **all learned skills** into a complete project  
- Handling **user input and game logic**  
- Working with **lists, functions, loops, and conditionals** together  

The Blackjack Capstone Project is a **fun and practical way to solidify your Python skills**.

---

If you want, I can create a **full “Beginner Python Project Review Series” Markdown** combining:  
- Hangman  
- Caesar Cipher  
- Secret Auction  
- Blackjack Capstone  

Do you want me to do that?

# blackjack-capstone-basic-project

- [built-in-functions](https://docs.python.org/3/library/functions.html#sum)
- [list-methods](https://developers.google.com/edu/python/lists#list-methods)

art.py
```python
logo = r"""
.------.            _     _            _    _            _    
|A_  _ |.          | |   | |          | |  (_)          | |   
|( \/ ).-----.     | |__ | | __ _  ___| | ___  __ _  ___| | __
| \  /|K /\  |     | '_ \| |/ _` |/ __| |/ / |/ _` |/ __| |/ /
|  \/ | /  \ |     | |_) | | (_| | (__|   <| | (_| | (__|   < 
`-----| \  / |     |_.__/|_|\__,_|\___|_|\_\ |\__,_|\___|_|\_\\
      |  \/ K|                            _/ |                
      `------'                           |__/           
"""
```

main.py
```python
import random
from art import logo


def deal_card():
    """Returns a random card from the deck"""
    cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
    card = random.choice(cards)
    return card


def calculate_score(cards):
    """Take a list of cards and return the score calculated from the cards"""
    if sum(cards) == 21 and len(cards) == 2:
        return 0

    if 11 in cards and sum(cards) > 21:
        cards.remove(11)
        cards.append(1)

    return sum(cards)


def compare(u_score, c_score):
    """Compares the user score u_score against the computer score c_score."""
    if u_score == c_score:
        return "Draw 🙃"
    elif c_score == 0:
        return "Lose, opponent has Blackjack 😱"
    elif u_score == 0:
        return "Win with a Blackjack 😎"
    elif u_score > 21:
        return "You went over. You lose 😭"
    elif c_score > 21:
        return "Opponent went over. You win 😁"
    elif u_score > c_score:
        return "You win 😃"
    else:
        return "You lose 😤"


def play_game():
    print(logo)
    user_cards = []
    computer_cards = []
    computer_score = -1
    user_score = -1
    is_game_over = False

    for _ in range(2):
        user_cards.append(deal_card())
        computer_cards.append(deal_card())

    while not is_game_over:
        user_score = calculate_score(user_cards)
        computer_score = calculate_score(computer_cards)
        print(f"Your cards: {user_cards}, current score: {user_score}")
        print(f"Computer's first card: {computer_cards[0]}")

        if user_score == 0 or computer_score == 0 or user_score > 21:
            is_game_over = True
        else:
            user_should_deal = input("Type 'y' to get another card, type 'n' to pass: ")
            if user_should_deal == "y":
                user_cards.append(deal_card())
            else:
                is_game_over = True

    while computer_score != 0 and computer_score < 17:
        computer_cards.append(deal_card())
        computer_score = calculate_score(computer_cards)

    print(f"Your final hand: {user_cards}, final score: {user_score}")
    print(f"Computer's final hand: {computer_cards}, final score: {computer_score}")
    print(compare(user_score, computer_score))


while input("Do you want to play a game of Blackjack? Type 'y' or 'n': ") == "y":
    print("\n" * 20)
    play_game()

```

