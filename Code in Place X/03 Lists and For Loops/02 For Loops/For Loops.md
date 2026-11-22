## For Loops

* [CiPX: For Loops](https://youtu.be/FNPJKRkJlpg?si=ZHRoZHx2Da8pg62N)
* [CiPX: Nested For Loops](https://youtu.be/LmXYBHm_Pj4?si=7b_4EXSzp1eovyHi)

### Example 01 - Roll Call

Every name in `TEAM` should get its own line of output. The print is already written, but it needs a loop above it. Which line walks through the list?

```python
TEAM = ["Ana", "Ben", "Cleo"]

def main():
    for name in TEAM:
        print(f"{name} is here!")
    for i in range(len(TEAM)):
        print(f"{i + 1}. {TEAM[i]}")

if __name__ == "__main__":
    main()
```

Output:

```
Ana is here!
Ben is here!
Cleo is here!
1. Ana
2. Ben
3. Cleo
```

---
### Example 02 - Counting positions

```python
main.py
def main():
    animals = ["cat", "dog", "fox"]
    for i in range(len(animals)):
        print(f"{i} {animals[i]}")

if __name__ == "__main__":
    main()
```

* 1 cat \
  2 dog \
  3 fox
* cat \
  dog \
  fox
* 0 cat \
  1 dog \
  2 fox
* 0 cat \
  1 dog

**Correct Answer**: \
  0 cat \
  1 dog \
  2 fox

---
### Example 03 - Find the name?

```python
GUESTS = ["Ana", "Ben", "Cleo", "Dev"]

def main():
    name = input("Who are you looking for? ")

    for guest in GUESTS:
        print(f"checking {guest}...")
        if guest == name:
            print("Found them!")
            break

if __name__ == "__main__":
    main()
```

Output:
```
Who are you looking for? Zoe
checking Ana...
checking Ben...
checking Cleo...
checking Dev...
```

---

### Example 04 - What is word?

```python
def main():
    words = ["hi", "there"]
    for word in words:
        print(len(word))

if __name__ == "__main__":
    main()
```

* hi \
there
* 0 \
1
* 7
* 2 \
5

**Correct Answer**: \
  2 \
  5

---
### Example 05 - Shout it Out

What does this program print?
```python
main.py
def main():
    pets = ["cat", "dog"]
    for pet in pets:
        loud = pet.upper()
        print(loud)
    print(pets[0])

if __name__ == "__main__":
    main()
```

* CAT \
DOG \
CAT

* cat \
dog \
cat

* CAT \
DOG \
cat

* CAT \
DOG

**Correct Answer**: \
  CAT \
  DOG \
  cat

---

### Example 06 - Icecream menu 

```python
def main():
    flavors = ["Vanilla", "Chocolate", "Strawberry"]
    toppings = ["Sprinkles", "Chocolate Sauce"]
    menu = []

    # Write a program that makes a menu of each flavor with each topping
    for flavor in flavors:
        for topping in toppings:
            ice_cream_combo = f"{flavor} with {topping}"
            menu.append(ice_cream_combo)

    for i in range(len(menu)):
        print(f"{i}. {menu[i]}")

if __name__ == "__main__":
    main()
```

----

### Example 07 - A loop inside a loop

What does this program print?

```python
main.py
def main():
    for letter in "hi":
        for i in range(3):
            print(letter)

if __name__ == "__main__":
    main()
```

* h \
h \
h \
i \
i \
i

* h \
i \
h \
i \
h
i

* h \
i

* hhh \
iii

**Correct Answer** \
h \
h \
h \
i \
i \
i

---
### Example 08 - Stretch It

Read this program, then run it with the word cat. Guess the output first.

```python
def main():
    word = input("Enter a word: ")
    stretched = ""

    for letter in word:
        for i in range(3):
            stretched += letter

    print(stretched)

if __name__ == "__main__":
    main()
```

Output:

```
% python main.py
Enter a word: cat
cat
% python main.py
Enter a word: cat
cccaaattt
% python main.py
Enter a word: cat
cccaaattt
% python main.py
Enter a word: wow
wwwooowww
```