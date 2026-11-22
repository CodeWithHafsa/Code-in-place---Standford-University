Quiz the user on one Spanish word, using != to check their answer.

Your program should:

1. Ask the user how to say Hello in Spanish.
2. If their response is **not** `Hola`, print `That is incorrect.`
3. Otherwise, print `This is correct!`

Here is example output from running this program twice:

```
How do you say Hello in Spanish? Bonjour
That is incorrect.
```

```
How do you say Hello in Spanish? Hola
This is correct!
```

!= means "is not equal to". It is the opposite of ==, so the if block runs when the two values are different and the else block runs when they match.

---

### Code

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