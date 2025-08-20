## Assignment 
Print 10 random numbers in the range 1 to 100. When you're done, click on the "Check Correct" button.

Here is an example run:
```
45
79
61
47
52
10
16
83
19
12
```

Each time you run your program you should get different numbers
```
81
76
70
1
27
63
96
100
32
92
```

Recall that the python random library has a function randint which returns an integer in the range set by the parameters (inclusive). For example this call would produce a random integer between 1 and 6, which could include 1 and could include 6:
```python
value = random.randint(1, 6)
```

### Given Code
```python
import random

N_NUMBERS = 10
MIN_VALUE = 1
MAX_VALUE = 100

def main():
    """
    You should write your code here. Make sure to delete 
    the 'pass' line before starting to write your own code.
    """
    pass

if __name__ == '__main__':
    main()
```

## Answer
```python
import random

N_NUMBERS = 10
MIN_VALUE = 1
MAX_VALUE = 100

def main():
    for _ in range(N_NUMBERS):
        number = random.randint(MIN_VALUE, MAX_VALUE)
        print(number)

if __name__ == '__main__':
    main()
```