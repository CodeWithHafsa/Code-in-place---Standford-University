## Team Dictionary

Write a program that combines two dictionaries. First, write a function called `combine(dict1, dict2)` that returns one new dictionary with every pair from both. Then ask the user to input two dictionaries, combine them, and use the combined dictionary for translation.

Here is a sample run:

```
Player 1, build your emoji dictionary! Press enter when you are done.
Word: pizza
Emoji for pizza: 🍕
Word: love
Emoji for love: ❤️
Word:
Player 2, build your emoji dictionary! Press enter when you are done.
Word: dog
Emoji for dog: 🐶
Word: love
Emoji for love: 💜
Word:
Words in your dictionary: 3
pizza: 🍕
love: 💜
dog: 🐶
Enter a sentence: my dog and I love pizza
my 🐶 and I 💜 🍕
Enter a sentence:
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

#### What changed?
1. `combine(dict1, dict2)` – Creates a copy of the first dictionary and adds all pairs from the second dictionary.
2. `dict1.copy()` – Ensures the original first dictionary isn't changed.
3. `combined_dict.update(dict2)` – Combines both dictionaries. Duplicate words use Player 2's emoji.
4. `emoji_dict = combine(dict1, dict2)` – Uses the combined dictionary for translation.

### Answer

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


# Returns one dictionary with every pair from both dictionaries.
def combine(dict1, dict2):
    combined = {}
    for word in dict1:
        combined[word] = dict1[word]
    for word in dict2:
        combined[word] = dict2[word]
    return combined


def main():
    print("Player 1, build your emoji dictionary! Press enter when you are done.")
    dict1 = build_emoji_dict()
    print("Player 2, build your emoji dictionary! Press enter when you are done.")
    dict2 = build_emoji_dict()
    emoji_dict = combine(dict1, dict2)
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
