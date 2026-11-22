## Phone Book

Build a phone book, then use it to make calls.

Your program should:
* Start with an empty dictionary of contacts.
* Keep asking for a name and a number until the user presses enter instead of typing a name. Store names in lowercase.
* Print how many contacts were saved.
* Then keep asking who to call until the user presses enter. Print their number if they are in the contacts, or a message if they are not.

Here is example output from running this program:

```
Add your contacts. Press enter when you are done.
Name: Mom
Number: 555-0123
Name: Ada
Number: 555-0199
Name:
Contacts saved: 2
Who do you want to call? ada
Calling ada at 555-0199...
Who do you want to call? Bob
bob is not in your contacts.
Who do you want to call?
```

This program has two halves. The first half fills the dictionary up, one pair each time around the loop. The second half only reads from it. If you type the same name twice, the second number replaces the first, because each key can only have one value.


### Answer

```python
def main():
    contacts = {}
    print("Add your contacts. Press enter when you are done.")
    name = input("Name: ").lower()
    while name != "":
        contacts[name] = input("Number: ")
        name = input("Name: ").lower()
    print(f"Contacts saved: {len(contacts)}")

    name = input("Who do you want to call? ").lower()
    while name != "":
        if name in contacts:
            print(f"Calling {name} at {contacts[name]}...")
        else:
            print(f"{name} is not in your contacts.")
        name = input("Who do you want to call? ").lower()


if __name__ == "__main__":
    main()
```
