## Double It

## Assignment
Write a program that asks a user to enter a number. Your program will then double that number and print out the result. It will repeat that process until the value is 100 or greater.

For example if the user enters the number 2, the program's console output would look like the below:

```
Enter a number: 2
4
8
16
32
64
128
```

Note that: \
2 doubled is 4 \
4 doubled is 8 \
8 doubled is 16 \
and so on. \
We stop at 128 because that value is greater than 100.

#### Answer

```python
def main():
    # Prompt the user for a number
    curr_value = int(input("Enter a number: "))

    # Loop until the value is greater than 100
    while curr_value < 100:
        # Double the number
        curr_value = curr_value * 2
        print(curr_value)

if __name__ == '__main__':
    main()
```


