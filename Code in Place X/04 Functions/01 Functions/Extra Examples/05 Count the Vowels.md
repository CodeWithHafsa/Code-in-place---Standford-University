## Count the Vowels

Your program should:

1. Use your `is_vowel(letter)` function from Is It a Vowel?
2. Define a second function `count_vowels(word)` that returns how many vowels are in the word. It should **call** `is_vowel` rather than checking the letters itself.
3. Ask the user for a word and print the count.

Here is example output from running this program twice:

```
Enter a word: banana
banana has 3 vowels.

Enter a word: rhythm
rhythm has 0 vowels.
```

The shape of count_vowels is worth learning by heart, because it is the shape of most of this week’s assignment:

```python
count = 0
for letter in word:
    ...
return count
```

**Start at zero, change it once per letter, hand it back after the loop.** If you accidentally return one indent deeper and return inside the loop, this would end the function on the very first letter. Line it up with the for, not with the body.

### Answer

```python
VOWELS = "aeiou"

def is_vowel(letter):
    return letter in VOWELS

def count_vowels(word):
    count = 0
    for letter in word:
        if is_vowel(letter):
            count += 1
    return count

def main():
    word = input("Enter a word: ")
    print(f"{word} has {count_vowels(word)} vowels.")

if __name__ == "__main__":
    main()
```