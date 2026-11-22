## No Repeats

*A twist on Wordle from your section. Try it yourself, then compare your code with the solution.*

Guessing the same word twice wastes a turn. If the player repeats a guess, tell them and let them try again, without using up a guess.

Here is a sample run:

```
Welcome to Wordle!
Enter your guess: crazy
Result: [c] r (a) z [y]
Enter your guess: crazy
You already guessed that one!
Enter your guess: corny
Result: [c] o r (n) [y]
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

#### What Changed?
1. Create an empty list to store previous guesses (add before the `for attempt` loop):
   ```python
   previous_guesses = []
   ```
2. Check if the player has already guessed the word.\
   Add this code after getting the guess and checking its length:
   ```python
   while guess in previous_guesses:
       print("You already guessed that one!")
       guess = input("Enter your guess: ").lower()
       while len(guess) != 5:
           print("Please enter a 5-letter word.")
           guess = input("Enter your guess: ").lower()
   ```
3. Store each new guess (add after the duplicate-checking loop):
   ```python
   previous_guesses.append(guess)
   ```
4. Keep the rest of your code unchanged.

Why?

- `previous_guesses` remembers all guesses.
- `while guess in previous_guesses` checks for repeated guesses.
- If the guess is repeated, the player must enter another word.
- The `for` loop doesn't restart, so repeated guesses don't use up an attempt.

### Answer

```python
from words import get_random_word

NUM_ATTEMPTS = 6

def main():
    # Print welcome message
    print("Welcome to Wordle!")

    # Set the secret word
    secret_word = get_random_word()

    # Every guess the player has made so far
    past_guesses = []

    # Let the player guess up to NUM_ATTEMPTS
    for attempt in range(NUM_ATTEMPTS):

        # Get the guess from the user
        guess = input("Enter your guess: ").lower()
        while guess in past_guesses:
            print("You already guessed that one!")
            guess = input("Enter your guess: ").lower()
        while len(guess) != 5:
            print("Please enter a 5-letter word.")
            guess = input("Enter your guess: ").lower()
        past_guesses.append(guess)

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
