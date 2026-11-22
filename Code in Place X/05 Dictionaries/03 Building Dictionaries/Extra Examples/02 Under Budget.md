## Under Budget

Find everything on the menu you can afford.

Your program should:
* Ask the user how many dollars they have.
* Loop over MENU and print every item that costs that much or less, with its price.

Here is example output from running this program:

```
How many dollars do you have? 4
You can afford:
tea ($2)
coffee ($3)
cookie ($1)
cake ($4)
```

A for loop over a dictionary hands you each key, here the name of each item. To get the price you look it up with that key: MENU[item]. The items print in the same order they were written in MENU.

### Answer

```python
# The menu at a tiny café, in dollars
MENU = {"tea": 2, "coffee": 3, "cookie": 1, "sandwich": 7, "soup": 5, "cake": 4}


def main():
    budget = int(input("How many dollars do you have? "))
    print("You can afford:")
    for item in MENU:
        if MENU[item] <= budget:
            print(f"{item} (${MENU[item]})")


if __name__ == "__main__":
    main()
```

