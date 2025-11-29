# Dictionaries, Nesting & The Secret Auction

This lesson covers:
- How Python dictionaries work  
- How to nest lists and dictionaries  
- How these concepts come together to build the **Secret Auction** project  

---

# 1. Python Dictionaries

A **dictionary** stores data in **key–value pairs**.

### Basic Syntax

```python
student = {
    "name": "Charles",
    "score": 95
}
```

### Accessing Values

```python
print(student["name"])   # Charles
```

---

## 1.1 Adding New Key–Value Pairs

```python
student["age"] = 17
```

---

## 1.2 Editing Existing Values

```python
student["score"] = 98
```

---

## 1.3 Looping Through a Dictionary

```python
for key in student:
    print(key, ":", student[key])
```

---

# 2. Nesting in Python

Nesting = putting **lists inside dictionaries**, **dictionaries inside lists**, or **dictionaries inside dictionaries**.

---

## 2.1 Nesting a List in a Dictionary

```python
programming_languages = {
    "python": ["easy", "popular", "beginner-friendly"]
}
```

---

## 2.2 Nesting a Dictionary in a Dictionary

```python
travel_log = {
    "France": {"cities_visited": ["Paris", "Nice"], "visits": 2},
    "Japan": {"cities_visited": ["Tokyo", "Osaka"], "visits": 3}
}
```

---

## 2.3 Nesting Dictionaries Inside a List

```python
travel_log = [
    {
        "country": "France",
        "cities": ["Paris", "Nice"],
        "visits": 2
    },
    {
        "country": "Japan",
        "cities": ["Tokyo", "Osaka"],
        "visits": 3
    }
]
```

---

# 3. The Secret Auction Project

The **Secret Auction** is a classic beginner Python project that teaches:
- Dictionaries  
- Loops  
- Nesting  
- Functions  
- Input handling  

The goal:  
Each bidder enters their **name** and **bid amount** secretly.  
The program stores all bids and finds the **highest bidder**.

---

# 4. Step-by-Step Logic

### 1. Create an empty dictionary to store bids

```python
bids = {}
```

### 2. Ask for name and bid

```python
name = input("What is your name?: ")
price = int(input("What is your bid?: $"))
bids[name] = price
```

### 3. Ask if there are more bidders

```python
should_continue = input("Are there any other bidders? Type 'yes' or 'no': ")
```

If "yes" → continue the loop  
If "no" → stop and determine the winner

---

# 5. Finding the Highest Bidder

```python
def find_highest_bidder(bidding_record):
    highest_bid = 0
    winner = ""
    for bidder in bidding_record:
        bid_amount = bidding_record[bidder]
        if bid_amount > highest_bid:
            highest_bid = bid_amount
            winner = bidder
    print(f"The winner is {winner} with a bid of ${highest_bid}.")
```

---

# 6. Full Secret Auction Program (Simple Version)

```python
bids = {}
bidding_finished = False

def find_highest_bidder(bidding_record):
    highest_bid = 0
    winner = ""
    for bidder in bidding_record:
        bid_amount = bidding_record[bidder]
        if bid_amount > highest_bid:
            highest_bid = bid_amount
            winner = bidder
    print(f"The winner is {winner} with a bid of ${highest_bid}.")

while not bidding_finished:
    name = input("What is your name?: ")
    price = int(input("What is your bid?: $"))
    bids[name] = price

    should_continue = input("Any other bidders? Type 'yes' or 'no': ")
    if should_continue == "no":
        bidding_finished = True
        find_highest_bidder(bids)
```

---

# 7. What You Should Understand

After this lesson, you should know:
- How dictionaries store and retrieve data  
- How to nest lists and dictionaries  
- How loops and functions work together  
- How to build a real mini-project using dictionaries  

---

If you want, I can also create:
✅ A Secret Auction **flowchart**  
✅ A **step-by-step worksheet**  
✅ An advanced version with **tie-breaking rules**  


# dictionaries-nesting-and-secret-auction

#### dictionaries
```python
# Creating a dictionary
programming_dictionary = {
    "Bug": "An error in a program that prevents the program from running as expected.",
    "Function": "A piece of code that you can easily call over and over again.",
}

# Retrieving a value from a dictionary
print(programming_dictionary["Function"])

# Adding more items to a dictionary
programming_dictionary["Loop"] = "The action of doing something over and over again."

# Creating an empty dictionary
empty_dictionary = {}

# Wipe an existing dictionary
# programming_dictionary = {}
# print(programming_dictionary)

# Edit an item in a dictionary
programming_dictionary["Bug"] = "A moth in your computer."
# print(programming_dictionary)

# Loop through a dictionary
for key in programming_dictionary:
    print(key)
    print(programming_dictionary[key])
```
#### nested-lists-and-dictionaries
```python
capitals = {
    "France": "Paris",
    "Germany": "Berlin",
}

# Nested List in Dictionary

# travel_log = {
#     "France": ["Paris", "Lille", "Dijon"],
#     "Germany": ["Stuttgart", "Berlin"],
# }

# print Lille
# print(travel_log["France"][1])

nested_list = ["A", "B", ["C", "D"]]
# print(nested_list[2][1])

# Nested dictionary in a dictionary
travel_log = {
  "France": {
    "cities_visited": ["Paris", "Lille", "Dijon"],
    "total_visits": 12
   },
  "Germany": {
    "cities_visited": ["Berlin", "Hamburg", "Stuttgart"],
    "total_visits": 5
   },
}

print(travel_log["Germany"]["cities_visited"][2])
```
#### blind-auction-project
art.py
```python
logo = r'''
                         ___________
                         \         /
                          )_______(
                          |"""""""|_.-._,.---------.,_.-._
                          |       | | |               | | ''-.
                          |       |_| |_             _| |_..-'
                          |_______| '-' `'---------'` '-'
                          )"""""""(
                         /_________\\
                       .-------------.
                      /_______________\\
'''
```
main.py
```python
from art import logo
print(logo)


def find_highest_bidder(bidding_record):
    highest_bid = 0
    winner = ""
    for bidder in bidding_record:
        bid_amount = bidding_record[bidder]
        if bid_amount > highest_bid:
            highest_bid = bid_amount
            winner = bidder
    print(f"The winner is {winner} with a bid of ${highest_bid}")


bids = {}
continue_bidding = True
while continue_bidding:
    name = input("What is your name?: ")
    price = int(input("What is your bid?: $"))
    bids[name] = price
    should_continue = input("Are there any other bidders? Type 'yes or 'no'.\n")
    if should_continue == "no":
        continue_bidding = False
        find_highest_bidder(bids)
    elif should_continue == "yes":
        print("\n" * 20)
```

