## Plus or Minus

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

Mix it up! For each problem, the computer flips a coin to decide if it is an adding problem or a subtracting problem.

Here is a sample run:

```
Khansole Academy
What is 84 - 25?
Your answer: 59
Correct!
You've gotten 1 correct in a row.

What is 37 + 52?
Your answer: 89
Correct!
You've gotten 2 correct in a row.
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

#### What Changed?

To mix addition and subtraction, use randint(0, 1) to flip a virtual coin. If it returns 0, ask an addition question; if it returns 1, ask a subtraction question.

* **Coin flip:** `operation = randint(0, 1)` randomly chooses addition or subtraction.
* **Conditional:** `if operation == 0` displays an addition problem; otherwise, it displays subtraction.
* **Answer calculation:** The program calculates the correct answer using either `num1 + num2` or `num1 - num2.`
* **Everything else stays the same:** The player still needs three correct answers in a row, and an incorrect answer resets the streak.

---

#### Answer

```python
from random import randint

def main():
    print("Khansole Academy")

    correct_in_a_row = 0

    while correct_in_a_row < 3:
        # Generate two random numbers
        num1 = randint(10, 99)
        num2 = randint(10, 99)

        # Flip a coin to pick adding or subtracting
        if randint(1, 2) == 1:
            sign = "+"
            true_ans = num1 + num2
        else:
            sign = "-"
            true_ans = num1 - num2

        # Prompt the user with the problem
        print(f"What is {num1} {sign} {num2}?")
        user_ans = int(input("Your answer: "))

        if user_ans == true_ans:
            print("Correct!")
            correct_in_a_row += 1
            print(f"You've gotten {correct_in_a_row} correct in a row.")
        else:
            print("Incorrect.")
            correct_in_a_row = 0
            print(f"The expected answer is {true_ans}")
        print()

    print("Congratulations! You mastered adding and subtracting.")

if __name__ == '__main__':
    main()
```