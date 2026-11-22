## Emoji Translator

> About this assignment

#### Milestones

**1. Build the Dictionary** \
Write a function build_emoji_dict() that asks the user for words and their emoji, and returns a dictionary from each word to its emoji.

Start with an empty dictionary.

* Ask for a word. Then ask for that word's emoji, and add the pair to your dictionary.
* Keep going until the user presses enter without typing a word. Then return the dictionary.
* Lowercase each word, so that Pizza and pizza are the same word. 

Print how many words the dictionary has. You can do that inside build_emoji_dict or in main. len works on dictionaries just like it works on lists. Your starter code already prints the welcome message, and when you are ready to test, uncomment the line in main that calls build_emoji_dict().

**2. Show the Dictionary** \
Write a function print_emoji_dict(emoji_dict) that prints every word in the dictionary next to its emoji. When you loop over a dictionary with for, you get its keys one at a time. Once you have a key, you can look up its value.

Call print_emoji_dict in main, right after you print how many words there are. Important note: make sure that you returned your dictionary from build_emoji_dict() so that you can pass it into print_emoji_dict(emoji_dict)!

**3. Translate a Sentence** \
Now for the fun part. Write a function translate(sentence, emoji_dict) that returns the sentence with every word that has an emoji swapped for its emoji.
* Start with an empty string for the result.
* Loop over the words in the sentence. sentence.split() gives you the words as a list.
* If a word is in the dictionary, add its emoji to the result. If it is not, add the word itself. Either way, put a space after it. A space at the end of the line is fine, since the checker ignores it.
* The words in your dictionary are lowercase, but the user might type Pizza. Lowercase each word before you check whether it is in the dictionary. If it has no emoji, add it to the result the way the user typed it.


**4. Keep Translating**\
One sentence is not enough. Change main so that it keeps asking for sentences and printing their translations until the user presses enter without typing anything.

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