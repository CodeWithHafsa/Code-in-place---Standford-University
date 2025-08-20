## Assignment
In Code in Place we are all about building technology to help folks learn. Now it is your turn. Implement Khansole Academy—a program that helps other people learn addition! Write a program that randomly generates a simple addition problem for the user, reads in the answer from the user, and then checks to see if they got it right or wrong.

More specifically, your program should be able to generate simple addition problems that involve adding two 2-digit integers (i.e., the numbers 10 through 99). The user should be asked for an answer to the generated problem. Your program should determine if the answer was correct or not, and give the user an appropriate message to let them know.

A sample run of the program is shown below (user input is in blue):
```
Khansole Academy
What is 51 + 79?
Your answer: 120
Incorrect.
The expected answer is 130
```

Here's another sample run, where the user gets the question correct (user input is in blue):
```
Khansole Academy
What is 55 + 11?
Your answer: 66
Correct!
```

When you have decided that your program works as intended, hit Check Correct.

## Optional Extension
If you're up for it, we can make Khansole Academy an even better learning tool. Be creative! We recommend you start with the "three in a row" extension first, then come up with your own :-).

### Three in a row
In the previous milestone you wrote code to randomly generate one addition problem at a time and tell the user if they got it right or not. In this milestone, you should randomly generate addition problems until the user has gotten 3 problems correct in a row. (Note: the number of problems the user needs to get correctly in a row to complete the program is just one example of a good place to specify a constant in your program).

You should be able to use a lot of your code from the previous milestone to help out here!
A sample run of the program is shown below (user input is in blue).

```
Khansole Academy
What is 51 + 79? 
Your answer: 120 
Incorrect. 
The expected answer is 130 

What is 33 + 19? 
Your answer: 42 
Incorrect. 
The expected answer is 52 

What is 55 + 11? 
Your answer: 66 
Correct! 
You've gotten 1 correct in a row. 

What is 84 + 25? 
Your answer: 109 
Correct! 
You've gotten 2 correct in a row. 

What is 26 + 58? 
Your answer: 74 
Incorrect. 
The expected answer is 84 

What is 98 + 85? 
Your answer: 183 
Correct! 
You've gotten 1 correct in a row. 

What is 79 + 66? 
Your answer: 145 
Correct! 
You've gotten 2 correct in a row. 

What is 97 + 20? 
Your answer: 117 
Correct! 
You've gotten 3 correct in a row. 

Congratulations! You mastered addition.
```

As a side note, one of the earliest programs Mehran wrote (with his friend Matthew) when he was first learning how to program was very similar to Khansole Academy. It was called “M&M’s Math Puzzles.” It was written in a language named BASIC on a computer that had 4K of memory (that’s 4 Kilobytes) and used cassette tapes (the same kind used for music in the 1970’s) to store information. Yeah, Mehran is old.

### Given Code
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