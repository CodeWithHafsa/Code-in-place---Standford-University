## Question # 01 - Double Lists
Write a program that doubles each element in a list of numbers. For example, if you start with this list:

```python
numbers = [1, 2, 3, 4]
```

You should end with this list:
```python
numbers = [2, 4, 6, 8]
```

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

def main():
    numbers = [1, 2, 3, 4]  # Creates a list of numbers

    # Write your code here! :)

    print(numbers) # This should print the doubled list


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Answer
```python
def main():
    numbers = [1, 2, 3, 4]  # Creates a list of numbers

    for i in range(len(numbers)):  # Loop through the indices of the list
        elem_at_index = numbers[i]  # Get the element at index i in the numbers list
        numbers[i] = elem_at_index * 2  # Set the element at index i to be equal to the previous element times 2

    print(numbers)  # This should print the doubled list


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```