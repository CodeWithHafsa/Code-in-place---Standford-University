## Recipe Book

Look up recipes in a recipe book.

Your program should:
* Store a recipe book as a dictionary. Each key is the name of a recipe, and each value is a dictionary with the minutes it takes and a list of ingredients.
* Keep asking for a recipe until the user presses enter instead of typing a name.
* For each recipe, print how long it takes and then each ingredient on its own line. If the recipe is not in the book, print a message instead.

Here is example output from running this program:

```
Which recipe? soup
soup takes 45 minutes. You need:
- carrots
- onion
- broth
Which recipe? cake
There is no recipe for cake.
Which recipe? salad
salad takes 10 minutes. You need:
- lettuce
- tomato
Which recipe?
```

Read nested data one bracket at a time. `recipes[name]` is one recipe's dictionary, so the program stores it in `recipe`. Then recipe`["minutes"]` is a number, and recipe`["ingredients"]` is a list the program can loop over.

### Answer:

```python
def main():
    recipes = {
        "pancakes": {"minutes": 20, "ingredients": ["flour", "milk", "eggs"]},
        "salad": {"minutes": 10, "ingredients": ["lettuce", "tomato"]},
        "soup": {"minutes": 45, "ingredients": ["carrots", "onion", "broth"]},
    }
    name = input("Which recipe? ")
    while name != "":
        if name in recipes:
            recipe = recipes[name]
            minutes = recipe["minutes"]
            print(f"{name} takes {minutes} minutes. You need:")
            for ingredient in recipe["ingredients"]:
                print(f"- {ingredient}")
        else:
            print(f"There is no recipe for {name}.")
        name = input("Which recipe? ")


if __name__ == "__main__":
    main()
```