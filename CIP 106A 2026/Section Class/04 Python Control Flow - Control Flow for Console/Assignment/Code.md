### Information Gathered
* Loop that too FOR Loop
   * Two numbers gathered range (1-100 inclusive)
   * One number will be computer input - Computer is out of option
   * The other one will be our
   * Computer number hidden, Our number visible on terminal
   * make a guess - higher or lower
   * Conditional logic
        - if guess matches the truth then you get a point

* Computer number will be generated first
* After Computer users number will be generated


## Given Code

```python
import random

NUM_ROUNDS = 5

def main():
    print("Welcome to the High-Low Game!")
    print('--------------------------------')
    
    # TODO: Write your code here!!! :)
    # NOTE: For the autograder to work, you must generate the
    # COMPUTER's number FIRST, then the user's

if __name__ == "__main__":
    main()
```

## Answer

### Milestone # 1

```python
import random


def main():
    print("Welcome to the High-Low Game!")
    print("--------------------------------")

    # Generate computer number first
    computer_num = random.randint(1, 100)

    # Generate user number second
    user_num = random.randint(1, 100)

    # Print both numbers
    print(f"The computer's number is {computer_num}")
    print(f"Your number is {user_num}")


if __name__ == "__main__":
    main()
```

---
### Milestone # 2

```python
import random


def main():
    print("Welcome to the High-Low Game!")
    print("--------------------------------")

    # Generate random numbers
    computer_num = random.randint(1, 100)
    user_num = random.randint(1, 100)

    # Print the numbers
    print(f"The computer's number is {computer_num}")
    print(f"Your number is {user_num}")

    # Get user choice
    choice = input(
        "Do you think your number is higher or lower than the computer's?: "
    )

if __name__ == "__main__":
    main()
```
---

### Milestone # 3

```python
import random


def main():
    print("Welcome to the High-Low Game!")
    print("--------------------------------")

    # Generate random numbers
    computer_num = random.randint(1, 100)
    user_num = random.randint(1, 100)

    # Print numbers
    print(f"The computer's number is {computer_num}")
    print(f"Your number is {user_num}")

    # Get user choice
    choice = input(
        "Do you think your number is higher or lower than the computer's?: "
    ).lower()

    # Game logic
    if choice == "higher" and user_num > computer_num:
        print(f"You were right! The computer's number was {computer_num}")

    elif choice == "lower" and user_num < computer_num:
        print(f"You were right! The computer's number was {computer_num}")

    else:
        print(f"Aww, that's incorrect. The computer's number was {computer_num}")


if __name__ == "__main__":
    main()
```

---

### Milestone # 4

```python
import random

# Number of rounds
NUM_ROUNDS = 5


def main():
    print("Welcome to the High-Low Game!")
    print("--------------------------------")

    # Play multiple rounds
    for round_num in range(1, NUM_ROUNDS + 1):

        print(f"Round {round_num}")

        # Generate random numbers
        computer_num = random.randint(1, 100)
        user_num = random.randint(1, 100)

        # Show user's number
        print(f"Your number is {user_num}")

        # Get user choice
        choice = input(
            "Do you think your number is higher or lower than the computer's?: "
        ).lower()

        # Check if user is correct
        if choice == "higher" and user_num > computer_num:
            print(f"You were right! The computer's number was {computer_num}")

        elif choice == "lower" and user_num < computer_num:
            print(f"You were right! The computer's number was {computer_num}")

        else:
            print(f"Aww, that's incorrect. The computer's number was {computer_num}")

        # Blank line between rounds
        print()


if __name__ == "__main__":
    main()
```

--- 
### Milestone # 5

```python
import random

# Number of rounds
NUM_ROUNDS = 5


def main():
    print("Welcome to the High-Low Game!")
    print("--------------------------------")

    # Keep track of score
    score = 0

    # Play multiple rounds
    for round_num in range(1, NUM_ROUNDS + 1):

        print(f"Round {round_num}")

        # Generate random numbers
        computer_num = random.randint(1, 100)
        user_num = random.randint(1, 100)

        # Show user's number
        print(f"Your number is {user_num}")

        # Get user choice
        choice = input(
            "Do you think your number is higher or lower than the computer's?: "
        ).lower()

        # Check if the user is correct
        if choice == "higher" and user_num > computer_num:
            print(f"You were right! The computer's number was {computer_num}")
            score += 1

        elif choice == "lower" and user_num < computer_num:
            print(f"You were right! The computer's number was {computer_num}")
            score += 1

        else:
            print(f"Aww, that's incorrect. The computer's number was {computer_num}")

        # Print updated score
        print(f"Your score is now {score}")

        # Blank line between rounds
        print()

    # Final message
    print("Thanks for playing!")


if __name__ == "__main__":
    main()
```

---


### Extension 1 & 2 

```python
"""
File: high_low.py
-----------------
This program plays a number guessing game called High-Low with the user.
It generates random target values, validates input choices, manages scores,
and outputs performance feedback upon completion.
"""

import random

# Global constant for the number of rounds to play
NUM_ROUNDS = 5


def main():
    print("Welcome to the High-Low Game!")
    print('--------------------------------')
    
    score = 0
    
    for round_num in range(1, NUM_ROUNDS + 1):
        print(f"Round {round_num}")
        
        # Core Constraint: Generate computer's number first, then user's number
        computer_num = random.randint(1, 100)
        user_num = random.randint(1, 100)
        
        print(f"Your number is {user_num}")
        
        # Extension 1: Safe user input processing loop
        choice = input("Do you think your number is higher or lower than the computer's?: ")
        while choice != "higher" and choice != "lower":
            choice = input("Please enter either higher or lower: ")
        
        # Round logic scoring evaluation (Ties go to the computer)
        if choice == "higher" and user_num > computer_num:
            print(f"You were right! The computer's number was {computer_num}")
            score += 1
        elif choice == "lower" and user_num < computer_num:
            print(f"You were right! The computer's number was {computer_num}")
            score += 1
        else:
            print(f"Aww, that's incorrect. The computer's number was {computer_num}")
            
        print(f"Your score is now {score}")
        print()
        
    print("Thanks for playing!")
    print()
    
    # Extension 2: Conditional performance completion reviews
    if score == NUM_ROUNDS:
        print("Wow! You played perfectly!")
    elif score >= (NUM_ROUNDS // 2):
        print("Good job, you played really well!")
    else:
        print("Better luck next time!")


if __name__ == "__main__":
    main()
```


# Final Code - Answer

```python
import random

# Constant for total rounds
NUM_ROUNDS = 5

"""
1. Generate random numbers for computer and user
2. Ask the user to choose higher or lower
3. Check if the user's guess is correct
4. Repeat the game for 5 rounds
5. Update score and print final message
"""


def main():
    print("Welcome to the High-Low Game!")
    print("--------------------------------")

    # Variable to keep track of score
    score = 0

    # Play the game for 5 rounds
    for round_num in range(1, NUM_ROUNDS + 1):

        print(f"Round {round_num}")

# Loop through all rounds from 1 to NUM_ROUNDS
# range(1, NUM_ROUNDS + 1) starts from 1
# ends at NUM_ROUNDS
# round_num stores the current round number (1, 2, 3, 4, 5)

        # 1. Generate random numbers
        computer_num = random.randint(1, 100)
        user_num = random.randint(1, 100)

        print(f"Your number is {user_num}")

        # 2. Ask the user for input
        choice = input(
            "Do you think your number is higher or lower than the computer's?: "
        ).lower()

        # 3. Check if the user is correct
        if choice == "higher" and user_num > computer_num:
            print(f"You were right! The computer's number was {computer_num}")
            score += 1

        elif choice == "lower" and user_num < computer_num:
            print(f"You were right! The computer's number was {computer_num}")
            score += 1

        else:
            print(f"Aww, that's incorrect. The computer's number was {computer_num}")

        # 5. Display updated score
        print(f"Your score is now {score}")
        print()

    # Final message
    print("Thanks for playing!")


if __name__ == "__main__":
    main()
```