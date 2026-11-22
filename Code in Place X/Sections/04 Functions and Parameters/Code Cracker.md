## Code Cracker

## Assignment
> About this assignment

## Milestones

### 1. One Letter
For this milestone, write a function called `shift_letter(letter, n)` that takes in a letter and a number, and returns the letter that is n places later in the alphabet. For example, `shift_letter("c", 3)` should return `"f"`.

Two things to know:

1. `ALPHABET.find(letter)` gives you the index of a letter in ALPHABET, for example, "a" is at 0 and "z" is at 25.
2. If the shift runs off the end of ALPHABET, it should wrap back around to the start. Use % to do the wrapping: 27 % 26 is 1, so position 27 means the second letter of the alphabet.

In your main function, ask the user to input any letter and a shift, and use your function to determine the shifted letter. Here is an example output:

```
Welcome to the Code Machine!
Enter a letter: c
Enter a shift: 3
c shifted by 3 is f
```

### 2. A Whole Message
Write a function `encode(message, n)` that returns the whole message with every letter shifted by n.

1. In your function, start by creating an empty string that will contain the shifted string.
2. Then loop over the characters of `message` one at a time. If the character is in `ALPHABET`, use `shift_letter` from milestone 1 to shift it. If it is not a letter, for instance a space, add it unchanged. In your loop, you can use in to check whether one string appears inside another: "c" in `ALPHABET is True`, and " " in `ALPHABET is False`.
3. Return the shifted string.

Then update your main function to ask for a message and a shift instead of a single letter, and print the encoded result. Here is example output:

```
Welcome to the Code Machine!
Enter a message: meet me at noon
Enter a shift: 3
Encoded: phhw ph dw qrrq
```

### 3. Decode It
Write a function decode(message, n) that turns an encoded message back into the original by shifting backwards by n.

**Before you write a loop, stop and think.** Shifting backwards by 3 is the same as shifting forwards by -3, and you already have a function that shifts a whole message forwards by any amount. decode should use this!

Now make your program:

1. Print `Welcome to the Code Machine!` and ask for a message and a shift, as before.
2. Print the encoded message.
3. Print the **decoded** version of what you just encoded.

Example output:

```
Welcome to the Code Machine!
Enter a message: meet me at noon
Enter a shift: 3
Encoded: phhw ph dw qrrq
Decoded: meet me at noon
```

### 4. Crack It
Someone has sent you a coded message and did not tell you the shift. That is fine: there are only 25 of them. Write a function `crack(message)` that prints the message decoded with every shift from 1 to 25.

Your program should now:

1. Print `Welcome to the Code Machine!`
2. Ask for a message and nothing else. No shift this time.
3. Call `crack` on it.

Example output (shortened):

```
Welcome to the Code Machine!
Enter a message: wkh wuhdvxuh lv xqghu wkh ehg
Shift 1: vjg vtgcuwtg ku wpfgt vjg dgf
Shift 2: uif usfbtvsf jt voefs uif cfe
Shift 3: the treasure is under the bed
Shift 4: sgd sqdzrtqd hr tmcdq sgd adc
...
Shift 25: xli xviewyvi mw yrhiv xli fih
```

Your program prints all 25 lines; the real message is the one you can read. Shift 3, here.



### Key Code (Solution)

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
    # Delete pass and start writing your code!
    print("Welcome to the Code Machine!")
    message = input("Enter a message: ")
    crack(message)


if __name__ == "__main__":
    main()
```