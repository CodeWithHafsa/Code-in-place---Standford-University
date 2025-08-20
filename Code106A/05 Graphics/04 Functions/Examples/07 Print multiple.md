## Print multiple
Fill out print_multiple(message, repeats), which takes as parameters a string message to print, and an integer repeats number of times to print message. We've written the main() function for you, which prompts the user for a message and a number of repeats.

Here's a sample run of the program (user input is in blue):
```
Please type a message: Hello! 
Enter a number of times to repeat your message: 6 
Hello! 
Hello! 
Hello! 
Hello! 
Hello! 
Hello!
```

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

def print_multiple(message, repeats):
    pass  # Delete this line and write your code here! :)

# There is no need to edit code beyond this point

def main():
    message = input("Please type a message: ")
    repeats = int(input("Enter a number of times to repeat your message: "))
    print_multiple(message, repeats)
    

if __name__ == '__main__':
    main()
```

## Answer
```python
def print_multiple(message, repeats):
    for i in range(repeats):
        print(message)

# There is no need to edit code beyond this point

def main():
    message = input("Please type a message: ")
    repeats = int(input("Enter a number of times to repeat your message: "))
    print_multiple(message, repeats)


if __name__ == '__main__':
    main()
```