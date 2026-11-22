## Back to Words

Write a function reverse_dict(emoji_dict) that returns a new dictionary from each emoji to its word. Then, instead of asking for sentences, ask for emoji messages and translate them back into words. Put a space between the emoji when you type a message.

Here is a sample run:

```
Let's build your emoji dictionary! Press enter when you are done.
Word: pizza
Emoji for pizza: 🍕
Word: love
Emoji for love: ❤️
Word: cat
Emoji for cat: 🐱
Word:
Words in your dictionary: 3
pizza: 🍕
love: ❤️
cat: 🐱
Enter an emoji message: 🐱 ❤️ 🍕
cat love pizza
Enter an emoji message: 🐶 ❤️ 🍕
🐶 love pizza
Enter an emoji message:
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

1. Added `reverse_dict()`

python

```python
def reverse_dict(emoji_dict):
    reversed_dict = {}
    for word in emoji_dict:
        emoji = emoji_dict[word]
        reversed_dict[emoji] = word
    return reversed_dict
```

This changes the dictionary from:

```python
{"pizza": "🍕", "love": "❤️", "cat": "🐱"}
```

Into:

```python
{"🍕": "pizza", "❤️": "love", "🐱": "cat"}
```

2. Changed the `translate()` function

- It now looks for emojis instead of words.
- If an emoji exists in the reversed dictionary, it replaces it with the word.
- If the emoji isn't found, it leaves it unchanged.
- `.strip()` removes the extra space at the end.

3. Changed `main()`

- We create the reversed dictionary using `reverse_dict(emoji_dict)`.
- We ask for an emoji message instead of a sentence.
- We translate the emoji message back into words.

**Important:** We kept `build_emoji_dict()` and `print_emoji_dict()` exactly the same.

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


# Returns a new dictionary from each emoji to its word.
def reverse_dict(emoji_dict):
    word_dict = {}
    for word in emoji_dict:
        emoji = emoji_dict[word]
        word_dict[emoji] = word
    return word_dict


def main():
    print("Let's build your emoji dictionary! Press enter when you are done.")
    emoji_dict = build_emoji_dict()
    num_words = len(emoji_dict)
    print(f"Words in your dictionary: {num_words}")
    print_emoji_dict(emoji_dict)
    word_dict = reverse_dict(emoji_dict)
    message = input("Enter an emoji message: ")
    while message != "":
        translation = translate(message, word_dict)
        print(translation)
        message = input("Enter an emoji message: ")


if __name__ == "__main__":
    main()
```