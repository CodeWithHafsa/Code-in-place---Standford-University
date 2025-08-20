## Assignment
Code in Place is not only massive, but also super diverse! We serve a lot of students worldwide who speak many different languages. To practice our language skills, we want to make a helpful tool to help us study Spanish!

Write a program that loops over a dictionary of words and quizzes the user for their corresponding Spanish translations, keeping count of how many the user gets correct! Separate each question and answer with a blank line to help with visual clarity.

Here's a sample run of the program (user input is in blue):

```
What is the Spanish translation for hello? hola
That is correct!

What is the Spanish translation for dog? gato
That is incorrect, the Spanish translation for dog is perro.

... (quizzes user on the rest of the words)
That is correct!

You got 6/8 words correct, come study again soon!
```

### Given Code
```python
def main():
    translations = {
        "hello": "hola",
        "dog": "perro",
        "cat": "gato",
        "well": "bien",
        "us": "nos",
        "nothing": "nada",
        "house": "casa",
        "time": "tiempo"
    }
    
    pass  # Delete this line and write your code here! :)

# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Answer
```python
def main():
    translations = {
        "hello": "hola",
        "dog": "perro",
        "cat": "gato",
        "well": "bien",
        "us": "nos",
        "nothing": "nada",
        "house": "casa",
        "time": "tiempo"
    }
    
    correct_count = 0
    total_words = len(translations)

    for english, spanish in translations.items():
        answer = input(f"What is the Spanish translation for {english}?").strip().lower()
        
        if answer == spanish:
            print("That is correct!")
            correct_count += 1
        else:
            print(f"That is incorrect, the Spanish translation for {english} is {spanish}.")
        
        print()  # Blank line for clarity

    print(f"You got {correct_count}/{total_words} words correct, come study again soon!")

if __name__ == '__main__':
    main()
```