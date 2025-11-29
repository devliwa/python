# The Quiz Project & the Benefits of OOP

This lesson combines **Object-Oriented Programming (OOP)** concepts with a practical project: building a **Quiz Game** in Python.

---

## 1. The Quiz Project Overview

The **Quiz Project** teaches:
- How to **structure code using classes**  
- How to use **methods and attributes**  
- How to **interact with users**  
- Benefits of **OOP in organizing programs**

### Project Idea:
- The program asks multiple-choice questions  
- Each question has a **text**, **answer options**, and a **correct answer**  
- Keep track of the **score**  
- Use **OOP** to manage questions and the quiz flow  

---

## 2. Creating the Question Class

```python
class Question:
    def __init__(self, text, options, answer):
        self.text = text
        self.options = options
        self.answer = answer

    def is_correct(self, guess):
        return guess.lower() == self.answer.lower()
```

- `text` → question text  
- `options` → list of answer choices  
- `answer` → correct answer  
- `is_correct()` → method to check if the player’s guess is correct  

---

## 3. Creating the Quiz Class

```python
class Quiz:
    def __init__(self, questions):
        self.questions = questions
        self.score = 0
        self.question_number = 0

    def next_question(self):
        if self.question_number < len(self.questions):
            current_question = self.questions[self.question_number]
            print(f"Q{self.question_number + 1}: {current_question.text}")
            for option in current_question.options:
                print(option)
            guess = input("Your answer: ")
            self.check_answer(guess, current_question)
            self.question_number += 1
        else:
            self.show_score()

    def check_answer(self, guess, question):
        if question.is_correct(guess):
            print("Correct!")
            self.score += 1
        else:
            print(f"Wrong! The correct answer is {question.answer}.")

    def show_score(self):
        print(f"Your final score is: {self.score}/{len(self.questions)}")
```

---

## 4. Running the Quiz

```python
q1 = Question("What is the capital of France?", ["A. Paris", "B. London", "C. Rome"], "A")
q2 = Question("What is 5 + 7?", ["A. 10", "B. 12", "C. 14"], "B")

questions = [q1, q2]
quiz = Quiz(questions)

while quiz.question_number < len(questions):
    quiz.next_question()
```

---

## 5. Benefits of Using OOP for the Quiz Project

1. **Organized Code**  
   - Each class handles its own responsibility  

2. **Reusability**  
   - `Question` class can be used in multiple quizzes  
   - `Quiz` class can handle any set of questions  

3. **Modular and Scalable**  
   - Adding new features (e.g., timed quiz, high score tracking) is easier  

4. **Encapsulation**  
   - Keeps **question data and quiz logic** separate  
   - Reduces risk of accidental changes  

5. **Maintainability**  
   - Easier to debug and update compared to procedural code  

---

## 6. Optional Enhancements

- Add **categories** for questions  
- Allow **multiple quizzes** in one session  
- Include **user feedback** for each question  
- Track **high scores** in a file or database  

---

## 7. Key Takeaways

- OOP allows building **real-world projects** like a Quiz Game  
- Classes help organize **data and logic together**  
- Methods allow **interactions with objects**  
- Projects like this show the **practical benefits of OOP** in building modular, reusable, and maintainable programs  

The Quiz Project is a **perfect beginner-to-intermediate capstone** for practicing OOP in Python.
