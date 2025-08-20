## Assignment - Multiply Two Numbers
Write a Python program that takes two integer inputs from the user and calculates the value of the first number multiplied with the second. The program should perform the following tasks:

After printing "This program multiplies two numbers."
1. Prompt the user to enter the first number.
2. Read the input and convert it to an integer.
3. Prompt the user to enter the second number.
4. Read the input and convert it to an integer.
5. Calculate the value of multiplying the two numbers.
6. Print the value

Here is a full run of the program (user input is in blue):
```
This program multiplies two numbers.
Enter first number: 20
Enter second number: 3
60
```

In order to pass the tests you will need very specific prompts:
```python
num1 = input("Enter first number: ")
num2 = input("Enter second number: ")
```
Don't forget to change these two values into integers.
This program is very similar to the example: **Add Two Numbers**

```python
"""
Program: multiply two numbers
--------------------
This program asks the user for two
integers and prints the value of the first number
multiplied with the second
"""

def main():
    print("This program multiplies two numbers.")
    # your code here


# This provided line is required at the end of
# Python file to call the main() function.
if __name__ == '__main__':
    main()
```

## Answer
```python
def main():
    print("This program multiplies two numbers.")
    num1 = int(input("Enter first number: "))
    num2 = int(input("Enter second number:"))
    product = num1 * num2
    print(product)

# This provided line is required at the end of
# Python file to call the main() function.
if __name__ == '__main__':
    main()
```
