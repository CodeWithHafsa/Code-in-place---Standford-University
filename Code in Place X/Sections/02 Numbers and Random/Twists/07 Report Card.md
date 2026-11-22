## Report Card

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

When the player finishes, show their report card: how many problems they tried and how many they got right in total.

Here is a sample run:

```
Khansole Academy
What is 51 + 79?
Your answer: 120
Incorrect.
The expected answer is 130

What is 55 + 11?
Your answer: 66
Correct!
You've gotten 1 correct in a row.

What is 84 + 25?
Your answer: 109
Correct!
You've gotten 2 correct in a row.

What is 97 + 20?
Your answer: 117
Correct!
You've gotten 3 correct in a row.

Congratulations! You mastered addition.
You tried 4 problems and got 3 right.
```

### Given Code

```python
from random import randint

def main():
    print("Khansole Academy")

    correct_in_a_row = 0

    while correct_in_a_row < 3:
        # Generate two random numbers
        num1 = randint(10, 99)
        num2 = randint(10, 99)

        # Prompt the user with the problem
        print(f"What is {num1} + {num2}?")
        user_ans = int(input("Your answer: "))
        true_ans = num1 + num2

        if user_ans == true_ans:
            print("Correct!")
            correct_in_a_row += 1
            print(f"You've gotten {correct_in_a_row} correct in a row.")
        else:
            print("Incorrect.")
            correct_in_a_row = 0
            print(f"The expected answer is {true_ans}")
        print()

    print("Congratulations! You mastered addition.")

if __name__ == '__main__':
    main()
```

---
#### What changed?
* `total_problems = 0` counts all questions attempted, whether correct or incorrect.
* `total_correct = 0` counts all correct answers.
* `total_problems += 1` runs after every answer.
* `total_correct += 1` runs only when the answer is correct.
* At the end, the program displays the report card with both totals.

Important: `total_correct `does not reset when the player gets an answer wrong. Only correct_in_a_row resets, because the report card tracks the player's overall performance, not just their current streak.

---

#### Answer

```python
from random import randint

def main():
    print("Khansole Academy")

    correct_in_a_row = 0
    num_problems = 0
    num_correct = 0

    while correct_in_a_row < 3:
        # Generate two random numbers
        num1 = randint(10, 99)
        num2 = randint(10, 99)

        # Prompt the user with the problem
        print(f"What is {num1} + {num2}?")
        user_ans = int(input("Your answer: "))
        true_ans = num1 + num2
        num_problems += 1

        if user_ans == true_ans:
            print("Correct!")
            correct_in_a_row += 1
            num_correct += 1
            print(f"You've gotten {correct_in_a_row} correct in a row.")
        else:
            print("Incorrect.")
            correct_in_a_row = 0
            print(f"The expected answer is {true_ans}")
        print()

    print("Congratulations! You mastered addition.")

    # Show how the whole practice went
    print(f"You tried {num_problems} problems and got {num_correct} right.")

if __name__ == '__main__':
    main()
```