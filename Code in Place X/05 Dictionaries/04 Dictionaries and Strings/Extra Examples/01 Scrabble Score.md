## Scrabble Score

In Scrabble, every letter is worth some points, and a word is worth the points of all its letters added up. quiz is worth 22 points: q is 10, u is 1, i is 1 and z is 10.

Your starter code has a dictionary called POINTS that goes from each letter to how many points it is worth, so `POINTS["q"]`is 10.

* Write a function `score(word)` that returns the total points for a word. Loop over the letters in the word and look up each one in `POINTS`.
* In `main`, keep asking for words and printing their scores until the user presses enter without typing anything.

You may assume every word is made of letters only, but they might be capital letters. Every key in `POINTS` is lowercase, so lowercase each word as soon as the user types it.

Here is example output from running this program:

```
Enter a word: quiz
quiz is worth 22 points.
Enter a word: cat
cat is worth 5 points.
Enter a word: JAZZ
jazz is worth 29 points.
Enter a word:
```

### Answer

```python
# How many points each letter is worth in Scrabble
POINTS = {
    "a": 1, "e": 1, "i": 1, "l": 1, "n": 1, "o": 1, "r": 1, "s": 1, "t": 1, "u": 1,
    "d": 2, "g": 2,
    "b": 3, "c": 3, "m": 3, "p": 3,
    "f": 4, "h": 4, "v": 4, "w": 4, "y": 4,
    "k": 5,
    "j": 8, "x": 8,
    "q": 10, "z": 10,
}


def score(word):
    """Adds up the points for every letter in word."""
    total = 0
    for letter in word:
        total += POINTS[letter]
    return total


def main():
    word = input("Enter a word: ").lower()
    while word != "":
        print(f"{word} is worth {score(word)} points.")
        word = input("Enter a word: ").lower()


if __name__ == "__main__":
    main()
```
