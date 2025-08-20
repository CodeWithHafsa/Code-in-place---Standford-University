## Print divisor
Write the helper function print_divisors(num), which takes in a number and prints all of its divisors (all the numbers from 1 to num inclusive that num can be cleanly divided by (there is no remainder to the division). Don't forget to call your function in main()!

Here's a sample run (user input is in blue):
```
Enter a number: 12 
Here are the divisors of 12 
1 
2 
3 
4 
6 
12
```

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

# Write your function here!

def main():
    num = int(input("Enter a number: "))
    # Call your function here with `num` as a parameter!


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Answer
```python
def print_divisors(num):
    print("Here are the divisors of", num)
    for i in range(num):
        curr_divisor = i + 1
        if num % curr_divisor == 0:
            print(curr_divisor)

def main():
    num = int(input("Enter a number: "))
    print_divisors(num)


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```