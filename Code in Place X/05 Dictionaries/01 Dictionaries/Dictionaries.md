## Dictionaries

* [CiPX: What is a dictionary?](https://youtu.be/AnY0pNukCFo?si=V8cqLh34deaw299y)


### Example 01 - Look it up

What does this program print?

```
def main():
    ages = {"Ana": 36, "Ben": 7, "Cleo": 12}
    print(ages["Ben"])

if __name__ == "__main__":
    main()

```

* Ben
* 7
* 1
* An error, because "Ben" is not a number

**Correct Answer:** 7

**Explanation:**
* ages is a Python dictionary containing names and their ages.
* ages["Ben"] looks up the value associated with the key "Ben".
* Ben's age is 7.

---

### Example 02 - In checks the keys

What does this program print?

```
def main():
    prices = {"tea": 3, "cake": 5}
    print(3 in prices)
    print("tea" in prices)

if __name__ == "__main__":
    main()
```

* True \
False

* True \
True

* False \
True

* An error, because 3 is not a key

**Correct Answer:** 

False \
True

**Explanation:**

```prices = {"tea": 3, "cake": 5}```

* 3 in prices → False because 3 is a value, not a key.
* "tea" in prices → True because "tea" is a key.

### Example 03 - Spanish Dictionary

Here is a tiny English to Spanish dictionary. Run it and type cat.

```
SPANISH = {"hello": "hola", "cat": "gato", "dog": "perro", "thanks": "gracias"}

def main():
    word = input("English word: ")
    word = word.lower()
    if word in SPANISH:
        print(SPANISH[word])
    else:
        print("I do not know that word yet!")

if __name__ == "__main__":
    main()
```

Output:

```
% python main.py
English word: Cat
gato
```

### Example 04 - Exactly the same

What does this program print?

```
def main():
    menu = {"pizza": 12, "salad": 8}
    order = "Pizza"
    if order in menu:
        print(menu[order])
    else:
        print("Sorry, that is not on the menu")

if __name__ == "__main__":
    main()
```

* 12
* Sorry, that is not on the menu
* pizza
* An error, because "Pizza" is not a key

**Correct Answer:**  Sorry, that is not on the menu

**Explanation:**

Python dictionary keys are case-sensitive.
* The dictionary key is `"pizza"` (lowercase p).
* The order is `"Pizza"` (uppercase P).
* `"Pizza"` does not match `"pizza"`.

Therefore, the condition order in menu is False, and the else block runs.
