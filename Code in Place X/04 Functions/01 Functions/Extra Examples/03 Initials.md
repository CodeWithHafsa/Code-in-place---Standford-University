## Initials

Turn somebody’s three names into their initials.

Your program should:
1. Define a function `initial(name)` that returns the **capital** first letter of that name.
2. Ask for a first name, a middle name and a last name.
3. Print all three initials together on one line.

Here is example output from running this program:

```
First name: ada
Middle name: byron
Last name: lovelace
Your initials: ABL
```

`name[0]` is the first letter of a string. These are the same square brackets you used on lists, counting from 0.

Write `initial` once and call it three times, once per name. Resist the urge to write the letter-grabbing out three times: that is exactly the copy-and-paste the Functions lecture was arguing against.

### Answer

```python
def initial(name):
    return name[0].upper()

def main():
    first = input("First name: ")
    middle = input("Middle name: ")
    last = input("Last name: ")
    print(f"Your initials: {initial(first)}{initial(middle)}{initial(last)}")

if __name__ == "__main__":
    main()
```