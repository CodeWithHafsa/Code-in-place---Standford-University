## Saving Seats

Start with a row of five seats, where one is already taken. Ask the user for their name and which seat they want. If that seat is open, save it for them. Then print the row.

You can change one item in a list by assigning to its position, like seats[2] = "Ana".

```python
def main():
    # Every seat starts open except seat 1
    seats = ["open", "Ana", "open", "open", "open"]
    print("Seats:", seats)

    name = input("What is your name? ")
    seat = int(input("Pick a seat from 0 to 4: "))

    # Assigning to a position replaces just that one item
    if seats[seat] == "open":
        seats[seat] = name
        print(f"Seat {seat} is yours, {name}.")
    else:
        print(f"Sorry, {seats[seat]} is already in seat {seat}.")

    print("Seats:", seats)

if __name__ == "__main__":
    main()
```

Output:

```
Seats: ['open', 'Ana', 'open', 'open', 'open']
What is your name? Hax
Pick a seat from 0 to 4: 2
Seat 2 is yours, Hax.
Seats: ['open', 'Ana', 'Hax', 'open', 'open']
```