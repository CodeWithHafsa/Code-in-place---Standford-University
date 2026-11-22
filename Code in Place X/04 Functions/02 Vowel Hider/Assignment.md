## Vowel Hider

### Assignment

>About this assignment

Write a program that hides the vowels in a secret message by replacing each one with a star. Here is example output:

```
Enter a secret: meet me at noon
m**t m* *t n**n
```

Your starter code already has VOWELS, the five lowercase vowels. Messages are lowercase only, so you never have to think about capitals.

This assignment has two milestones. Milestone 1 checks your function on its own: we call `hide_vowels` with a few messages and look at what it returns. Milestone 2 checks your whole program.


## Milestone

### 1. Write hide_vowels
Write a function `hide_vowels(message)` that returns a copy of message with every vowel replaced by *.

* Start with an empty string called result.
* Loop over the letters of message one at a time.
* If the letter is in VOWELS, add "*" to result. Otherwise add the letter itself. letter in VOWELS is True when the letter appears anywhere in VOWELS.
* After the loop is done, return result.

For example, hide_vowels("banana") should return "b*n*n*", and hide_vowels("rhythm") returns "rhythm" unchanged.

The checks for this milestone call your function directly, so you do not need to change main yet. Make sure `hide_vowels` uses return, not print.

### 2. Ask the User
Now update main so that it asks the user for a secret with `input("Enter a secret: ")`, calls `hide_vowels` on it, and prints the result.

Here is example output:

```
Enter a secret: hello world
h*ll* w*rld
```

Notice that you did not have to change `hide_vowels` at all! You wrote it once, and now main can call it on anything the user types.

### Answer

```python
VOWELS = "aeiou"

# Milestone 1
def hide_vowels(message):
    result = ""

    for letter in message:
        if letter in VOWELS:
            result += "*"
        else:
            result += letter

    return result

# Milestone 2
def main():
    secret = input("Enter a secret: ")
    hidden = hide_vowels(secret)
    print(hidden)


if __name__ == "__main__":
    main()
```