## Ticket Booth

A museum charges different prices for different ages: under 5 is free, kids under 18 and seniors 65 and over pay $8, and everyone else pays $12.

Your program should:
* Write a function ticket_price(age) that returns the price for one visitor.
* Loop over the list of visitors and print each visitor's name, age, and price.
* Print the total for the whole group.

Here is example output from running this program:

```
Ana (4): $0
Ben (16): $8
Cleo (35): $12
Dev (70): $8
Total: $28
```

`ticket_price` has three choices, so it uses elif. Python checks the conditions from the top down and uses the first one that is true, so a 4 year old gets the free ticket even though 4 is also less than 18. The middle choice uses or because two different groups pay the same price.


### Answer

```python
VISITORS = [
    {"name": "Ana", "age": 4},
    {"name": "Ben", "age": 16},
    {"name": "Cleo", "age": 35},
    {"name": "Dev", "age": 70},
]


def ticket_price(age):
    if age < 5:
        return 0
    elif age < 18 or age >= 65:
        return 8
    else:
        return 12


def main():
    total = 0
    for visitor in VISITORS:
        price = ticket_price(visitor["age"])
        print(f"{visitor['name']} ({visitor['age']}): ${price}")
        total += price
    print(f"Total: ${total}")


if __name__ == "__main__":
    main()
```