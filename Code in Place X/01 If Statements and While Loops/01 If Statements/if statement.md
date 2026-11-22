## CIPX 

- [CiPX: If Statements](https://youtu.be/iSqWiLP1YVA?si=jc4waUXRFPNPBmtw)
- [CiPX: If Statements 2](https://youtu.be/s_0JFKDwr-k?si=VTwV0PWNsfc5BFnS)


### Example 01 - Spotlight

```python
def main():
    light = "red"

    if light == "green":
        print("Go!")
    else:
        print("Stop.")

if __name__ == "__main__":
    main()
```

Output:

```
Stop
```

----
### Example 02 - Good Morning

```python
def main():
    part_of_day = input("Is it morning or night? ")
    if part_of_day == "morning":
        print("Good morning!")

if __name__ == "__main__":
    main()
```

----
### Example 03 - Outside the If

```python
def main():
    guess = "cat"

    if guess == "dog":
        print("Correct!")
    print("Thanks for playing!")

if __name__ == "__main__":
    main()
```


Output:

```
Thanks for playing!
```

---
### Example 04 - Good Evening

```python
def main():
    part_of_day = input("Is it morning or night? ")
    if part_of_day == "morning":
        print("Good morning!")
    else:
        print("Good evening!")

if __name__ == "__main__":
    main()
```

---
### Example 05 - What else != do?

```python
def main():
    response = input("How do you say Hello in Spanish? ")

    if response != "Hola":
        print("That is incorrect.")
    else:
        print("This is correct!")

if __name__ == "__main__":
    main()
```

Output
```
This is correct!
```

---
### Example 06 - Cat != cat

```
from ai import call_gpt

def main():
    animal = input("Name an animal: ")
    description = input("Describe it in a few words: ")

    prompt = f"The user is thinking of an animal. Here is a description: {description}. Guess the animal. Respond in a single word, nothing else."
    guess = call_gpt(prompt)

    if guess.lower() == animal.lower():
        print(f"Wahoo! GPT guessed {guess}!")
    else:
        print(f"Aww! GPT guessed {guess}, but you were thinking of {animal}.")

if __name__ == "__main__":
    main()
```