## 05 Translation Practice
In this assignment, you'll build a simple language practice tool!

Your program should:

1. Ask the user what **language** they want to practice.
2. Ask the user to enter a **word in English**.
3. Ask the user to translate the word in their chosen language.
4. Use `call_gpt` to use GPT to translate the English word.
5. Use an **if statement** to compare the user's translation with GPT's translation.
6. If they match, celebrate! Otherwise, tell the user what translation GPT gave.

Here is example output from running this program twice:

```
% python main.py
What language do you want to practice? Spanish
Type the word in English: apple
Type the word in Spanish: manzana
Wahoo! You and GPT agreed on the translation.
% python main.py
What language do you want to practice? French
Type the word in English: Hello
Type the word in French: Aloha
Oh no! GPT said that the translation is Bonjour
```

Remember: You can use `.lower()` on both translations before comparing them so that capitalization doesn't affect the result.

---
### Code

```python
from ai import call_gpt

def main():
    # Prompt the user to enter the language, word, and translation
    language = input("What language do you want to practice? ")
    english_word = input("Type the word in English: ")
    user_translation = input(f"Type the word in {language}: ")

    # Use GPT to translate the word
    gpt_translation = call_gpt(f"Translate the word {english_word} to {language}. Return the translation only.")

    # Convert the translations to lowercase for comparison
    gpt_answer = gpt_translation.lower()
    user_answer = user_translation.lower()
    if gpt_answer == user_answer:
        print("Wahoo! You and GPT agreed on the translation.")
    else:
        print(f"Oh no! GPT said that the translation is {gpt_translation}")

if __name__ == "__main__":
    main()
```

