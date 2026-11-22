## Grocery List
Start with an empty list. Ask the user for three grocery items and append each one to the list. Then print the whole list, how many items it has, and a reminder about the first item.

#### Answer

```python
def main():
    # Start with an empty list and grow it one item at a time
    groceries = []

    item = input("Add an item: ")
    groceries.append(item)
    item = input("Add an item: ")
    groceries.append(item)
    item = input("Add an item: ")
    groceries.append(item)

    print(f"Your list has {len(groceries)} items: {groceries}")
    print(f"Don't forget the {groceries[0]}!")

if __name__ == "__main__":
    main()
```

Output:

```
Add an item: Carrot
Add an item: Lemon
Add an item: Spinach
Your list has 3 items: ['Carrot', 'Lemon', 'Spinach']
Don't forget the Carrot!
```