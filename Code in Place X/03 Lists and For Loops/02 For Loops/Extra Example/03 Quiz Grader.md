## Quiz Grader

Start with the answer key for a five-question quiz and a list of one student's answers. Count how many answers match the key, then print the score.

Loop over the positions with range(len(key)). The same i can then look up question i in both lists.

#### Answer

```python
def main():
    key = ["b", "a", "d", "c", "a"]
    answers = ["b", "c", "d", "c", "b"]

    score = 0
    # One i walks through both lists at once
    for i in range(len(key)):
        if answers[i] == key[i]:
            score += 1

    print(f"You got {score} out of {len(key)} right.")

if __name__ == "__main__":
    main()
```

Output:

```
You got 3 out of 5 right.
```