Sometimes code breakers know one word that is in the secret message. Change the program to:

1. Ask the user for a word.
2. Pass that word into crack as a second parameter.
3. Print only the shifts whose decoded message contains that word.


Here is a sample run:
```
Welcome to the Code Machine!
Enter a message: atkkl alcej ty esp alcv
A word you think is in it: party
Shift 11: pizza party in the park
```

### Given Code
```python
ALPHABET = "abcdefghijklmnopqrstuvwxyz"


def shift_letter(letter, n):
    position = ALPHABET.find(letter)
    new_position = (position + n) % len(ALPHABET)
    return ALPHABET[new_position]


def encode(message, n):
    result = ""
    for letter in message:
        if letter in ALPHABET:
            result += shift_letter(letter, n)
        else:
            result += letter
    return result


def decode(message, n):
    return encode(message, -n)


def crack(message):
    for i in range(25):
        shift = i + 1
        decoded_message = decode(message, shift)
        print(f"Shift {shift}: {decoded_message}")


def main():
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    crack(message)


if __name__ == "__main__":
    main()
```

#### What Changed?
* Added an input to ask the user for a word.
* Added `word` as the second parameter of the `crack()` function.
* Passed `word` into `crack(message, word)`.
* Added an `if` statement to check whether the decoded message contains the given word.
* Used `print()` only when the word is found.


### Answer

```python
ALPHABET = "abcdefghijklmnopqrstuvwxyz"


def shift_letter(letter, n):
    position = ALPHABET.find(letter)
    new_position = (position + n) % len(ALPHABET)
    return ALPHABET[new_position]


def encode(message, n):
    result = ""
    for letter in message:
        if letter in ALPHABET:
            result += shift_letter(letter, n)
        else:
            result += letter
    return result


def decode(message, n):
    return encode(message, -n)


def crack(message, clue):
    for i in range(25):
        shift = i + 1
        decoded_message = decode(message, shift)
        if clue in decoded_message:
            print(f"Shift {shift}: {decoded_message}")


def main():
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    clue = input("A word you think is in it: ")
    crack(message, clue)


if __name__ == "__main__":
    main()
```