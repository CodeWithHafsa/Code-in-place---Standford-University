## Guest List

Start with a list of party guests. Ask the user for their name. If they are already on the list, welcome them in. Otherwise, add them to the list and print the new list.

The in keyword checks whether a value is somewhere in a list.

#### Answer

```python
def main():
    guests = ["Ana", "Ben", "Cleo"]
    name = input("What is your name? ")

    # in looks through the whole list to see if the name is there
    if name in guests:
        print(f"Welcome in, {name}!")
    else:
        guests.append(name)
        print(f"You're on the list now, {name}.")
        print("Guests:", guests)

if __name__ == "__main__":
    main()
```

Output:

```
What is your name? Hax
You're on the list now, Hax.
Guests: ['Ana', 'Ben', 'Cleo', 'Hax']
```