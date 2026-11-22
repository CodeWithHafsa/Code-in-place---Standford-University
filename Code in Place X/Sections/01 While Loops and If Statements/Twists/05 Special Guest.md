## Special Guest

*A twist on Guess My Animal from week 1 section. Try it yourself, then compare your code with the solution.*

Ask for the player's name at the start. If it's your section leader's name, roll out the red carpet! Everyone else gets a normal welcome. Make it work even if they type the name in capital letters.

Here is a sample run, where the section leader is named Sam:

```
What's your name? SAM
Welcome, VIP SAM! The red carpet is ready for you.
I am thinking of an animal.
Can you guess what animal it is?
Ask me a yes or no question: is it a zebra?
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

* `name = input("What's your name? ")` asks for the player's name first.
* `name.lower() == "sam"` checks the name without worrying about capitalization.
* The `if` branch gives Sam the VIP welcome; the `else` branch welcomes everyone else normally.

### Answer

```python
from animal import get_random_animal
from ai import call_gpt

def main():
    # Choose a random animal
    animal = get_random_animal()
    
    # Ask for the player's name
    name = input("What's your name? ")

    # Roll out the red carpet for the section leader
    if name.lower() == "sam":
        print(f"Welcome, VIP {name}! The red carpet is ready for you.")
    else:
        print(f"Welcome, {name}!")

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