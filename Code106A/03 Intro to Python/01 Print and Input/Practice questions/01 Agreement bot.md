## Practice Question # 01
Write a program which asks the user what their favorite animal is, and then always responds with "My favorite animal is also ___!" (the blank should be filled in with the user-inputted animal, of course).

Here's a sample run of the program (user input is in bold italics - note the space between the prompt and the user input!):

    What's your favorite animal? cow 
    My favorite animal is also cow!
---
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
    animal = input("What's your favorite animal? ")
    print(f"My favorite animal is also {animal}!")
    

if __name__ == '__main__':
    main()
```