## Key Letter

Spies use a key letter instead of a shift number. Key a means shift 0, b means shift 1, c means shift 2, and so on.

1. Write a function `letter_to_shift(key)` that returns the shift for a key letter.
2. Instead of cracking the message, ask for a key letter and print the message encoded with that key's shift.

Here is a sample run:

```
Welcome to the Code Machine!
Enter a message: meet me at noon
Enter a key letter: d
Secret: phhw ph dw qrrq
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
Need to add a new function called letter_to_shift(key) that converts a key letter into a shift number.

For example:
* a = 0
* b = 1
* c = 2
* d = 3

You can use `ALPHABET.find(key)` to get the shift number.
* Created a new function `letter_to_shift(key)`.
* Used `ALPHABET.find(key)` to convert the key letter into a shift number.
* Asked the user to enter a key letter instead of cracking the message.
* Passed the shift number into `encode()`.
* Printed the encoded message using `Secret:`.

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


def crack(message):
    for i in range(25):
        shift = i + 1
        decoded_message = decode(message, shift)
        print(f"Shift {shift}: {decoded_message}")


def letter_to_shift(key):
    shift = ALPHABET.find(key)
    return shift


def main():
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    key = input("Enter a key letter: ")
    shift = letter_to_shift(key)
    secret = encode(message, shift)
    print("Secret:", secret)


if __name__ == "__main__":
    main()
```