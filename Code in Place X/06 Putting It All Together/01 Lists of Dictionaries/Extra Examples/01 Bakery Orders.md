## Bakery Orders

A bakery keeps today's orders in a list of dictionaries. Each order has an item and a price.

Your program should:
* Print every order with its price.
* Add up the prices and print the total.
* Find the order with the highest price and print its item.

Here is example output from running this program:

```
croissant: $3
sourdough: $7
bagel: $2
muffin: $4
Total: $16
Most expensive: sourdough
```

Notice that priciest holds a whole dictionary, not just a price. That way, when the loop is done, the program still knows which item was the most expensive. It starts as the first order, ORDERS[0], and is replaced whenever the loop finds an order that costs more.

### Answer

```python
ORDERS = [
    {"item": "croissant", "price": 3},
    {"item": "sourdough", "price": 7},
    {"item": "bagel", "price": 2},
    {"item": "muffin", "price": 4},
]


def main():
    total = 0
    priciest = ORDERS[0]
    for order in ORDERS:
        print(f"{order['item']}: ${order['price']}")
        total += order["price"]
        if order["price"] > priciest["price"]:
            priciest = order
    print(f"Total: ${total}")
    print(f"Most expensive: {priciest['item']}")


if __name__ == "__main__":
    main()
```

