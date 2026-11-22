## Unknown Word

The translator crashes when we type a sentence! Find the bug and fix it.

Here is what happens now (shortened):

```
Words in your dictionary: 3
pizza: 🍕
love: ❤️
cat: 🐱
Enter a sentence: I love pizza
KeyError: 'i'
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
        emoji = emoji_dict[lower_word]
        result += emoji + " "
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

- `emoji_dict.get(lower_word, word)` returns the emoji if the word is in the dictionary.
- If the word isn't found, it returns the original word instead.
- This prevents the `KeyError` and keeps words without emojis unchanged.

### Answer:

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