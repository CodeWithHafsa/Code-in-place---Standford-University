## Assignment
In Code in Place we are all about building technology to help folks learn. Now it is your turn. Implement Khansole Academy—a program that helps other people learn addition! Write a program that randomly generates a simple addition problem for the user, reads in the answer from the user, and then checks to see if they got it right or wrong.

More specifically, your program should be able to generate simple addition problems that involve adding two 2-digit integers (i.e., the numbers 10 through 99). The user should be asked for an answer to the generated problem. Your program should determine if the answer was correct or not, and give the user an appropriate message to let them know.

A sample run of the program is shown below (user input is in blue for visual clarity):

>> Khansole Academy \
What is 51 + 79? \
Your answer: 120 \
Incorrect. \
The expected answer is 130

Here's another sample run, where the user gets the question correct (user input is in blue):

>> Khansole Academy \
What is 55 + 11? \
Your answer: 66 \
Correct!

When you have decided that your program works as intended, hit Check Correct.

## Optional Extension
Note: To avoid the assignment being marked incorrect because you did an extension, leave the base assignment solution in this project. To do your extension, make your own project under `"Code > Your Own"`. If you get something cool working, share it on the forum!!


If you're up for it, we can make Khansole Academy an even better learning tool. Be creative! We recommend you start with the "three in a row" extension first, then come up with your own.

```python
import random

def main():
    print("Khansole Academy")
    # TODO: your code here
    
    
if __name__ == '__main__':
    main()
```

## Answer

```python
import random

def main():
    print("Khansole Academy")

    # Generate two random 2-digit integers
    num1 = random.randint(10, 99)
    num2 = random.randint(10, 99)

    # Ask the question
    print(f"What is {num1} + {num2}?")
    user_answer = int(input("Your answer: "))

    # Check if the answer is correct
    correct_answer = num1 + num2
    if user_answer == correct_answer:
        print("Correct!")
    else:
        print("Incorrect.")
        print(f"The expected answer is {correct_answer}")

if __name__ == '__main__':
    main()
```
