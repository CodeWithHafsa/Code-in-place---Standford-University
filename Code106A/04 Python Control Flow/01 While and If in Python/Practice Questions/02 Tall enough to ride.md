## Question # 02 - Tall enough to ride
Write a program which asks the user how tall they are and prints whether or not they're taller than a pre-specified minimum height.\
In amusement parks (ah, the good old pre-pandemic days...), rollercoasters frequently have minimum height requirements for safety reasons. Assume for now that the minimum height is 50 of whatever height unit you'd like :)

Here's two sample runs (user input is in bold italics):
```
How tall are you? 100 
You're tall enough to ride!

How tall are you? 10 
You're not tall enough to ride, but maybe next year!
```

(For an extra challenge, write code which will repeatedly ask a user how tall they are and tell them whether or not they're tall enough to ride, until the user doesn't enter a height at all, in which case the program stops. Curious about how to do this? See the function `tall_enough_extension()` in the solution code!)

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
MINIMUM_HEIGHT = 50 # arbitrary units

def main():
    height = float(input("How tall are you? "))
    if height >= MINIMUM_HEIGHT:
        print("You're tall enough to ride!")
    else:
        print("You're not tall enough to ride, but maybe next year!")


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Challenge
```python
MINIMUM_HEIGHT = 50  # Arbitrary units :)

def main():
    # Ask the user for a height to check
    height = input("How tall are you? ")

    # If the user presses Enter immediately (without typing anything),
    # the result of input() will be an empty string (nothing between the quotation marks!)
    while height != "":
        height = float(height)  # Convert non-empty strings to be a float!
        
        # Perform height check
        if height >= MINIMUM_HEIGHT:
            print("You're tall enough to ride!")
        else:
            print("You're not tall enough to ride, but maybe next year!")

        # Ask the user for another height to check
        height = input("How tall are you? ")


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```