## Say It Louder

Write a function that shouts a word, and then use it twice.

Your program should:

1. Define a function `shout(word)` that **returns** the word in capitals with an exclamation mark after it.
2. Ask the user what to shout.
3. Print the shouted version of what they typed.
4. Print `shout("and I mean it")` on the next line.

Here is example output from running this program:

```
What should I shout? hello
HELLO!
AND I MEAN IT!
```

`"hello".upper()` gives you "HELLO". It hands back a new capitalised string and leaves the original alone.

Notice that you wrote shout once and called it twice, with two different words, and got two different answers. A function does not remember being called before; every call starts fresh with whatever it was handed.


### Answer


```python
def shout(word):
    return word.upper() + "!"

def main():
    word = input("What should I shout? ")
    print(shout(word))
    print(shout("and I mean it"))

if __name__ == "__main__":
    main()
```