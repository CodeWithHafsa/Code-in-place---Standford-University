## Exclamation Cheer

## Assignment
Write a program to cheer on your team.

Start with a list of words like `["way", "to", "go", "team"].`
Loop through the list and print each word in **all capital letters**, followed by an exclamation mark.

Here’s what the output should look like:

```
WAY!
TO!
GO!
TEAM!
```

#### Answer

```python

CHEER = ["way", "to", "go", "team"]

def main():
    for word in CHEER:
        print(word.upper() + "!")

if __name__ == "__main__":
    main()
```