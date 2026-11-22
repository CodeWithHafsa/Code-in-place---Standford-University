## Times Table
Ask the user for a number, then print its times table from 1 to 10.

range(10) counts from 0 to 9, so add 1 to get the numbers 1 to 10.

#### Answer

```python
def main():
    num = int(input("Pick a number: "))

    # range(10) gives 0 through 9, so i + 1 gives 1 through 10
    for i in range(10):
        times = i + 1
        print(f"{num} x {times} = {num * times}")

if __name__ == "__main__":
    main()
```

Output:

```
Pick a number: 2
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
2 x 10 = 20
```