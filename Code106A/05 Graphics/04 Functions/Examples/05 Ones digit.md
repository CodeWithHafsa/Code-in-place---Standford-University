## Print ones digit
Write a function called print_ones_digit , which takes as a parameter an integer num and prints its ones digit. The modulo (remainder) operator, %, should be helpful to you here. Call your function from main()!

Here's a sample run (user input is in blue):
```
Enter a number: 42
The ones digit is 2
```

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

# Write your helper function here!

def main():
    num = int(input("Enter a number: "))
    # Call your helper function with `num` as a parameter!
    
    
# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Answer
```python
def print_ones_digit(num):
    print("The ones digit is", num % 10)

def main():
    num = int(input("Enter a number: "))
    print_ones_digit(num)


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```
