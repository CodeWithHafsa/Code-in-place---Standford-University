## 02 Greetings!

Ask the user what part of the day it is for them, then greet them accordingly.

Your program should:

1. Ask whether it is morning or night.
2. If they answer `morning`, print Good `morning!`
3. Otherwise, print `Good evening!` Then print `Have a great day!` — **no matter what** they answered.

Here is example output from running this program twice:

```
Is it morning or night? morning
Good morning!
Have a great day!

Is it morning or night? night
Good evening!
Have a great day!
```

Look closely at the last line. It is **not** indented under the `if` or the `else`, so it is not part of either block and runs every single time.

---
### Code

```python
def main():
    part_of_day = input("Is it morning or night? ")

    if part_of_day == "morning":
        print("Good morning!")
    else:
        print("Good evening!")

    # This line is not indented under the if or the else, so it always runs
    print("Have a great day!")

if __name__ == "__main__":
    main()
```

