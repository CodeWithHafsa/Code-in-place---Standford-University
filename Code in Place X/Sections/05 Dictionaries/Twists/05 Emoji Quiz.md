## Emoji Quiz

Write a function quiz(emoji_dict) that shows each emoji in the dictionary, asks what word it stands for, and says if the guess is right. Capital letters in a guess are fine, so Love counts for love. At the end, print the score. In main, call quiz instead of printing the dictionary and translating sentences.

Here is a sample run:


```
Let's build your emoji dictionary! Press enter when you are done.
Word: pizza
Emoji for pizza: 🍕
Word: cat
Emoji for cat: 🐱
Word: love
Emoji for love: ❤️
Word:
Words in your dictionary: 3
What word is 🍕? pizza
Correct!
What word is 🐱? dog
Nope, it was cat.
What word is ❤️? Love
Correct!
You got 2 out of 3!
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

#### What Changed
Here are the exact changes made to your original code:

### 1. Added a new `quiz()` function

python

```python
def quiz(emoji_dict):
    score = 0

    for word in emoji_dict:
        emoji = emoji_dict[word]
        guess = input(f"What word is {emoji}? ")

        if guess.lower() == word:
            print("Correct!")
            score += 1
        else:
            print(f"Nope, it was {word}.")

    print(f"You got {score} out of {len(emoji_dict)}!")
```

What it does:

- Starts the score at `0`.
- Shows each emoji and asks the user to guess its word.
- Uses `.lower()` so capital letters don't matter.
- Adds 1 to the score for every correct answer.
- Displays the correct word if the guess is wrong.
- Prints the final score.

### 2. Changed the `main()` function

Removed these lines:

python

```python
print_emoji_dict(emoji_dict)

sentence = input("Enter a sentence: ")
while sentence != "":
    translation = translate(sentence, emoji_dict)
    print(translation)
    sentence = input("Enter a sentence: ")
```

Replaced them with:

python

```python
quiz(emoji_dict)
```

### 3. What stayed the same?

- `build_emoji_dict()` — unchanged.
- `print_emoji_dict()` — no longer needed.
- `translate()` — no longer needed.
- The dictionary-building process — unchanged.

In short: You added the `quiz()` function and replaced the dictionary printing and sentence translation in `main()` with a call to `quiz(emoji_dict)`.

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


# Shows each emoji and asks for its word, then prints the score.
def quiz(emoji_dict):
    score = 0
    for word in emoji_dict:
        emoji = emoji_dict[word]
        guess = input(f"What word is {emoji}? ")
        guess = guess.lower()
        if guess == word:
            print("Correct!")
            score += 1
        else:
            print(f"Nope, it was {word}.")
    total = len(emoji_dict)
    print(f"You got {score} out of {total}!")


def main():
    print("Let's build your emoji dictionary! Press enter when you are done.")
    emoji_dict = build_emoji_dict()
    num_words = len(emoji_dict)
    print(f"Words in your dictionary: {num_words}")
    quiz(emoji_dict)


if __name__ == "__main__":
    main()
```