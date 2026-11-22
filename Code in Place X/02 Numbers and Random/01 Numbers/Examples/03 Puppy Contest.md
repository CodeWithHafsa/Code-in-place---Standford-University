## Puppy Contest

Three judges each score a puppy out of 10. Print the puppy’s average score.

Your program should:

1. Ask each of the three judges for a score.
2. Add the three scores together, then divide by 3.
3. Print the average.

Here is example output from running this program:

```
Enter judge 1's score: 9
Enter judge 2's score: 8
Enter judge 3's score: 10
The average score is 9.0
```

The parentheses are doing real work here. Without them Python would divide first and compute `first + second + (third / 3)`, which is not an average at all. It would not raise an error either. It would just quietly be wrong.

Notice too that the answer prints as 9.0 and not 9. / always hands back a decimal, even when it divides evenly.

#### Answer

```python
def main():
    first = int(input("Enter judge 1's score: "))
    second = int(input("Enter judge 2's score: "))
    third = int(input("Enter judge 3's score: "))

    # The parentheses matter: without them only the third score is divided
    average = (first + second + third) / 3

    print(f"The average score is {average}")

if __name__ == "__main__":
    main()
```