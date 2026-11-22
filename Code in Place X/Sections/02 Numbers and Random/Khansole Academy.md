## Khansole Academy

## Assignment

Implement Khansole Academy: a program that helps people practice addition!

#### Step 1:

Write a program that generates simple addition problems that involve adding two 2-digit integers (i.e., the numbers 10 through 99). The user should be asked for an answer to the generated problem. Your program should determine if the answer was correct or not, and give the user an appropriate message to let them know.

A sample run of the program is shown below:

```
Khansole Academy
What is 51 + 79?
Your answer: 120
Incorrect.
The expected answer is 130
```

Here's another sample run, where the user gets the question correct:

```
Khansole Academy
What is 55 + 11?
Your answer: 66
Correct!
```

#### Step 2: Three in a row!

In the previous step you wrote code to randomly generate one addition problem at a time and tell the user if they got it right or not. Update your code to randomly generate addition problems until the user has gotten 3 problems correct in a row.

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

#### Answer

```python

from random import randint

def main():
    print("Khansole Academy")

    correct_in_a_row = 0

    while correct_in_a_row < 3:
        # Generate two random numbers from 10 to 99
        num1 = randint(10, 99)
        num2 = randint(10, 99)

        # Ask the addition question
        print(f"What is {num1} + {num2}?")
        user_ans = int(input("Your answer: "))

        # Calculate the correct answer
        true_ans = num1 + num2

        # Check the user's answer
        if user_ans == true_ans:
            print("Correct!")
            correct_in_a_row += 1
            print(f"You've gotten {correct_in_a_row} correct in a row.")
        else:
            print("Incorrect.")
            print(f"The expected answer is {true_ans}")
            correct_in_a_row = 0

        print()

    print("Congratulations! You mastered addition.")

if __name__ == '__main__':
    main()
```



