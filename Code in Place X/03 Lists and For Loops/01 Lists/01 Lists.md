## Lists

* [CiPX: Lists](https://youtu.be/Y_MZGpyuzGk?si=L0e_QIxcN2gZwNfd)


### Example 01 - Third Snack
What does this program print?

```python
main.py
def main():
    snacks = ["chips", "salsa", "cookies", "grapes"]
    print(snacks[2])

if __name__ == "__main__":
    main()
```

* chips
* salsa
* cookies
* grapes

**Correct Answer**: cookies

---
### Example 02 - Playlist

```python
def main():
    playlist = ["Levitating", "Flowers", "Golden Hour"]
    print(playlist[0])
    print(playlist[2])
    playlist.append("Cruel Summer")
    playlist[0] = "Espresso"
    print(playlist)

if __name__ == "__main__":
    main()
```

---

### Example 03 - The Last One

```python
def main():
    snacks = ["chips", "salsa", "cookies", "grapes"]
    print(len(snacks))
    print(snacks[len(snacks)])

if __name__ == "__main__":
    main()
```

* 4, and then grapes
* 4, and then an IndexError
* 3, and then grapes
* 4, and then chips

**Correct Answer**: 4, and then an IndexError
