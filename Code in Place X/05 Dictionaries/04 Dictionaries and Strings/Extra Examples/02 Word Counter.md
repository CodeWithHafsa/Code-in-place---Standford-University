## Word Counter

Count how many times each word appears in a sentence.

Your program should:
* Ask the user for a sentence.
* Count how many times each word appears, ignoring capital letters.
* Print every word once, next to its count.

Here is example output from running this program:

```
Enter a sentence: the cat and the hat and the bat
the: 3
cat: 1
and: 2
hat: 1
bat: 1
```

This is one of the most useful dictionary patterns there is. The keys are the words and the values are counts. The first time you see a word it is not a key yet, so you add it with a count of 1. Every time after that it is already a key, so you add 1 to the count that is there. `sentence.split()` breaks the sentence into a list of words.

### Answer

```python
def main():
    sentence = input("Enter a sentence: ").lower()
    counts = {}
    for word in sentence.split():
        if word in counts:
            counts[word] += 1
        else:
            counts[word] = 1
    for word in counts:
        print(f"{word}: {counts[word]}")


if __name__ == "__main__":
    main()
```