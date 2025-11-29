# Local Development Environment Setup & The Coffee Machine

This lesson covers:
- Setting up a **local Python development environment**  
- Building the **Coffee Machine project** to practice Python fundamentals  

---

## 1. Setting Up a Local Python Development Environment

### 1.1 Install Python
- Download Python from [python.org](https://www.python.org/downloads/)  
- Ensure you check **“Add Python to PATH”** during installation  

### 1.2 Install an IDE or Code Editor
- **VS Code** (recommended)  
- **PyCharm**  
- **Thonny** (beginner-friendly)  

### 1.3 Verify Installation
```bash
python --version
```

### 1.4 Running Python Scripts
- Use terminal or IDE:  
```bash
python filename.py
```

---

## 2. The Coffee Machine Project

The Coffee Machine project is a beginner-friendly project that simulates a coffee vending machine.

### Concepts Practiced:
- Variables  
- Conditionals  
- Loops  
- Functions  
- User input  

---

## 3. Coffee Machine Requirements

1. The machine offers **espresso, latte, and cappuccino**  
2. Each drink costs a certain amount  
3. Track **resources** (water, milk, coffee)  
4. Accept **coins** as payment  
5. Check if resources are sufficient before making a drink  
6. Give change if needed  
7. Display a **report** of remaining resources  

---

## 4. Sample Resources and Menu

```python
MENU = {
    "espresso": {"ingredients": {"water": 50, "coffee": 18}, "cost": 1.5},
    "latte": {"ingredients": {"water": 200, "milk": 150, "coffee": 24}, "cost": 2.5},
    "cappuccino": {"ingredients": {"water": 250, "milk": 100, "coffee": 24}, "cost": 3.0}
}

resources = {"water": 300, "milk": 200, "coffee": 100, "money": 0}
```

---

## 5. Checking Resources

```python
def is_resource_sufficient(order_ingredients):
    for item in order_ingredients:
        if order_ingredients[item] > resources[item]:
            print(f"Sorry there is not enough {item}.")
            return False
    return True
```

---

## 6. Processing Coins

```python
def process_coins():
    print("Please insert coins.")
    total = int(input("Quarters: ")) * 0.25
    total += int(input("Dimes: ")) * 0.10
    total += int(input("Nickels: ")) * 0.05
    total += int(input("Pennies: ")) * 0.01
    return total
```

---

## 7. Transaction Check

```python
def is_transaction_successful(money_received, drink_cost):
    if money_received >= drink_cost:
        change = round(money_received - drink_cost, 2)
        print(f"Here is ${change} in change.")
        resources["money"] += drink_cost
        return True
    else:
        print("Sorry, that's not enough money. Money refunded.")
        return False
```

---

## 8. Making Coffee

```python
def make_coffee(drink_name, order_ingredients):
    for item in order_ingredients:
        resources[item] -= order_ingredients[item]
    print(f"Here is your {drink_name} ☕️. Enjoy!")
```

---

## 9. Main Program Loop

```python
is_on = True

while is_on:
    choice = input("What would you like? (espresso/latte/cappuccino): ").lower()
    
    if choice == "off":
        is_on = False
    elif choice == "report":
        for resource, amount in resources.items():
            print(f"{resource}: {amount}")
    else:
        drink = MENU[choice]
        if is_resource_sufficient(drink["ingredients"]):
            payment = process_coins()
            if is_transaction_successful(payment, drink["cost"]):
                make_coffee(choice, drink["ingredients"])
```

---

## 10. Key Takeaways

- **Local environment setup** ensures you can run and test Python scripts  
- **Coffee Machine Project** teaches:
  - Handling **user input**  
  - Using **functions** to organize code  
  - Managing **loops and conditionals**  
  - Tracking **state using dictionaries**  
- Projects like this build **practical programming skills**  

---

Optional Enhancements:
- Add **more drink options**  
- Keep track of **daily sales**  
- Add **error handling** for invalid input  
- Include **refill functionality**  

The Coffee Machine project is a **great capstone for beginners** to combine core Python concepts into a working program.

# local-development-environment-setup-coffee-machine

- [PyCharm keyboard shortcuts](https://www.jetbrains.com/help/pycharm/mastering-keyboard-shortcuts.html?keymap=secondary_windows)
- [emojipedia](https://emojipedia.org/hot-beverage)
- [Use emoji and symbols on Mac](https://support.apple.com/en-gb/guide/mac-help/mchlp1560/mac)

```python
MENU = {
    "espresso": {
        "ingredients": {
            "water": 50,
            "coffee": 18,
        },
        "cost": 1.5,
    },
    "latte": {
        "ingredients": {
            "water": 200,
            "milk": 150,
            "coffee": 24,
        },
        "cost": 2.5,
    },
    "cappuccino": {
        "ingredients": {
            "water": 250,
            "milk": 100,
            "coffee": 24,
        },
        "cost": 3.0,
    }
}

profit = 0
resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
}


def is_resource_sufficient(order_ingredients):
    """Returns True when order can be made, False if ingredients are insufficient."""
    for item in order_ingredients:
        if order_ingredients[item] > resources[item]:
            print(f"Sorry there is not enough {item}.")
            return False
    return True


def process_coins():
    """Returns the total calculated from coins inserted."""
    print("Please insert coins.")
    total = int(input("how many quarters?: ")) * 0.25
    total += int(input("how many dimes?: ")) * 0.1
    total += int(input("how many nickles?: ")) * 0.05
    total += int(input("how many pennies?: ")) * 0.01
    return total


def is_transaction_successful(money_received, drink_cost):
    """Return True when the payment is accepted, or False if money is insufficient."""
    if money_received >= drink_cost:
        change = round(money_received - drink_cost, 2)
        print(f"Here is ${change} in change.")
        global profit
        profit += drink_cost
        return True
    else:
        print("Sorry that's not enough money. Money refunded.")
        return False


def make_coffee(drink_name, order_ingredients):
    """Deduct the required ingredients from the resources."""
    for item in order_ingredients:
        resources[item] -= order_ingredients[item]
    print(f"Here is your {drink_name} ☕️. Enjoy!")


is_on = True

while is_on:
    choice = input("What would you like? (espresso/latte/cappuccino): ")
    if choice == "off":
        is_on = False
    elif choice == "report":
        print(f"Water: {resources['water']}ml")
        print(f"Milk: {resources['milk']}ml")
        print(f"Coffee: {resources['coffee']}g")
        print(f"Money: ${profit}")
    else:
        drink = MENU[choice]
        if is_resource_sufficient(drink["ingredients"]):
            payment = process_coins()
            if is_transaction_successful(payment, drink["cost"]):
                make_coffee(choice, drink["ingredients"])
```

