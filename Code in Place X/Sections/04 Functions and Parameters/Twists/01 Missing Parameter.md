## Missing Parameter

The code machine crashes before it prints anything! There is something wrong with the function decode. Find the bug and fix it.

Here is what happens now (shortened):
```
Welcome to the Code Machine!
Enter a message: wkh wuhdvxuh lv xqghu wkh ehg
TypeError: decode() takes 1 positional argument but 2 were given
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


def decode(n):
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

#### What changed?
* Added `message` as a parameter in the `decode()` function.
* Added `n` as the second parameter to accept the shift value.
* Changed `decode()` to `return encode(message, -n)` to reverse the encryption.
* ixed the error caused by passing two arguments to a function that accepted only one.
* Now the program can successfully decode the encrypted message.

### Answer:

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