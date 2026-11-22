## Translation Practice, Again

In the last lesson you built a language practice tool that quizzed the user on a single word. Now use a while loop to keep quizzing them until they want to stop.

Your program should:
1. Ask the user what language they want to practice.
2. Ask them for an English word, or `done` to quit.
3. As long as the word is **not** `done`: ask for their translation, use GPT to translate the same word, compare the two with an if statement, and then ask for the next word.
4. When they type `done`, print a goodbye message.

Here is example output from running this program:

```
What language do you want to practice? Spanish
Type a word in English, or done to quit: apple
Type the word in Spanish: manzana
Wahoo! You and GPT agreed on the translation.
Type a word in English, or done to quit: hello
Type the word in Spanish: Aloha
Oh no! GPT said that the translation is Hola
Type a word in English, or done to quit: done
Nice practicing with you!
```

Remember to call `.lower()` on both translations before comparing them, so capitalization does not change the result.

---
### Code

```python
from ai import call_gpt

def main():
    # Ask which language to practice
    language = input("What language do you want to practice? ")

    # Ask for the first word, or done to quit
    english_word = input("Type a word in English, or done to quit: ")

    while english_word != "done":
        # Get the user's translation, then GPT's translation
        user_translation = input(f"Type the word in {language}: ")
        gpt_translation = call_gpt(f"Translate the word {english_word} to {language}. Return the translation only.")

        # Compare them in lowercase so capitalization doesn't matter
        if user_translation.lower() == gpt_translation.lower():
            print("Wahoo! You and GPT agreed on the translation.")
        else:
            print(f"Oh no! GPT said that the translation is {gpt_translation}")

        # Ask for the next word, or done to quit
        english_word = input("Type a word in English, or done to quit: ")

    print("Nice practicing with you!")

if __name__ == "__main__":
    main()
```