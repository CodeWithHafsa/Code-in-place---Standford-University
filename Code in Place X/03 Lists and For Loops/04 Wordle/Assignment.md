## Assignment

>About this assignment

In this assignment you will build the game [Wordle!](https://www.nytimes.com/games/wordle/index.html)

The goal of Wordle is to guess a secret 5-letter word. The player has 6 guesses. After each guess, every letter gets feedback:
* **Right letter, right place:** wrapped in brackets, like [a]
* **Right letter, wrong place:** wrapped in parentheses, like (b)
* **Not in the word at all:** left alone, like c

Here is an example game:
```
Welcome to Wordle!
Enter your guess: crazy
Result: [c] r (a) z [y]
Enter your guess: corny
Result: [c] o r (n) [y]
Enter your guess: candy
Result: [c] [a] [n] [d] [y]
Congratulations! You guessed the word in 3 tries!
```

This is the biggest program you have written so far, so we’ve broken it into five milestones. To complete a milestone, pass its tests. Each time you complete one, you’ll unlock the next.

Once you complete a milestone, it stays complete even as you change your code. For example, after milestone 3, your program’s output will no longer pass the milestone 1 tests. That’s okay! Milestone 1 is already complete, and the Check button only tests the milestone you currently have selected.

Until milestone 5, keep the secret word as `"candy"` so you can predict what your program should print.

---

Milestone 1 of 5

### 1. Exact Matches
Write a program that:
1. Prints Welcome to Wordle!
2. Sets the secret word to "candy"
3. Asks the user to enter a guess. For now, you may assume that they will always enter a 5 letter guess.
4. Compares the guess to the secret word one letter at a time, building a list as it goes: add "G" when the letter matches the letter in the **same position**, and "B" otherwise.
5. Builds a string from that list and prints it out. A space at the end of the line is fine, since the checker ignores it.

Here is an example output:

```
Welcome to Wordle!
Enter your guess: crazy
Result: G B B B G
```

Both crazy and "candy" have c first and y last, so those two are G. Everything else is B for now.

#### Answer

```python
from words import get_random_word

NUM_ATTEMPTS = 6

def main():
    print("Welcome to Wordle!")
    secret_word = "candy"

    guess = input("Enter your guess: ")

    result = []
    for i in range(len(secret_word)):
        if guess[i] == secret_word[i]:
            result.append("G")
        else:
            result.append("B")

    print("Result:", " ".join(result))

if __name__ == "__main__":
    main()
```

### 2. Yellow Matches

In this next milestone, you will build on your solution from milestone 1, and mark the letters that are in the secret word but in the **wrong place**, using "Y".

For example, look at the following output:

```
Welcome to Wordle!
Enter your guess: dance
Result: Y G G Y B
```

Here's how to implement this:

1. Create a second list called `remaining_letters`. You will use this list to keep track of all of the letters that have not been matched yet. Start by adding all of the letters of the secret word to it.

2. Find the exact matches using your same loop as from milestone 1, but modify it to remove each matched letter out of `remaining_letters` as you go.

3. After that loop finishes, write a second loop. For each letter that is still marked B, look for it in remaining_letters. If it's there, mark it "Y" and remove that letter from remaining_letters. This has to be a separate loop. If you look for Y letters inside the first loop, an early letter can use up a match that a later letter needs for its G.

The key is to keep track of the remaining letters! Try guessing daddy against "candy": the answer is B G B G G, because "candy" has only one d and the exact match already claimed it. Without remaining_letters you would light up all three.

---
For Milestone 2, use remaining_letters to track which letters in "candy" haven't already been matched. 
* First find all green (G) matches, 
* Then check the remaining B letters for yellow (Y) matches.

---

#### Answer

```python

from words import get_random_word

NUM_ATTEMPTS = 6

def main():
    print("Welcome to Wordle!")
    secret_word = "candy"

    guess = input("Enter your guess: ")

    result = []
    remaining_letters = list(secret_word)

    # First, find exact matches (G)
    for i in range(len(secret_word)):
        if guess[i] == secret_word[i]:
            result.append("G")
            remaining_letters.remove(guess[i])
        else:
            result.append("B")

    # Next, find letters in the wrong position (Y)
    for i in range(len(secret_word)):
        if result[i] == "B" and guess[i] in remaining_letters:
            result[i] = "Y"
            remaining_letters.remove(guess[i])

    print("Result:", " ".join(result))

if __name__ == "__main__":
    main()
```

### 3. Format the Output

Use the list of marks to print something a person would actually want to look at:

1. "G" → the letter in brackets, like [a]
2. "Y" → the letter in parentheses, like (b)
3. "B" → just the letter, like c

**Example output:**

```
Welcome to Wordle!
Enter your guess: dance
Result: (d) [a] [n] (c) e
```

Note that the letters come from the guess, not from the secret word.

---
You just need to update the printing section to use the marks in result to format each letter from guess

---

#### Answer

```python

from words import get_random_word

NUM_ATTEMPTS = 6

def main():
    print("Welcome to Wordle!")
    secret_word = "candy"

    guess = input("Enter your guess: ")

    result = []
    remaining_letters = list(secret_word)

    # First, find exact matches (G)
    for i in range(len(secret_word)):
        if guess[i] == secret_word[i]:
            result.append("G")
            remaining_letters.remove(guess[i])
        else:
            result.append("B")

    # Next, find letters in the wrong position (Y)
    for i in range(len(secret_word)):
        if result[i] == "B" and guess[i] in remaining_letters:
            result[i] = "Y"
            remaining_letters.remove(guess[i])

    # Format the result using the letters from the guess
    formatted_result = []
    for i in range(len(guess)):
        if result[i] == "G":
            formatted_result.append("[" + guess[i] + "]")
        elif result[i] == "Y":
            formatted_result.append("(" + guess[i] + ")")
        else:
            formatted_result.append(guess[i])

    print("Result:", " ".join(formatted_result))

if __name__ == "__main__":
    main()
```

### 4. Six Attempts

Turn this into a real game:
1. Let the player guess up to `NUM_ATTEMPTS` times, showing the formatted result after each guess. Use the loop for `attempt` in `range(NUM_ATTEMPTS):` for this.
2. If they guess the word, print `Congratulations!` You guessed the word in `3 tries!` (with the real number of guesses) and end the game.
3. If they use up all six guesses, print `Better luck next time! The correct word was 'candy'.`

**Example output:**

```
Welcome to Wordle!
Enter your guess: crazy
Result: [c] r (a) z [y]
Enter your guess: corny
Result: [c] o r (n) [y]
Enter your guess: candy
Result: [c] [a] [n] [d] [y]
Congratulations! You guessed the word in 3 tries!
```

Hint: Be careful with the count: range starts at 0, so the first guess is attempt 0 and the player made attempt + 1 guesses.

---

The main change is adding a loop that lets the player guess up to six times, checks whether they won, and prints the appropriate ending message.

---

#### Answer

```python

from words import get_random_word

NUM_ATTEMPTS = 6

def main():
    print("Welcome to Wordle!")
    secret_word = "candy"

    for attempt in range(NUM_ATTEMPTS):
        guess = input("Enter your guess: ")

        result = []
        remaining_letters = list(secret_word)

        # Find exact matches (G)
        for i in range(len(secret_word)):
            if guess[i] == secret_word[i]:
                result.append("G")
                remaining_letters.remove(guess[i])
            else:
                result.append("B")

        # Find yellow matches (Y)
        for i in range(len(secret_word)):
            if result[i] == "B" and guess[i] in remaining_letters:
                result[i] = "Y"
                remaining_letters.remove(guess[i])

        # Format the result
        formatted_result = []
        for i in range(len(guess)):
            if result[i] == "G":
                formatted_result.append("[" + guess[i] + "]")
            elif result[i] == "Y":
                formatted_result.append("(" + guess[i] + ")")
            else:
                formatted_result.append(guess[i])

        print("Result:", " ".join(formatted_result))

        # Check whether the player won
        if guess == secret_word:
            print("Congratulations! You guessed the word in",
                  attempt + 1, "tries!")
            return

    # All attempts were used
    print("Better luck next time! The correct word was '" + secret_word + "'.")

if __name__ == "__main__":
    main()
```

### 5. Polish

Great work! Let's add a few finishing touches to make this a fun game to play :)

Do the following:
1. Use `get_random_word()` so the secret word is different every game.
2. Accept any capitalisation by calling `.lower()` on the guess.
3. If the guess is not exactly 5 letters, print `Please enter a 5-letter word.` and ask again. A typo must **not** use up one of the six guesses. You will need a `while` loop **inside** the for loop to do this!

**Example output:**
```
Welcome to Wordle!
Enter your guess: cat
Please enter a 5-letter word.
Enter your guess: PLANT
Result: [p] [l] [a] n t
```

#### Answer


```

from words import get_random_word

NUM_ATTEMPTS = 6

def main():
    print("Welcome to Wordle!")
    secret_word = get_random_word()

    for attempt in range(NUM_ATTEMPTS):
        guess = input("Enter your guess: ").lower()

        # Keep asking until the guess has exactly 5 letters
        while len(guess) != 5:
            print("Please enter a 5-letter word.")
            guess = input("Enter your guess: ").lower()

        result = []
        remaining_letters = list(secret_word)

        # Find exact matches (G)
        for i in range(len(secret_word)):
            if guess[i] == secret_word[i]:
                result.append("G")
                remaining_letters.remove(guess[i])
            else:
                result.append("B")

        # Find yellow matches (Y)
        for i in range(len(secret_word)):
            if result[i] == "B" and guess[i] in remaining_letters:
                result[i] = "Y"
                remaining_letters.remove(guess[i])

        # Format the result
        formatted_result = []
        for i in range(len(guess)):
            if result[i] == "G":
                formatted_result.append("[" + guess[i] + "]")
            elif result[i] == "Y":
                formatted_result.append("(" + guess[i] + ")")
            else:
                formatted_result.append(guess[i])

        print("Result:", " ".join(formatted_result))

        # Check whether the player won
        if guess == secret_word:
            print("Congratulations! You guessed the word in",
                  attempt + 1, "tries!")
            return

    # All attempts were used
    print("Better luck next time! The correct word was '" + secret_word + "'.")

if __name__ == "__main__":
    main()
```