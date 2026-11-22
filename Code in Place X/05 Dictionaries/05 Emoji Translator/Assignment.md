## Emoji Translator

> About This Assignment

In this assignment you will build a translator that turns sentences into emoji 🎉

Your program works in two steps. First, the user teaches it which emoji goes with which word. Then it translates their sentences, swapping every word it knows for its emoji. Here is an example output:

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
Enter a sentence: I love pizza
I ❤️ 🍕
Enter a sentence: my cat loves tea
my 🐱 loves tea
Enter a sentence:
```

This assignment has four milestones. The first three each add one function, and the fourth puts them all to work in `main`. The Check button runs your whole program, starting from `main`, so each new function needs to be called from `main` before its tests can pass. Every milestone is a program you can run.

To complete a milestone, pass its tests. Each time you complete one, you will unlock the next. Once you complete a milestone, it stays complete even as you change your code. For example, after milestone 2, your program's output will no longer pass the milestone 1 tests. That is okay! Milestone 1 is already complete, and the **Check** button only tests the milestone you currently have selected.

### Notes

* The dictionary is the whole program. You will build a dictionary in milestone 1, and every milestone after that just uses it: looking at every word in it, checking whether a word is in it, and looking up a word's emoji. By the end you will have done all of the main things you can do with a dictionary.
* You can copy and paste emoji from here when you test: 🍕 ❤️ 🐱 🐶 ☀️ 😊 ☕ 🎵 🌧️ 🚀


### Above and beyond

Once all four milestones are complete, here are some ways to make your translator your own. Pick one, or invent your own!

* **Ask the AI.** When a word has no emoji, use call_gpt to ask for one, and add it to your dictionary. Next time that word comes up, it is already in the dictionary, so you don't have to ask again.

* **Translate it back.** Build a second dictionary that goes the other way, from each emoji to its word. Then let the user type a message in emoji and translate it back into words.

* **Punctuation.** Right now pizza! doesn't turn into 🍕, because pizza! is not in the dictionary. Fix that, so the punctuation stays in the sentence.

* **Emoji quiz.** Show the user one emoji at a time from the dictionary and ask what word it stands for. Keep score. It is more fun if a friend builds the dictionary!

* **Your favorite emoji.** Count how many times each emoji is used across all the sentences, and when the user is done, print the one that was used the most.

## Milestones

### Milestone 1 of 4
### 1. Build the Dictionary
Write a function `build_emoji_dict()` that asks the user for words and their emoji, and returns a dictionary from each word to its emoji.

* Start with an empty dictionary.
* Ask for a word. Then ask for that word's emoji, and add the pair to your dictionary.
* Keep going until the user presses enter without typing a word. Then return the dictionary.
* Lowercase each word, so that `Pizza` and `pizza` are the same word.

Print how many words the dictionary has. You can do that inside `build_emoji_dict` or in `main`. len works on dictionaries just like it works on lists. Your starter code already prints the welcome message, and when you are ready to test, uncomment the line in `main` that calls `build_emoji_dict()`.

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
```

### Milestone 2 of 4
### 2. Show the Dictionary
Write a function `print_emoji_dict(emoji_dict)` that prints every word in the dictionary next to its emoji. When you loop over a dictionary with for, you get its keys one at a time. Once you have a key, you can look up its value.



Call `print_emoji_dict in main`, right after you print how many words there are. **Important note**: make sure that you returned your dictionary from `build_emoji_dict()` so that you can pass it into `print_emoji_dict(emoji_dict)`!

Here is example output:

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
```

Now try something: type pizza twice, with a different emoji each time. How many words does your dictionary have? What emoji does pizza have? A dictionary can only have each key once, so the second emoji replaces the first. You don't need to write any code for this. It just works!

### Milestone 3 of 4
### 3. Translate a Sentence
Now for the fun part. Write a function `translate(sentence, emoji_dict)` that returns the sentence with every word that has an emoji swapped for its emoji.

* Start with an empty string for the result.
* Loop over the words in the sentence. `sentence.split()` gives you the words as a list.
* If a word is in the dictionary, add its emoji to the result. If it is not, add the word itself. Either way, put a space after it. A space at the end of the line is fine, since the checker ignores it.
* The words in your dictionary are lowercase, but the user might type Pizza. Lowercase each word before you check whether it is in the dictionary. If it has no emoji, add it to the result the way the user typed it.

In `main`, after you print the dictionary, ask for one sentence and print its translation. Here is an example run:

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
Enter a sentence: I love Pizza
I ❤️ 🍕
```

### Milestone 4 of 4 

### 4. Keep Translating

One sentence is not enough. Change main so that it keeps asking for sentences and printing their translations until the user presses enter without typing anything.

Here is example output:

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
Enter a sentence: I love pizza
I ❤️ 🍕
Enter a sentence: my cat loves tea
my 🐱 loves tea
Enter a sentence:
```

Look at your main function. It doesn't say anything about how to build a dictionary, print one, or translate a sentence. Those jobs are each tucked inside a function with a name that says what it does, which is beautiful!


---

### Milestone 1: How it works

1. `emoji_dict = {}` creates an empty dictionary.
2. `input("Word: ")` asks the user for a word.
3. `while word != ""` continues until the user presses Enter.
4. `word.lower()` converts the word to lowercase.
5. `emoji_dict[word] = emoji` stores the word and emoji.
6. `len(emoji_dict)` counts the number of unique words.
7. `return emoji_dict` returns the completed dictionary.

---

### Milestone 2:  What's new?

We added this function:

```python
def print_emoji_dict(emoji_dict):
    for word in emoji_dict:
        print(f"{word}: {emoji_dict[word]}")
```

- `for word in emoji_dict` loops through every dictionary key.
- `emoji_dict[word]` retrieves the emoji associated with that word.
- `print()` displays the word and its emoji.

#### Important concept: Duplicate keys

Suppose you enter:

```
Word: pizza
Emoji for pizza: 🍕
Word: pizza
Emoji for pizza: 🍔
```

Your dictionary will contain:

```python
{"pizza": "🍔"}
```

It will have 1 word, not 2.

The second emoji replaces the first because dictionary keys must be unique.

**Remember:** A dictionary stores unique keys, and each key points to its current value.

---

### Milestone 3

#### Understanding the new function

The most important part is:

```python
for word in words:
    if word.lower() in emoji_dict:
        result += emoji_dict[word.lower()]
    else:
        result += word

    result += " "
```

Here's what happens with the sentence `"I love Pizza"`:

| Word | Dictionary lookup | Result |
| --- | --- | --- |
| I | Not found | I |
| love | Found | ❤️ |
| Pizza | Found as `pizza` | 🍕 |


Three important things to remember:

1. `.split()` separates a sentence into individual words.
2. `.lower()` makes dictionary lookups case-insensitive.
3. `return result` sends the translated sentence back to whoever called the function.

You're now combining dictionaries, loops, strings, conditions, and functions in one program\!

### Milestone 4

Just need to change the `main()` function so that it uses a `while` loop to keep asking for sentences until the user presses Enter.

#### What's new?
Only this part is new in `main()`:

```python
sentence = input("Enter a sentence: ")

while sentence != "":
    translated = translate(sentence, emoji_dict)
    print(translated)

    sentence = input("Enter a sentence: ")
```

#### How does it work?

1. Ask the user for a sentence.
2. Check whether the sentence is empty.
3. If it isn't empty, translate and print it.
4. Ask for another sentence.
5. Repeat until the user presses Enter.

**Remember:** The `while` loop keeps translating, while `sentence != ""` determines when to stop.


## Answer

```python

def build_emoji_dict():
    emoji_dict = {}

    word = input("Word: ")

    while word != "":
        word = word.lower()
        emoji = input(f"Emoji for {word}: ")

        emoji_dict[word] = emoji

        word = input("Word: ")

    print(f"Words in your dictionary: {len(emoji_dict)}")

    return emoji_dict


def print_emoji_dict(emoji_dict):
    for word in emoji_dict:
        print(f"{word}: {emoji_dict[word]}")


def translate(sentence, emoji_dict):
    result = ""

    words = sentence.split()

    for word in words:
        if word.lower() in emoji_dict:
            result += emoji_dict[word.lower()]
        else:
            result += word

        result += " "

    return result


def main():
    print("Let's build your emoji dictionary! Press enter when you are done.")

    emoji_dict = build_emoji_dict()

    print_emoji_dict(emoji_dict)

    sentence = input("Enter a sentence: ")

    while sentence != "":
        translated = translate(sentence, emoji_dict)
        print(translated)

        sentence = input("Enter a sentence: ")


if __name__ == "__main__":
    main()
```

