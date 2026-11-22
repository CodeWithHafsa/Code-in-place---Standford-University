## Where Did It Go?

Every Shift line says None, and the decoded messages are printing on their own lines instead! Find the bug and fix it.

Here is what happens now (shortened):
```
Welcome to the Code Machine!
Enter a message: khoor
jgnnq
Shift 1: None
ifmmp
Shift 2: None
hello
Shift 3: None
...
lipps
Shift 25: None
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
    print(encode(message, -n))


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
The bug is that the `decode()` function is printing the decoded message instead of returning it.

This causes `decoded_message` to become `None`, because `print()` does not return a value.

* Replaced `print()` with `return` in the `decode()` function.
* This allows the decoded message to be stored in `decoded_message`.
* The `crack()` function can now correctly check whether the word is present.
* The shift number and decoded message now print together on the same line.

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


def main():
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    crack(message)


if __name__ == "__main__":
    main()
```