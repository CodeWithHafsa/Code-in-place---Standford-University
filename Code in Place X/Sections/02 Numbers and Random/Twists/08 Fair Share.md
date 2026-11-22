## Fair Share

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

Time to practice division! Ask division problems where the answer is always a whole number, like 42 / 6. No leftovers allowed!

Here is a sample run:

```
Khansole Academy
What is 42 / 6?
Your answer: 7
Correct!
You've gotten 1 correct in a row.

What is 36 / 4?
Your answer: 8
Incorrect.
The expected answer is 9
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
To turn Khansole Academy into a division trainer, generate a divisor and a whole-number answer first, then multiply them to get the dividend.

* **Generated a divisor:** `num2 = randint(2, 12)` chooses a number to divide by.
* **Generated the correct answer:** `true_ans = randint(2, 12)` chooses a whole-number quotient.
* **Calculated the dividend:** `num1 = num2 * true_ans` ensures `num1 / num2` always divides evenly.
* **Changed the question:** The program displays division using `/`instead of addition using `+`.
* **Updated the final message:** It now says `"You mastered division."`

The program still requires three correct answers in a row, and an incorrect answer resets the streak to zero.

---

#### Answer

```python
from random import randint

def main():
    print("Khansole Academy")

    correct_in_a_row = 0

    while correct_in_a_row < 3:
        # Pick the answer first, then build the problem from it
        num2 = randint(2, 9)
        quotient = randint(2, 12)
        num1 = num2 * quotient

        # Prompt the user with the problem
        print(f"What is {num1} / {num2}?")
        user_ans = int(input("Your answer: "))
        true_ans = quotient

        if user_ans == true_ans:
            print("Correct!")
            correct_in_a_row += 1
            print(f"You've gotten {correct_in_a_row} correct in a row.")
        else:
            print("Incorrect.")
            correct_in_a_row = 0
            print(f"The expected answer is {true_ans}")
        print()

    print("Congratulations! You mastered division.")

if __name__ == '__main__':
    main()
```