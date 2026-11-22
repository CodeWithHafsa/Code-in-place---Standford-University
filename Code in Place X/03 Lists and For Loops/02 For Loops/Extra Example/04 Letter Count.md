## Letter Count

Ask the user for a word and a letter. Print how many times that letter appears in the word.

A for loop can walk through a string one letter at a time, just like a list.

#### Answer

```python
def main():
    word = input("Enter a word: ")
    letter = input("Which letter should I count? ")

    # Go through the word one letter at a time
    count = 0
    for char in word:
        if char == letter:
            count += 1

    print(f"{letter} appears {count} times in {word}.")

if __name__ == "__main__":
    main()
```

Output:

```
Enter a word: python
Which letter should I count? t
t appears 1 times in python.
```