## Set the Goal

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

Three in a row is a lot of pressure! At the start, ask the player how many correct answers in a row they want to get. Then keep going until they reach their goal.

Here is a sample run:

```
Khansole Academy
How many in a row do you want to get? 2
What is 42 + 17?
Your answer: 59
Correct!
You've gotten 1 correct in a row.

What is 63 + 25?
Your answer: 88
Correct!
You've gotten 2 correct in a row.

Congratulations! You mastered addition.
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

#### What changed?
* Added `goal = int(input("How many in a row do you want to get? "))` to let the player choose their goal.
* Changed `while correct_in_a_row < 3: to while correct_in_a_row < goal:` so the game continues until the player's chosen goal is reached.

The rest of the code stays the same. If the player enters `2`, they need two correct answers in a row. If they get an answer wrong, their streak resets to zero.

### Answer

```python
from random import randint

def main():
    print("Khansole Academy")

    goal = int(input("How many in a row do you want to get? "))
    correct_in_a_row = 0

    while correct_in_a_row < goal:
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

