## Double Lock

One lock is good, two are better! Write a function `double_lock(message, n)` that encodes the message by n, then encodes the result by n again, and returns it. Instead of cracking the message, ask for a shift and print the double-locked message.

Here is a sample run:

```
Welcome to the Code Machine!
Enter a message: meet me at noon
Enter a shift: 3
Double locked: skkz sk gz tuut
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

The output shows that the message is being encoded using a shift of 3 twice.

* Asked the user to enter a shift number.
* Encoded the message once using the given shift.
* Encoded the first result again using the same shift.
* Printed the final result with `Double locked:`.


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


def double_lock(message, n):
    once = encode(message, n)
    return encode(once, n)


def main():
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    n = int(input("Enter a shift: "))
    secret = double_lock(message, n)
    print("Double locked:", secret)


if __name__ == "__main__":
    main()
```