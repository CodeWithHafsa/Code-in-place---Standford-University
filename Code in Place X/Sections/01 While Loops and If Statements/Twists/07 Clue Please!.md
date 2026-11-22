## Clue Please!

*A twist on Guess My Animal from week 1 section. Try it yourself, then compare your code with the solution.*

After the first question, let the player type hint to get a clue about the animal instead of a yes or no answer.

Here is a sample run:

```
I am thinking of an animal.
Can you guess what animal it is?
Ask me a yes or no question: can it fly?
No.
Ask me a yes or no question, or type hint: hint
It has black and white stripes.
Ask me a yes or no question, or type hint: is it a zebra?
Correct!
```

### Given Code

```python
from animal import get_random_animal
from ai import call_gpt

def main():
    # Choose a random animal
    animal = get_random_animal()
    
    # Print the initial message to the user
    print("I am thinking of an animal.")
    print("Can you guess what animal it is?")

    # Get their first guess
    question = input("Ask me a yes or no question: ")

    # Use GPT to get a yes, no, or correct
    prompt = f"We are playing twenty questions and the answer is {animal}. The user has asked the following yes or no question: {question}. Please respond with exactly Yes, No, or Correct if they guess the animal exactly. Do not say anything else."
    gpt_response = call_gpt(prompt)
    
    # Keep letting the user guess as long as its not correct
    while gpt_response != "Correct":
        # Output GPT's response
        print(f"{gpt_response}.")

        # Get the next question
        question = input("Ask me a yes or no question: ")

        # Use GPT to get the response
        prompt = f"We are playing twenty questions and the answer is {animal}. The user has asked the following yes or no question: {question}. Please respond with exactly Yes, No, or Correct if they guess the animal exactly. Do not say anything else."
        gpt_response = call_gpt(prompt)
    
    print("Correct!")

if __name__ == "__main__":
    main()
```

#### Changes made

You can add an `if `statement inside the loop to check whether the player typed `"hint"`. If they did, ask GPT to provide a clue about the animal. Otherwise, process the question as usual.

* **Hint option:** The input prompt now tells the player they can type `hint`.
* **Check for hints:** if `question.lower() == "hint":` recognizes `hint`, `HINT`, or `Hint`.
* **Generate a clue:** GPT provides a short clue without revealing the animal's name.
* **Continue the game:** After showing the hint, the loop asks for another question. The previous GPT response remains unchanged until the player asks a new yes/no question.

### Answer

```python
from animal import get_random_animal
from ai import call_gpt

def main():
    # Choose a random animal
    animal = get_random_animal()
    
    # Print the initial message to the user
    print("I am thinking of an animal.")
    print("Can you guess what animal it is?")

    # Get their first guess
    question = input("Ask me a yes or no question: ")

    # Use GPT to get a yes, no, or correct
    prompt = f"We are playing twenty questions and the answer is {animal}. The user has asked the following yes or no question: {question}. Please respond with exactly Yes, No, or Correct if they guess the animal exactly. Do not say anything else."
    gpt_response = call_gpt(prompt)
    
    # Keep letting the user guess as long as its not correct
    while gpt_response != "Correct":
        # Output GPT's response
        print(f"{gpt_response}.")

        # Get the next question
        question = input("Ask me a yes or no question, or type hint: ")

        # Use GPT to get a clue or the response
        if question == "hint":
            prompt = f"Give a short clue about a {animal} in a few words, without saying what it is. Do not end with a period."
        else:
            prompt = f"We are playing twenty questions and the answer is {animal}. The user has asked the following yes or no question: {question}. Please respond with exactly Yes, No, or Correct if they guess the animal exactly. Do not say anything else."
        gpt_response = call_gpt(prompt)
    
    print("Correct!")

if __name__ == "__main__":
    main()
```