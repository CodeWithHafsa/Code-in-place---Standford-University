## 02 Echo Until Done

Echo back everything the user types, until they type done.

Your program should:
1. Ask the user to type a message, or `done`.
2. As long as the message is **not** `done`, print the message back and ask again.
3. When they type `done`, the program ends.

Here is example output from running this program:
```
Type a message, or done: hello
hello
Type a message, or done: how are you
how are you
Type a message, or done: done
```

Notice that `done` itself never gets echoed, because the loop checks its condition before running the body again.

---
### Code

```python
def main():
    message = input("Type a message, or done: ")
    while message != "done":
        print(message)
        message = input("Type a message, or done: ")

if __name__ == "__main__":
    main()
```