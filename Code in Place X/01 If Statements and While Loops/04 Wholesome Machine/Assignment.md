## Assignment
Write a program which prompts the user to type the affirmation "I can do anything I put my mind to." until they type it correctly. Sometimes, especially in the midst of such uncertain times, we just need to be reminded that we are resilient, capable, and strong; this little Python program may be able to help!

Here's a sample run of the program (user input is in blue):

---
Please type the following affirmation: I can do anything I  put my mind to. \
<span style="color: blue;">Hmmm</span>\
That was not the affirmation. \
Please type the following affirmation: I can do anything I put my mind to. \
<span style="color: blue;">I can do anything I put my mind to.</span>\
That's right! :)

---

Note that you can call `input()` with no prompt and it will still wait for a user to type something!

---
### Code

```python
def main():
    affirmation = "I can do anything I put my mind to."

    while True:
        answer = input(f"Please type the following affirmation: {affirmation}\n")

        if answer == affirmation:
            print("That's right! :)")
            break
        else:
            print("That was not the affirmation.")


if __name__ == "__main__":
    main()
```