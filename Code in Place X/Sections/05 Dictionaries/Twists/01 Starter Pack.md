## Starter Pack

Write two functions that each return a ready-made dictionary: food_pack() with pizza 🍕, taco 🌮 and apple 🍎, and animal_pack() with cat 🐱, dog 🐶 and fish 🐟. In the main function, ask the user which pack they want and use it.

Here is a sample run:

```
Pick a pack (food or animals): food
Words in your dictionary: 3
pizza: 🍕
taco: 🌮
apple: 🍎
Enter a sentence: I want a taco
I want a 🌮
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
1. `food_pack()` returns the food emoji dictionary.
2. `animal_pack()` returns the animal emoji dictionary.
3. In `main()`, the user chooses a pack.
4. The selected dictionary is passed to `print_emoji_dict()` and `translate()`.


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


# Returns a ready-made dictionary of food words.
def food_pack():
    return {"pizza": "🍕", "taco": "🌮", "apple": "🍎"}


# Returns a ready-made dictionary of animal words.
def animal_pack():
    return {"cat": "🐱", "dog": "🐶", "fish": "🐟"}


def main():
    pack = input("Pick a pack (food or animals): ")
    pack = pack.lower()
    if pack == "food":
        emoji_dict = food_pack()
    else:
        emoji_dict = animal_pack()
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