## Question # 02 - How old are they?
Write a program to solve this age-related riddle!\
Anton, Beth, Chen, Drew, and Ethan are all friends. Their ages are as follows:
* Anton is 21 years old.
* Beth is 6 years older than Anton.
* Chen is 20 years older than Beth.
* Drew is as old as Chen's age plus Anton's age.
* Ethan is the same age as Chen.

Your code should store each person's age to a variable and print their names and ages at the end. The autograder is sensitive to capitalization and punctuation, be careful! Your solution should look like this (the below numbers are made up -- your solution should have the correct values!):

```
Anton is 3
Beth is 4
Chen is 5
Drew is 6
Ethan is 7
```

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

def main():
    print("Delete this line and write your code here! :)")


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Answer
```python 
def main():
    Anton = 21
    Beth = Anton + 6
    Chen = Beth + 20
    Drew = Chen + Anton
    Ethan = Chen

    print("Anton is", Anton)
    print("Beth is", Beth)
    print("Chen is", Chen)
    print("Drew is", Drew)
    print("Ethan is", Ethan)


if __name__ == '__main__':
    main()
```
