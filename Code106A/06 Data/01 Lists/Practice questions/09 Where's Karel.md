## Question # 09 - Where's Karel?
Fill in the function `find_karel(roster)` which takes in a list, roster, and prints "Karel is here!" if 'karel' is an element in roster, or prints "Karel isn't here." if 'karel' isn't an element in roster. You can assume all elements in roster will be lowercase.

We've provided you some code which will populate a list with names and pass it into your function.

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

def find_karel(roster):
    """
    Prints "Karel isn't here." if 'karel' is not in the list `roster` and "Karel is here!" if 'karel' is present in `roster`.
    """
    
    pass  # Delete this line and write your code here! :)

# There is no need to edit code beyond this point

def get_list():
    """
    Prompts the user to enter one element of the list at a time and returns the resulting list. All elements will be lowercase.
    """
    lst = []
    elem = input("Please enter an element of the list or press enter to stop. ")
    while elem != "":
        lst.append(elem.lower())
        elem = input("Please enter an element of the list or press enter to stop. ")
    return lst


def main():
    roster = get_list()
    find_karel(roster)


if __name__ == '__main__':
    main()
```

## Answer
```python
def find_karel(roster):
    """
    Prints "Karel isn't here." if 'karel' is not in the list `roster` and "Karel is here!" if 'karel' is present in `roster`.
    """
    if 'karel' in roster:
        print("Karel is here!")
    else:
        print("Karel isn't here.")

# There is no need to edit code beyond this point

def get_list():
    """
    Prompts the user to enter one element of the list at a time and returns the resulting list. All elements will be lowercase.
    """
    lst = []
    elem = input("Please enter an element of the list or press enter to stop. ")
    while elem != "":
        lst.append(elem.lower())
        elem = input("Please enter an element of the list or press enter to stop. ")
    return lst

def main():
    roster = get_list()
    find_karel(roster)


if __name__ == '__main__':
    main()
```