## Split the Bill

Dinner is over and nobody wants to do the arithmetic. Work out what each person owes.

Your program should:

1. Ask for the total bill.
2. Ask how many people are splitting it.
3. Divide the bill evenly and print what each person owes, rounded to two decimal places.

Here is example output from running this program:

```
Enter the total bill: 78.50
Enter the number of people: 3
Each person owes $26.17
```

The two answers need two different casts. A bill can have cents in it, so it becomes a float. A number of people cannot be 2.5, so it becomes an int. Choosing the right one is part of reading the problem.

One thing to notice: a bill of 100 split 8 ways prints $12.5 rather than $12.50. round hands back a number, and a number has no opinion about trailing zeros. That is a job for formatting, which is a story for another day.

#### Answer

```python
def main():
    bill = float(input("Enter the total bill: "))
    people = int(input("Enter the number of people: "))

    share = bill / people
    share = round(share, 2)

    print(f"Each person owes ${share}")

if __name__ == "__main__":
    main()
```
