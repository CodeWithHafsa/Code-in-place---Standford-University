## Emoji Alphabet

Add these two lists to the top of your program:

```
LETTERS = ["a", "c", "e", "i", "o", "t"]
EMOJIS = ["🍎", "🐱", "🥚", "🍦", "🐙", "🌮"]
```

Write a function build_alphabet(letters, emojis) that returns a dictionary from each letter to the emoji at the same position. Instead of building a dictionary and translating sentences, print the alphabet with print_emoji_dict.

Here is a sample run:


```
a: 🍎
c: 🐱
e: 🥚
i: 🍦
o: 🐙
t: 🌮
```


### Given Code

```python
# Asks the user for words and their emoji until they press enter, and returns the dictionary.
def build_emoji_dict():
    emoji_dict = {}
    word = input("Word: ")
    word = word.lower()
    while word != "":
        emoji = input(f"Emoji for {word}: ")
        emoji_dict[word] = emoji
        word = input("Word: ")
        word = word.lower()
    return emoji_dict


# Prints every word in the dictionary next to its emoji.
def print_emoji_dict(emoji_dict):
    for word in emoji_dict:
        emoji = emoji_dict[word]
        print(f"{word}: {emoji}")


# Swaps every word that has an emoji for its emoji. Other words stay the same.
def translate(sentence, emoji_dict):
    result = ""
    words = sentence.split()
    for word in words:
        lower_word = word.lower()
        if lower_word in emoji_dict:
            emoji = emoji_dict[lower_word]
            result += emoji + " "
        else:
            result += word + " "
    return result


def main():
    print("Let's build your emoji dictionary! Press enter when you are done.")
    emoji_dict = build_emoji_dict()
    num_words = len(emoji_dict)
    print(f"Words in your dictionary: {num_words}")
    print_emoji_dict(emoji_dict)
    sentence = input("Enter a sentence: ")
    while sentence != "":
        translation = translate(sentence, emoji_dict)
        print(translation)
        sentence = input("Enter a sentence: ")


if __name__ == "__main__":
    main()
```

#### What Changed?

1. Added the two lists:

```python
LETTERS = ["a", "c", "e", "i", "o", "t"]
EMOJIS = ["🍎", "🐱", "🥚", "🍦", "🐙", "🌮"]
```

2. Added `build_alphabet()`:

```python
def build_alphabet(letters, emojis):
    alphabet = {}
    for i in range(len(letters)):
        alphabet[letters[i]] = emojis[i]
    return alphabet
```

- `range(len(letters))` loops through the positions in the lists.
- `letters[i]` gets the letter.
- `emojis[i]` gets the emoji at the same position.
- Both are added to the dictionary.

3. Simplified `main()`:

```python
def main():
    alphabet = build_alphabet(LETTERS, EMOJIS)
    print_emoji_dict(alphabet)
```

We removed `build_emoji_dict()` and `translate()` because we no longer need user input.

### Answer

```python
LETTERS = ["a", "c", "e", "i", "o", "t"]
EMOJIS = ["🍎", "🐱", "🥚", "🍦", "🐙", "🌮"]


# Asks the user for words and their emoji until they press enter, and returns the dictionary.
def build_emoji_dict():
    emoji_dict = {}
    word = input("Word: ")
    word = word.lower()
    while word != "":
        emoji = input(f"Emoji for {word}: ")
        emoji_dict[word] = emoji
        word = input("Word: ")
        word = word.lower()
    return emoji_dict


# Prints every word in the dictionary next to its emoji.
def print_emoji_dict(emoji_dict):
    for word in emoji_dict:
        emoji = emoji_dict[word]
        print(f"{word}: {emoji}")


# Swaps every word that has an emoji for its emoji. Other words stay the same.
def translate(sentence, emoji_dict):
    result = ""
    words = sentence.split()
    for word in words:
        lower_word = word.lower()
        if lower_word in emoji_dict:
            emoji = emoji_dict[lower_word]
            result += emoji + " "
        else:
            result += word + " "
    return result


# Returns a dictionary from each letter to the emoji at the same position.
def build_alphabet(letters, emojis):
    alphabet = {}
    for i in range(len(letters)):
        letter = letters[i]
        emoji = emojis[i]
        alphabet[letter] = emoji
    return alphabet


def main():
    alphabet = build_alphabet(LETTERS, EMOJIS)
    print_emoji_dict(alphabet)


if __name__ == "__main__":
    main()
```
