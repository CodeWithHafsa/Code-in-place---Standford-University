## 01 Secret Word

Keep asking for a secret word until the user types it correctly. The secret word is sunrise.



Your program should:
1. Ask the user to type the secret word.
2. As long as their answer is **not** sunrise, print T`ry again!` and ask again.
3. Once they type `sunrise`, print `Ready!`

Here is example output when the user needs two tries:

```
Type the secret word: moon
Try again!
Type the secret word: sunrise
Ready!
```

And when they get it right the first time:

```
Type the secret word: sunrise
Ready!
```

Notice there are two input lines: one before the loop, and one inside it. The one inside is what gives the loop a new answer to check. Without it, `answer` would never change and the loop would run forever.

---
### Code

```python
def main():
    answer = input("Type the secret word: ")
    while answer != "sunrise":
        print("Try again!")
        answer = input("Type the secret word: ")
    print("Ready!")

if __name__ == "__main__":
    main()
```