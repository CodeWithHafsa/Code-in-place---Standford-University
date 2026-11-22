## Swap Ends
The first and last people in line want to trade places. Swap the first and last names in the list, and print the list before and after.

Save the first name in a variable before you write over it!

#### Answer

```python
def main():
    line = ["Ana", "Ben", "Cleo", "Dev"]
    print("Before:", line)

    # Save the first name, because the next step writes over it
    first = line[0]
    last_index = len(line) - 1

    line[0] = line[last_index]
    line[last_index] = first
    print("After:", line)

if __name__ == "__main__":
    main()
```

Output:

```
Before: ['Ana', 'Ben', 'Cleo', 'Dev']
After: ['Dev', 'Ben', 'Cleo', 'Ana']
```