## Level Up

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

Start easy and get harder! The first problem uses numbers up to 10. Each correct answer allows bigger numbers: up to 100, then up to 1000. A wrong answer goes back to numbers up to 10.

Here is a sample run:

```
Khansole Academy
What is 4 + 7?
Your answer: 11
Correct!
You've gotten 1 correct in a row.

What is 52 + 38?
Your answer: 90
Correct!
You've gotten 2 correct in a row.

What is 640 + 215?
Your answer: 855
Correct!
You've gotten 3 correct in a row.

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

---

#### What changed?

To make the problems harder after each correct answer, use a variable called max_num to control the largest random number. Start at 10, increase it to 100 and then 1000 after correct answers, and reset it to 10 after a wrong answer.

* `max_num = 10` starts the game with small numbers.
* `randint(1, max_num)` generates numbers from 1 up to the current maximum.
* `max_num *= 10` makes the next problem harder after a correct answer: 10 → 100 → 1,000.
* `max_num = 10` resets the difficulty after a wrong answer, along with the correct-answer streak.

----


#### Answer

```python
from random import randint

def main():
    print("Khansole Academy")

    correct_in_a_row = 0
    biggest = 10

    while correct_in_a_row < 3:
        # Generate two random numbers
        num1 = randint(1, biggest)
        num2 = randint(1, biggest)

        # Prompt the user with the problem
        print(f"What is {num1} + {num2}?")
        user_ans = int(input("Your answer: "))
        true_ans = num1 + num2

        if user_ans == true_ans:
            print("Correct!")
            correct_in_a_row += 1
            biggest = biggest * 10
            print(f"You've gotten {correct_in_a_row} correct in a row.")
        else:
            print("Incorrect.")
            correct_in_a_row = 0
            biggest = 10
            print(f"The expected answer is {true_ans}")
        print()

    print("Congratulations! You mastered addition.")

if __name__ == '__main__':
    main()
```