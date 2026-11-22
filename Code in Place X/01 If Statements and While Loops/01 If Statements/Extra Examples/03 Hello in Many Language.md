## 03 Hello in Many Language

Say hello to a user in many different languages!

Start with a variable called `language` that holds one language name. Then write a separate if statement for each language, so that only the matching greeting prints:
1. English → Welcome!
2. Spanish → ¡Bienvenido!
3. French → Bienvenue!
4. Italian → Benvenuto!

Here is the output when language is "French":
```
Bienvenue!
```

This program uses four separate if statements rather than one if/else, because there are four different things to check. Try changing language and running it again.

---
### Code

```python
def main():
    language = "French"

    if language == "English":
        print("Welcome!")

    if language == "Spanish":
        print("¡Bienvenido!")

    if language == "French":
        print("Bienvenue!")

    if language == "Italian":
        print("Benvenuto!")

if __name__ == "__main__":
    main()
```