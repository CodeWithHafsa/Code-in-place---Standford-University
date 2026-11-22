## Spy Briefing

Define a function `spy_message(topic)` which asks `call_gpt` to write a short secret spy message about topic and returns it. Instead of cracking a message the user types, ask for a topic, encode the spy message with a random shift, and print only the secret. Nobody knows what it says, not even the driver! When the user presses enter, crack it.

Here is a sample run (shortened):

```python
Welcome to the Code Machine!
Enter a topic: pizza
Secret briefing: aol wpggh kyvw pz ha tpkupnoa if aol vsk vhr ayll
Can anyone crack it? Press enter to find out. 
Shift 1: znk voffg jxuv oy gz sojtomnz he znk urj ugq zxkk
Shift 2: ymj uneef iwtu nx fy rnisnlmy gd ymj tqi tfp ywjj
...
Shift 6: uif qjaab espq jt bu njeojhiu cz uif pme pbl usff
Shift 7: the pizza drop is at midnight by the old oak tree
Shift 8: sgd ohyyz cqno hr zs lhcmhfgs ax sgd nkc nzj sqdd
...
Shift 25: bpm xqhhi lzwx qa ib uqlvqopb jg bpm wtl wis bzmm
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
* Imported the `random` module to generate a random shift.
* Created `spy_message(topic)` to ask AI to write a short spy message.
* Used `call_gpt()` to generate the message and `return` to send it back.
* Asked the user to enter a topic instead of an encrypted message.
* Generated a random shift between 1 and 25.
* Encoded the AI-generated message using the random shift.
* Printed only the encrypted secret briefing.
* Used `input()` to wait until the user presses Enter.
* Called `crack(secret)` to display all possible decoded messages.

### Answer

```python
from random import randint
from ai import call_gpt

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


def spy_message(topic):
    prompt = f"Write one short secret spy message about {topic}. Use only lowercase letters and spaces."
    message = call_gpt(prompt)
    return message


def main():
    print("Welcome to the Code Machine!")
    topic = input("Enter a topic: ")
    message = spy_message(topic)
    shift = randint(1, 25)
    secret = encode(message, shift)
    print("Secret briefing:", secret)
    input("Can anyone crack it? Press enter to find out. ")
    crack(secret)


if __name__ == "__main__":
    main()
```