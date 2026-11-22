## Snack Picker

Start with a list of snacks. Print how many snacks there are, the first and last snack, and then pick a random snack for tonight.

Positions start at 0, so the last snack is at position len(snacks) - 1.

#### Answer

```python
from random import randint

def main():
    snacks = ["chips", "popcorn", "grapes", "pretzels", "cookies"]
    print(f"There are {len(snacks)} snacks to choose from.")

    # The last snack is at position len(snacks) - 1, because positions start at 0
    print(f"The first snack is {snacks[0]} and the last is {snacks[len(snacks) - 1]}.")

    # Pick a random position, from 0 up to the last one
    pick = randint(0, len(snacks) - 1)
    print(f"Tonight's snack: {snacks[pick]}")

if __name__ == "__main__":
    main()
```

Output:

```
There are 5 snacks to choose from.
The first snack is chips and the last is cookies.
Tonight's snack: chips
```