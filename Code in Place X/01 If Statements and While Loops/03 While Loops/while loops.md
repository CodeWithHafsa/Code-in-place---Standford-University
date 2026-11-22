## CIPX 

- [CiPX: Intro to While Loops](https://youtu.be/FCxbQaTJv6Q?si=q92QjOoTEHcNJjH7)
- [CiPX: While Loops Chatbot Example](https://youtu.be/tVkgUfkeQJ8?si=xl-RSXAtdGpnaAcF)


### Example 01 - Moon Sunrise

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

Output

```
Type the secret word: moon
Try again!
Type the secret word: sunrise
Ready!
```

---
### Example 02 - Sunrise 

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

Output

```
Type the secret word: sunrise
Ready!
```

---
### Example 03 - Password

```python
def main():
    password = input("Enter the gallery password: ")
    while password != "blue":
        print("That is not it.")
        password = input("Enter the gallery password: ")
    print("The gallery opens!")
if __name__ == "__main__":
    main()
```

---
### Example 04 - Encore

```python
def main():
    request = input("Type encore to hear the finale again: ")
    while request == "encore":
        print("The band plays the finale!")
        request = input("Type encore to hear it again: ")
    print("The concert is over!")

if __name__ == "__main__":
    main()
```

---
### Example 05 - Chatbot

```python
from ai import call_gpt

def main():
    message = input("You: ")
    while message != "bye":
        response = call_gpt(message)
        print("Chatbot:", response)
        message = input("You: ")
        
if __name__ == "__main__":
    main()
```

---
### Example 06 - Sentinel

```python
def main():
    message = input("Type a message, or done: ")
    while message != "done":
        print(message)
        message = input("Type a message, or done: ")

if __name__ == "__main__":
    main()
```

Output
```
"done"
```

---
### Example 07 - Done First

```python
def main():
    message = input("Type a message, or done: ")
    while message != "done":
        print(message)
        message = input("Type a message, or done: ")

if __name__ == "__main__":
    main()
```

Output

```
Type a message, or done: done
```