## Star Square

Ask the user for a size, then print a square of stars that many rows tall and that many stars wide.

Use one loop for the rows. Inside it, use a second loop to build up each row one star at a time.


#### Answer

```python
def main():
    size = int(input("How big should the square be? "))

    for i in range(size):
        # Build one row, one star at a time
        row = ""
        for j in range(size):
            row += "*"
        print(row)

if __name__ == "__main__":
    main()
```

Output:

```
How big should the square be? 4
****
****
****
****
```