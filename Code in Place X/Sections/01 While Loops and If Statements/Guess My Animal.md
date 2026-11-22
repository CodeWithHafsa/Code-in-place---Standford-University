# Guess My Animal
### Assignment
In this assignment, you'll implement a fun guessing game called **Guess My Animal**. The program will first randomly pick an animal, and then the user gets to guess which animal it is by asking yes or no questions. You can play around with the prompt to call_gpt to get the best experience for the user and to get practice with prompt engineering! 

Your program should:
* Start by selecting a random animal using the function `get_random_animal()`.
* Let the user ask yes-or-no questions about the animal.
* Use the `call_gpt()` function to respond yes or no to each question.
* End when the user guesses correctly.

Two functions are already provided and imported for you:
* `get_random_animal()` – returns a string with the name of a random animal
* `call_gpt()` – sends your prompt to an AI model and returns its response. You can think of it as asking an AI model a question from inside your Python program. Learn more about call_gpt here. 

Here’s a sample run of the game:

```
I am thinking of an animal.
Can you guess what animal it is?
Ask me a yes or no question: does it live on land?
Yes.
Ask me a yes or no question: is it a mammal?
Yes.
Ask me a yes or no question: is it commonly kept as a pet?
No.
```

---

### Answer

```python
from animal import get_random_animal
from ai import call_gpt


def main():
    animal = get_random_animal()

    print("I am thinking of an animal.")
    print("Can you guess what animal it is?")

    while True:
        question = input("Ask me a yes or no question: ")

        if question.lower() == animal.lower():
            print("Correct!")
            break

        prompt = f"""
I am thinking of the animal: {animal}.
The user is trying to guess the animal.
Answer the user's question with only "Yes." or "No.".
User's question: {question}
"""

        answer = call_gpt(prompt)
        print(answer)


if __name__ == "__main__":
    main()
```