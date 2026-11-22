## Three's a Crowd

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

Two numbers is too easy. Add a third number to every problem!

Here is a sample run:

```
Khansole Academy
What is 23 + 45 + 17?
Your answer: 85
Correct!
You've gotten 1 correct in a row.
```

### Given Code

```
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
* Added `num3 = randint(10, 99)` to generate a third random number.
* Updated the question to display all three numbers.
* Updated `true_ans` to calculate the sum of all three numbers.

Everything else stays the same: the user must answer three problems correctly in a row to win, and an incorrect answer resets the streak to zero.

---


### Answer

```python
from random import randint

def main():
    print("Khansole Academy")

    correct_in_a_row = 0

    while correct_in_a_row < 3:
        # Generate three random numbers
        num1 = randint(10, 99)
        num2 = randint(10, 99)
        num3 = randint(10, 99)

        # Prompt the user with the problem
        print(f"What is {num1} + {num2} + {num3}?")
        user_ans = int(input("Your answer: "))
        true_ans = num1 + num2 + num3

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
