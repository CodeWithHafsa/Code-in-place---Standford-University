## Story Time

*A twist on Khansole Academy from your section. Try it yourself, then compare your code with the solution.*

Plain math problems are a little boring. Ask GPT to turn each problem into a one-sentence story, and show the story in place of "What is ...?".

Here is a sample run:

```
Khansole Academy
Maya has 23 stickers and her friend gives her 45 more. How many stickers does Maya have now?
Your answer: 68
Correct!
You've gotten 1 correct in a row.
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
* Imported GPT: Added `from ai import call_gpt` to allow the program to ask GPT to generate a story problem.
* Created a prompt: Added:

```python
prompt = f"Write a one-sentence word problem that asks the reader to add {num1} and {num2}. Do not give the answer."
```
* Generated the story: Added:

```python
story = call_gpt(prompt)
```
* Displayed the story: Replaced the regular math question with

---

#### Answer

```python
from random import randint
from ai import call_gpt

def main():
    print("Khansole Academy")

    correct_in_a_row = 0

    while correct_in_a_row < 3:
        # Generate two random numbers
        num1 = randint(10, 99)
        num2 = randint(10, 99)

        # Ask GPT to turn the problem into a story
        prompt = f"Write a one-sentence word problem that asks the reader to add {num1} and {num2}. Do not give the answer."
        story = call_gpt(prompt)

        # Prompt the user with the problem
        print(story)
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