## Even or Odd

Tell a user whether the number they typed is even or odd.

Your program should:

1. Ask the user for a number.
2. If dividing that number by 2 leaves no remainder, print that it is **even**.
3. Otherwise, print that it is **odd**.

Here is example output from running this program twice:

```
Enter a number: 7
7 is odd!

Enter a number: 4
4 is even!
```

% gives you the **remainder** left over after a division, so num % 2 is 0 for every even number and 1 for every odd one. Comparing a remainder against 0 is how you ask "does this divide evenly?"

#### Answer

```python
def main():
    num = int(input("Enter a number: "))

    if num % 2 == 0:
        print(f"{num} is even!")
    else:
        print(f"{num} is odd!")

if __name__ == "__main__":
    main()
```
