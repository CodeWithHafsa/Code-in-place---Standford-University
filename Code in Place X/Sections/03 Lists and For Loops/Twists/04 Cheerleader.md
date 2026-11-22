## Cheerleader

*A twist on Wordle from your section. Try it yourself, then compare your code with the solution.*

Wordle could use some team spirit! After each wrong guess, cheer the player on with a different message every time.

Use these cheers, in this order, one for each wrong guess:

1. Nice start!
2. Keep going!
3. You're getting closer!
4. Don't give up!
5. One guess left!
6. Good try!

Here is a sample run:

```
Welcome to Wordle!
Enter your guess: crazy
Result: [c] r (a) z [y]
Nice start!
Enter your guess: corny
Result: [c] o r (n) [y]
Keep going!
Enter your guess: candy
Result: [c] [a] [n] [d] [y]
Congratulations! You guessed the word in 3 tries!
```

### Given Code

```python
from words import get_random_word

NUM_ATTEMPTS = 6

def main():
    # Print welcome message
    print("Welcome to Wordle!")

    # Set the secret word
    secret_word = get_random_word()

    # Let the player guess up to NUM_ATTEMPTS
    for attempt in range(NUM_ATTEMPTS):

        # Get the guess from the user
        guess = input("Enter your guess: ").lower()
        while len(guess) != 5:
            print("Please enter a 5-letter word.")
            guess = input("Enter your guess: ").lower()

        # Initialize remaining_letters to contain
        # the remaining letters in the secret word
        remaining_letters = []
        for i in range(5):
            remaining_letters.append(secret_word[i])

        # Compare the guess to the secret word
        result = []
        for i in range(5):
            if secret_word[i] == guess[i]:
                # It's a match!
                result.append("G")

                # Update the remaining letters
                remaining_letters.remove(secret_word[i])
            else:
                # Not an exact match
                result.append("B")

        # Look for the yellow letters
        for i in range(5):
            # Look for letters that were not exact matches
            if result[i] == "B":
                # Check if the guessed letter is somewhere else in the secret word
                if guess[i] in remaining_letters:
                    result[i] = "Y"
                    remaining_letters.remove(guess[i])

        # Build a string from the list and print the result
        result_str = "Result:"
        for i in range(5):
            # Append each letter using an f string
            if result[i] == "G":
                # Put the letter in brackets
                result_str = f"{result_str} [{guess[i]}]"

            if result[i] == "Y":
                # Put the letter in parentheses
                result_str = f"{result_str} ({guess[i]})"

            if result[i] == "B":
                result_str = f"{result_str} {guess[i]}"

        # Print out the result string
        print(result_str)

        # Check if they got it correct
        if secret_word == guess:
            print(f"Congratulations! You guessed the word in {attempt + 1} tries!")
            break

        # Check if it's their last attempt
        if attempt == NUM_ATTEMPTS - 1:
            print(f"Better luck next time! The correct word was '{secret_word}'.")

if __name__ == "__main__":
    main()
```

#### What changed?

1. Create a list of cheer messages (add before the `main()` function):
   python
   ```python
   cheers = [
       "Nice start!",
       "Keep going!",
       "You're getting closer!",
       "Don't give up!",
       "One guess left!",
       "Good try!"
   ]
   ```
2. Print a different cheer after each wrong guess.
   Add this code after the congratulations check (`if secret_word == guess:` block), but before the last-attempt condition:
   python
   ```python
   print(cheers[attempt])
   ```
3. Keep the rest of your code unchanged.

Why?

- `cheers` stores all six messages in order.
- `attempt` starts at 0, so `cheers[attempt]` prints the correct message for each guess.
- The cheer appears only when the guess is wrong because the correct guess uses `break` before reaching the cheer.

### Answer

```python
from words import get_random_word

NUM_ATTEMPTS = 6

# One cheer for each guess
CHEERS = ["Nice start!", "Keep going!", "You're getting closer!", "Don't give up!", "One guess left!", "Good try!"]

def main():
    # Print welcome message
    print("Welcome to Wordle!")

    # Set the secret word
    secret_word = get_random_word()

    # Let the player guess up to NUM_ATTEMPTS
    for attempt in range(NUM_ATTEMPTS):

        # Get the guess from the user
        guess = input("Enter your guess: ").lower()
        while len(guess) != 5:
            print("Please enter a 5-letter word.")
            guess = input("Enter your guess: ").lower()

        # Initialize remaining_letters to contain
        # the remaining letters in the secret word
        remaining_letters = []
        for i in range(5):
            remaining_letters.append(secret_word[i])

        # Compare the guess to the secret word
        result = []
        for i in range(5):
            if secret_word[i] == guess[i]:
                # It's a match!
                result.append("G")

                # Update the remaining letters
                remaining_letters.remove(secret_word[i])
            else:
                # Not an exact match
                result.append("B")

        # Look for the yellow letters
        for i in range(5):
            # Look for letters that were not exact matches
            if result[i] == "B":
                # Check if the guessed letter is somewhere else in the secret word
                if guess[i] in remaining_letters:
                    result[i] = "Y"
                    remaining_letters.remove(guess[i])

        # Build a string from the list and print the result
        result_str = "Result:"
        for i in range(5):
            # Append each letter using an f string
            if result[i] == "G":
                # Put the letter in brackets
                result_str = f"{result_str} [{guess[i]}]"

            if result[i] == "Y":
                # Put the letter in parentheses
                result_str = f"{result_str} ({guess[i]})"

            if result[i] == "B":
                result_str = f"{result_str} {guess[i]}"

        # Print out the result string
        print(result_str)

        # Cheer the player on after a wrong guess
        if guess != secret_word:
            print(CHEERS[attempt])

        # Check if they got it correct
        if secret_word == guess:
            print(f"Congratulations! You guessed the word in {attempt + 1} tries!")
            break

        # Check if it's their last attempt
        if attempt == NUM_ATTEMPTS - 1:
            print(f"Better luck next time! The correct word was '{secret_word}'.")

if __name__ == "__main__":
    main()
```
