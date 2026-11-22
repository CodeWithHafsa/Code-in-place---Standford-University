## Crash Landing

*A twist on Guess My Animal from week 1 section. Try it yourself, then compare your code with the solution.*

The game crashes right after the first question! Run it, read the error message, and get it flying again.

Here is what happens now:
```
I am thinking of an animal.
Can you guess what animal it is?
Ask me a yes or no question: is it big?
UnboundLocalError: cannot access local variable 'gpt_response' where it is not associated with a value
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
The error happens because `gpt_response` is used in the `while` loop before it has been assigned a value.

**Fix:** Add the prompt and `call_gpt(prompt)` right after the first question, before the `while` loop.

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
        question = input("Ask me a yes or no question: ")

        # Use GPT to get the response
        prompt = f"We are playing twenty questions and the answer is {animal}. The user has asked the following yes or no question: {question}. Please respond with exactly Yes, No, or Correct if they guess the animal exactly. Do not say anything else."
        gpt_response = call_gpt(prompt)
    
    print("Correct!")

if __name__ == "__main__":
    main()
```