## Dictionaries and Strings

* [CiPX: Dictionary example (scrabble)](https://youtu.be/nncPsGtl67o?si=_Yo-OBttd5siV9fL)
* [CiPX: Dictionaries and Strings](https://youtu.be/hfPmfxzU_XA?si=6qop75OHqflGVuCH)

### Example 01 - Trace It

What does this program print?

```
POINTS = {"a": 1, "c": 3, "t": 1}

def score(word):
    total = 0
    for letter in word:
        total += POINTS[letter]
    return total

def main():
    print(score("tact"))

if __name__ == "__main__":
    main()
```

* 4
* 5
* 6
* An error, because "t" appears twice

**Correct Answer:** 6

**Explanation:**

The program calculates the score of each letter in `"tact"` using the dictionary:

```python
POINTS = {"a": 1, "c": 3, "t": 1}
```

Let's add the points:

| Letter | Points |
| --- | --- |
| t | 1 |
| a | 1 |
| c | 3 |
| t | 1 |
| Total | 6 |

The letter `"t"` appears twice, and its points are counted twice.

Output:

```
6
```

**Remember**: A dictionary stores each letter's score once, but you can look up and add that score multiple times.

----

### Example 02 - Scrabble Score

```python
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
    total = 0
    for letter in word:
        if letter in POINTS:
            total += POINTS[letter]
    return total


def main():
    word = input("Enter a word: ")
    word = word.lower()
    print(f"{word} is worth {score(word)} points.")

if __name__ == "__main__":
    main()
```

Output:

```
% python main.py
Enter a word: don't
don't is worth 5 points.
```

----

### Example 03 - Split It

What does this program print?

```
def main():
    sentence = "the cat sat"
    words = sentence.split()
    print(len(words))
    print(words[1])

if __name__ == "__main__":
    main()
```

* 11\
h

* 3\
cat

* 3\
the

* 1\
the cat sat

**Correct Answer:**

3\
cat

**Explanation:**

```python
sentence = "the cat sat"
words = sentence.split()
```

The `.split()` method separates the sentence into a list of words:

```python
["the", "cat", "sat"]
```

Now:

- `len(words)` → `3` (there are three words).
- `words[1]` → `"cat"` (Python indexing starts at 0).

**Remember:** Python lists start counting at index `0`, not `1`.

---

### Example 04 - Build It

What does this program print?

```
def main():
    colors = ["red", "green", "blue"]
    result = ""
    for color in colors:
        result += color + " "
    print(result)

if __name__ == "__main__":
    main()
```

* blue
* redgreenblue
* red green blue
* ["red", "green", "blue"]

**Correct answer:** Option 3: red green blue

**Explanation:**

The loop goes through each color and adds it to the `result` string, followed by a space.

```python
result = ""
result += "red "    # result = "red "
result += "green "  # result = "red green "
result += "blue "   # result = "red green blue "
```

Output:

```
red green blue
```

**Remember:** The `+=` operator adds text to the existing string.

----

### Example 05 - Hashtags

This program should turn every word of a message into a hashtag. Run it and type code in place.

```python
def main():
    message = input("Message: ")
    words = message.split()
    result = ""
    for word in words:
        result += f"#{word} "
    print(result)

if __name__ == "__main__":
    main()
```

Output:

```
% python main.py
Message: I love dictionaries
#I #love #dictionaries 
```

