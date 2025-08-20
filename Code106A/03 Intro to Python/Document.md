## Console Program Structure
The following code defines and calls a main() function:

```python
def main():
    # Your code goes here

if __name__ == '__main__':
    main()
```

## Printing

```python
# writes hello world
print("hello world")

# You can print variables
x = 12
print(x)

# You can put an f before the string
print(f"Value of x is {x}")

# You can print multiple things
print("Value of x", x)
```

## Input

```python
# gets input form the user
input_str = input("Prompt: ")
```

## Variables

```python
# example var
variable_name = 12

# example use of a variable
print(variable_name)

# example reassignment
variable_name = variable_name + 2
```

## Changing Types

```python
# input always gives a value of type string
value_as_str = input("Enter a value ")

# you can change the string to a float
value_as_number = float(value_as_str)

# you can change the string to an integer
value_as_int = int(value_as_str)

# change any number (int or float) to str
value_as_str = str(value_as_int)
```

## Random 

```python
# import the python random library
import random 

# generate a random number between 1-100 inclusive
rand_num = random.randint(1, 100) 
```

## AI 

```python
# a library that access the gpt API
from ai import call_gpt

# make a call to gpt and get a response
response = call_gpt("What is the capitol of Kenya?") 
```

## For Loops 

```python
n = int(input("times to repeat? "))
for i in range(n):
    # i is a variable you can use
    # it stores how many times the loop
    # has completed
    print(f"completed {i}")
```

## While Loops 

```python
while condition:
    # code to repeat
```

## If Statement 

```python
if condition:
    # code run if condition passes


if condition:
    # code block for True
else:
    # code block for False
```

## Math 

```python
# a library with math functions
import math

# consider a number
diameter = float(input("Enter a diameter: ")

# +, -, *, / are standard in python
radius = diameter / 2 

# math has many built in functions such as 
# power, square root and pi
area = math.pi * math.pow(radius, 2)
side = math.sqrt(area)
```