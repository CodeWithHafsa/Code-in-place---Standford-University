## Chaotic counting
Fill out the chaotic_counting() function, which prints the numbers from 1 to 10, but with a catch. We've written a done() function which returns True with likelihood DONE_LIKELIHOOD -- at each number, before printing the number, you should call done() and check if it returns True or not. If done() returns True, we're done counting, and you should use a return statement to end the chaotic_counting() function execution and resume execution of main(), which will print "I'm done.". We've written main() for you -- check it out! Notice that we'll only print "I'm done" from main() once chaotic_counting() is done with its execution.

Here's a sample run of this program:

```
I'm going to count until 10 or until I feel like stopping, whichever comes first. 
1 
2 
3 
I'm done.
```

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

import random

DONE_LIKELIHOOD = 0.3

def chaotic_counting():
    pass  # Delete this line and write your code here! :)

# There is no need to edit code beyond this point

def done():
    """ Returns True with a probability of DONE_LIKELIHOOD """
    if random.random() < DONE_LIKELIHOOD:
        return True
    return False

def main():
    print("I'm going to count until 10 or until I feel like stopping, whichever comes first.")
    chaotic_counting()
    print("I'm done")

if __name__ == "__main__":
    main()
```

## Answer
```python
import random  # This is the missing import

DONE_LIKELIHOOD = 0.3  # Probability of stopping early (can adjust this!)

def chaotic_counting():
    for i in range(10):
        curr_num = i + 1
        if done():
            return  # Ends the function early
        print(curr_num)

def done():
    """Returns True with a probability of DONE_LIKELIHOOD"""
    if random.random() < DONE_LIKELIHOOD:
        return True
    return False

def main():
    print("I'm going to count until 10 or until I feel like stopping, whichever comes first.")
    chaotic_counting()
    print("I'm done")

if __name__ == "__main__":
    main()
```