## 03 Encore

Play the concert finale again for as long as the user keeps asking for an encore.

Your program should:

1. Ask the user to type encore to hear the finale again.
2. As long as their answer is encore, print `The band plays the finale!` and ask again.
3. When they type anything else, print `The concert is over!`

Example output:

```
Type encore to hear the finale again: encore
The band plays the finale!
Type encore to hear it again: encore
The band plays the finale!
Type encore to hear it again: no more
The concert is over!
```

---
### Code

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