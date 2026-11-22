## Too Generous

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

Khansole Academy is supposed to wait for 3 correct answers in a row. But it seems to be counting wrong. Find the bug and fix it!

Here is what happens now:

```
Khansole Academy
What is 55 + 11?
Your answer: 66
Correct!
You've gotten 1 correct in a row.

What is 51 + 79?
Your answer: 120
Incorrect.
The expected answer is 130

What is 84 + 25?
Your answer: 109
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
            print(f"The expected answer is {true_ans}")
        print()

    print("Congratulations! You mastered addition.")

if __name__ == '__main__':
    main()
```

---

#### What changed?

The bug is that when the user answers incorrectly, correct_in_a_row is not reset to zero. Add `correct_in_a_row = 0` inside the `else` block

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