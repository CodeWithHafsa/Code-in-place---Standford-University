## Emoji Helper

When a word has no emoji, ask call_gpt for one instead of keeping the word. Add the new emoji to the dictionary, so the translator learns it. When the user is done translating, print how many words the dictionary has now, and print the dictionary again to see every word it learned.

Here is a sample run (the AI's emoji may be different):

```
Let's build your emoji dictionary! Press enter when you are done.
Word: pizza
Emoji for pizza: 🍕
Word: love
Emoji for love: ❤️
Word:
Words in your dictionary: 2
pizza: 🍕
love: ❤️
Enter a sentence: I love tea
🙋 ❤️ 🍵
Enter a sentence:
Words in your dictionary: 4
pizza: 🍕
love: ❤️
i: 🙋
tea: 🍵
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
Need to make two main changes:
* Update translate() so that when a word isn't in the dictionary, it calls call_gpt() to get an emoji and adds that word and emoji to the dictionary.
* Update main() to print the dictionary again after the user finishes translating.

1. Modified `translate()`

```python
else:
    emoji = call_gpt(lower_word)
    emoji_dict[lower_word] = emoji
```

- `call_gpt(lower_word)` asks AI for an emoji.
- `emoji_dict[lower_word] = emoji` saves the new emoji in the dictionary.
- The next time that word appears, the program uses the saved emoji instead of asking AI again.

2. Added two lines at the end of `main()`

```python
print(f"Words in your dictionary: {len(emoji_dict)}")
print_emoji_dict(emoji_dict)
```

### Answer:

```python
from ai import call_gpt


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
            emoji = call_gpt(f"Reply with only one emoji for the word {word}.")
            emoji_dict[lower_word] = emoji
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
    num_words = len(emoji_dict)
    print(f"Words in your dictionary: {num_words}")
    print_emoji_dict(emoji_dict)


if __name__ == "__main__":
    main()
```