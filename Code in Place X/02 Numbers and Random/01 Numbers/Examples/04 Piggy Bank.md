## Piggy Bank

Keep dropping coins into a piggy bank until it holds at least $10.

Your program should:

1. Start with a total of 0.
2. As long as the total is under $10, ask for an amount to add, add it to the total, and print the new total.
3. Once the total reaches $10, print that you saved enough.

Here is example output from running this program:

```
Enter an amount to add: 3.50
You have saved $3.5
Enter an amount to add: 4.25
You have saved $7.75
Enter an amount to add: 5.00
You have saved $12.75
You saved enough!
```

`total = total + amount` reads strangely if you think of it as math, because it looks like it cannot be true. It is not an equation: Python works out the right-hand side first, then stores the result back in total. That is what lets one variable carry a running total across every pass of the loop.

#### Answer

```python
GOAL = 10

def main():
    total = 0

    while total < GOAL:
        amount = float(input("Enter an amount to add: "))

        # Work out the new total, then store it back in the same variable
        total = total + amount
        print(f"You have saved ${total}")

    print("You saved enough!")

if __name__ == "__main__":
    main()
```