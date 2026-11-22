## Roll Dice
Simulate rolling two dice, and print the result of each roll as well as the total.

```python
"""
File: rolldice.py
------------------
Simulate rolling two dice, and print the result of each
roll as well as the total.
"""

# Import randint from the random library, which lets us simulate random things like dice!
from random import randint

# Number of sides on each die to roll
NUM_SIDES = 6

def main():
    # Roll die
    die1 = randint(1, NUM_SIDES)
    die2 = randint(1, NUM_SIDES)

    # Get their total
    total = die1 + die2

    # Print out the results
    print("Dice have", NUM_SIDES, "sides each.")
    print("First die:", die1)
    print("Second die:", die2)
    print("Total of two dice:", total)


# This provided line is required at the end of a Python file
# to call the main() function.
if __name__ == '__main__':
    main()
```