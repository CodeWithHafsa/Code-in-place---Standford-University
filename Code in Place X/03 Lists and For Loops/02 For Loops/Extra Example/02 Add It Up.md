## Add It Up

Start with a list of prices from a shopping trip. Print each price, and then print the total.

Start the total at 0 before the loop, and add to it once for each price.

#### Answer

```python
def main():
    prices = [4, 12, 3, 8, 5]

    # The total starts at 0 and grows by one price each time around the loop
    total = 0
    for price in prices:
        print(f"${price}")
        total += price

    print(f"Total: ${total}")

if __name__ == "__main__":
    main()
```

Output:

```
$4
$12
$3
$8
$5
Total: $32
```