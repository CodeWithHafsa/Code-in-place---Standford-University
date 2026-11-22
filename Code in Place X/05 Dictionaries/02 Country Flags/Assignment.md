## Country Flags

Code in Place has students from all over the world. Let's write a program that shows each of them their flag!

Your starter code comes with a file called `flags.py`. It has a function called `build_flag_dictionary() `that returns a dictionary from every country's name to its flag emoji. Open `flags.py` and scroll through it: there are almost 300 entries! Imagine writing an if for every one of them. With a dictionary, you can find any country's flag in one line.

Your program should:

* Call `build_flag_dictionary()` to get the dictionary.
* Ask the user what country they are from.
* Every name in the dictionary is lowercase, so convert what the user typed to lowercase before you check whether it is in the dictionary.
* If the country is in the dictionary, print its flag and a welcome message that uses the name the way the user typed it.
* If it is not, print `Sorry, that country is not in the dictionary. Maybe try a different spelling!`

Here is an example run:

```
What country are you from? Japan
Here is your flag: 🇯🇵
Welcome to Code in Place X, friend from Japan!
```

And here is another:

```
What country are you from? Narnia
Sorry, that country is not in the dictionary. Maybe try a different spelling!
```

### Answer

```python

from flags import build_flag_dictionary


def main():
    flags = build_flag_dictionary()

    country = input("What country are you from? ")

    if country.lower() in flags:
        print("Here is your flag:", flags[country.lower()])
        print(f"Welcome to Code in Place X, friend from {country}!")
    else:
        print("Sorry, that country is not in the dictionary. Maybe try a different spelling!")


if __name__ == "__main__":
    main()
```
