## Grocery Total

Ring up a shopping trip using a dictionary of prices.

Your program should:

* Keep asking the user for items until they press enter without typing anything.
* Lowercase each item, because every key in PRICES is lowercase.
* If the item is in PRICES, print what it costs and add it to the total.
* If it is not, print a polite message and keep going.
* At the end, print the total.

Here is example output from running this program:

```
Item: bread
bread costs $3
Item: Milk
milk costs $2
Item: pizza
Sorry, we do not sell pizza.
Item: eggs
eggs costs $4
Item:
Your total is $9.
```

Start the total at 0, look up each item, and add on what you find. The if item in PRICES check is what lets the program shrug off pizza instead of crashing with a KeyError.

### Answer

```python
# How much each item costs, in dollars
PRICES = {"apple": 1, "bread": 3, "milk": 2, "cheese": 5, "eggs": 4}


def main():
    total = 0
    item = input("Item: ").lower()
    while item != "":
        if item in PRICES:
            total += PRICES[item]
            print(f"{item} costs ${PRICES[item]}")
        else:
            print(f"Sorry, we do not sell {item}.")
        item = input("Item: ").lower()
    print(f"Your total is ${total}.")


if __name__ == "__main__":
    main()
```
