## Mirror Alphabet

A different kind of code: flip the alphabet, so a becomes z, b becomes y, and so on.

To mirror one letter, find its position with `ALPHABET.find(letter)`. The mirrored letter is at position `25 - position`. For example, c is at position 2, and `25 - 2` is 23, which is x.

Write `mirror_letter(letter)`, which returns the mirrored letter, and `mirror(message)`, which mirrors every letter and leaves spaces alone. Instead of cracking the message, just print the message mirrored, and then mirrored again.

Here is a sample run:

```
Welcome to the Code Machine!
Enter a message: hello friend
Mirrored: svool uirvmw
Mirrored again: hello friend
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

Need to create two new functions:

* `mirror_letter(letter)` – finds the position of a letter and returns its opposite letter in the alphabet.
* `mirror(message)` – mirrors every letter in the message while keeping spaces unchanged.

---

* Created `mirror_letter(letter)` to find the opposite letter in the alphabet.
* Used `25 - position` to calculate the mirrored letter's position.
* Created `mirror(message)` to mirror every letter.
* Kept spaces unchanged using the `else` statement.
* Mirrored the message a second time to get the original message back.


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


def mirror_letter(letter):
    position = ALPHABET.find(letter)
    return ALPHABET[25 - position]


def mirror(message):
    result = ""
    for letter in message:
        if letter in ALPHABET:
            result += mirror_letter(letter)
        else:
            result += letter
    return result


def crack(message):
    for i in range(25):
        shift = i + 1
        decoded_message = decode(message, shift)
        print(f"Shift {shift}: {decoded_message}")


def main():
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    secret = mirror(message)
    print("Mirrored:", secret)
    print("Mirrored again:", mirror(secret))


if __name__ == "__main__":
    main()
```