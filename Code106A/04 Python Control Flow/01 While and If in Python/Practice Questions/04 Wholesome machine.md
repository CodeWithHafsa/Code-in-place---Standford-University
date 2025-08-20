## Question # 04 - Wholesome machine
Write a program which prompts the user to type an affirmation of your choice (we'll use "I am capable of doing anything I put my mind to.") until they type it correctly. Sometimes, especially in the midst of such uncertain times, we just need to be reminded that we are resilient, capable, and strong; this little Python program may be able to help!

Here's a sample run of the program (user input is in blue):

```
Please type the following affirmation: I am capable of doing anything I put my mind to. 
Hmmm 
That was not the affirmation. 
Please type the following affirmation: I am capable of doing anything I put my mind to. 
I am capable of doing anything I put my mind to. 
That's right!
```

Note that you can call input() with no prompt and it will still wait for a user to type something!

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

AFFIRMATION = "I am capable of doing anything I put my mind to."

def main():
    print("Delete this line and write your code here! :)")


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Answer
```python
AFFIRMATION = "I am capable of doing anything I put my mind to."

def main():
    # First prompt (no trailing space)
    print("Please type the following affirmation: " + AFFIRMATION)

    user_feedback = input()
    
    while user_feedback != AFFIRMATION:
        print("That was not the affirmation.")

        # Second and further prompts (with trailing space after the period)
        print("Please type the following affirmation: " + AFFIRMATION + " ")
        user_feedback = input()

    print("That's right! :)")

if __name__ == '__main__':
    main()
```