## Mixed Up Arguments

The code machine crashes with a strange error about -. Someone swapped two things in crack. Find the bug and fix it.

Here is what happens now (shortened):

```
Welcome to the Code Machine!
Enter a message: wkh wuhdvxuh lv xqghu wkh ehg
TypeError: bad operand type for unary -: 'str'
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
        decoded_message = decode(shift, message)
        print(f"Shift {shift}: {decoded_message}")


def main():
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    crack(message)


if __name__ == "__main__":
    main()
```

#### What Changed?
The bug is that the arguments in the `decode()` function have been swapped.

The `decode()` function expects:
* `message` first (a string).
* `n` second (a number).

---

* Swapped the arguments in the `decode()` function call.
* Passed `message` as the first argument.
* Passed `shift` as the second argument.
* Fixed the unary minus error.

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
