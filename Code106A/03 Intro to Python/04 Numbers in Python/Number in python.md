## Numbers in python

**Choose your own adventure**\
Select actions to complete the program. Follow the instructions provided in the blue box.

```python
"""
This program asks the user for two numbers and then subtracts them
"""

def main():
    print("This program subtracts two numbers.")
    num1 = input("Enter first number: ")
    num1 = int(num1)
    num2 = input("Enter second number: ")
    num2 = int(num2)
    
    # Complete the code here

    print("The difference is " + str(diff) + ".")


# This provided line is required at the end of
# Python file to call the main() function.
if __name__ == '__main__':
    main()
```

## Answer
```python
"""
This program asks the user for two numbers and then subtracts them
"""

def main():
    print("This program subtracts two numbers.")
    num1 = input("Enter first number: ")
    num1 = int(num1)
    num2 = input("Enter second number: ")
    num2 = int(num2)
    diff = num1 - num2
    print("The difference is " + str(diff) + ".")


# This provided line is required at the end of
# Python file to call the main() function.
if __name__ == '__main__':
    main()
```