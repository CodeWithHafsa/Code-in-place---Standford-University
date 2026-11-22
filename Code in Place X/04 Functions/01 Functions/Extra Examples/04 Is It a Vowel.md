## Is It a Vowel?

Write a function that answers a yes-or-no question, and then ask it one.

Your program should:
1. Define a function `is_vowel(letter)` that returns True if the letter is a vowel and False if it is not. Note that `letter` in `VOWELS` asks whether letter appears anywhere in the string VOWELS and returns `True or False`, so you can hand it straight to `return`. This means that you don't need if inside the function.
2. Ask the user for a letter.
3.Print whether or not it is a vowel.

Here is example output from running this program twice:

```
Enter a letter: e
e is a vowel.

Enter a letter: z
z is not a vowel.
```

### Answer

```python
VOWELS = "aeiou"

def is_vowel(letter):
    return letter in VOWELS

def main():
    letter = input("Enter a letter: ")
    if is_vowel(letter):
        print(f"{letter} is a vowel.")
    else:
        print(f"{letter} is not a vowel.")

if __name__ == "__main__":
    main()
```