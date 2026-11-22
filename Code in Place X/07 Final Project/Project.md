## ⭐ Star Creator
*A Magical Galaxy of Your Own*

![alt text](image.png)

* [Link](https://codeinplace.stanford.edu/cipx/share/0XjFP1GyOTcmtHBswU87)

> About Project

Welcome to Star Creator, a magical universe where creativity meets the beauty of the stars!

Star Creator is an interactive Python application that lets users create their own constellations by adding stars, connecting them, and giving their creations unique names.

Explore a random galaxy, complete constellation challenges, choose different star themes, and build your own personal universe collection.

**Features:**

* Create stars using custom coordinates.
* Connect stars to design unique constellations.
* Name and save your creations.
* Generate random galaxies.
* Play constellation challenges.
* Choose different galaxy themes.
* Save, load, view, and manage your * constellation collection.

**My goal:** To combine creativity, imagination, and Python programming to create a fun experience where everyone can become a Star Creator!

✨ Every star tells a story. Create yours!

---

```python

# ==================================================
# STAR CREATOR
# A Magical Galaxy Project
# Code in Place Final Project
#
# Step 1: Magical Welcome Screen
# Step 2: Add Your Own Stars
# Step 3: Connect the Stars
# Step 4: Name Your Constellation
# Step 5: Random Galaxy Generator
# Step 6: Save and Load Creations
# Step 7: Constellation Challenge Game
# Step 8: Star Colors and Themes
# Step 9: My Universe Collection
# Step 10: Final Menu and Polish
# ==================================================

import random
import json
import os


# -------------------------------
# CONSTANTS
# -------------------------------

WIDTH = 45
HEIGHT = 12

SAVE_FILE = "star_creator_data.json"

PURPLE = "\033[95m"
BLUE = "\033[94m"
CYAN = "\033[96m"
YELLOW = "\033[93m"
RESET = "\033[0m"

STAR_SYMBOL = "*"

stars = []
connections = []
constellations = []


# ==================================================
# STEP 1: MAGICAL WELCOME SCREEN
# ==================================================

def show_title():
    print()
    print(PURPLE + "=" * 48)
    print("                 STAR CREATOR")
    print("=" * 48 + RESET)
    print(BLUE + "          CREATE YOUR OWN UNIVERSE" + RESET)
    print()
    print("       Explore the magic of the stars!")
    print()


def create_galaxy():
    print(CYAN + "             YOUR MAGICAL GALAXY" + RESET)
    print()

    symbols = [".", "*", "+", " ", " ", " "]

    for row in range(HEIGHT):
        line = ""

        for column in range(WIDTH):
            line += random.choice(symbols)

        print(BLUE + line + RESET)

    print()
    print(PURPLE + "       A UNIVERSE FULL OF POSSIBILITIES" + RESET)
    print()


# ==================================================
# STEP 2: ADD YOUR OWN STARS
# ==================================================

def get_number(prompt, minimum, maximum):
    while True:
        answer = input(prompt)

        if not answer.isdigit():
            print("Please enter a valid number.")
            continue

        number = int(answer)

        if minimum <= number <= maximum:
            return number

        print(f"Enter a number between {minimum} and {maximum}.")


def add_stars():
    print("\n========== ADD YOUR STARS ==========")

    print("X coordinates: 1 to", WIDTH)
    print("Y coordinates: 1 to", HEIGHT)
    print("Type 'done' to finish.\n")

    while True:
        answer = input("Enter X coordinate: ")

        if answer.lower() == "done":
            break

        if not answer.isdigit():
            print("Please enter a valid number.")
            continue

        x = int(answer)

        if x < 1 or x > WIDTH:
            print("X coordinate is out of range.")
            continue

        y = get_number("Enter Y coordinate: ", 1, HEIGHT)

        if any(star["x"] == x and star["y"] == y for star in stars):
            print("There is already a star there!")
            continue

        stars.append({"x": x, "y": y})

        print(YELLOW + f"Star {len(stars)} created!" + RESET)


# ==================================================
# STEP 3: CONNECT THE STARS
# ==================================================

def connect_stars():
    print("\n========== CONNECT YOUR STARS ==========")

    if len(stars) < 2:
        print("You need at least two stars!")
        return

    for i, star in enumerate(stars):
        print(
            f"Star {i + 1}: "
            f"({star['x']}, {star['y']})"
        )

    print("\nType 'done' to finish.")

    while True:
        first = input("\nFirst star number: ")

        if first.lower() == "done":
            break

        if not first.isdigit():
            print("Enter a valid star number.")
            continue

        second = input("Second star number: ")

        if second.lower() == "done":
            break

        if not second.isdigit():
            print("Enter a valid star number.")
            continue

        a = int(first)
        b = int(second)

        if a < 1 or a > len(stars):
            print("First star does not exist.")
            continue

        if b < 1 or b > len(stars):
            print("Second star does not exist.")
            continue

        if a == b:
            print("Choose two different stars.")
            continue

        connection = (a - 1, b - 1)

        if connection in connections or (b - 1, a - 1) in connections:
            print("These stars are already connected.")
            continue

        connections.append(connection)

        print(YELLOW + f"Stars {a} and {b} connected!" + RESET)


# Display the star map

def show_constellation():
    print("\n========== YOUR STAR MAP ==========")

    if not stars:
        print("No stars have been created yet.")
        return

    grid = [
        [" " for column in range(WIDTH)]
        for row in range(HEIGHT)
    ]

    # Draw connecting lines
    for first, second in connections:

        star1 = stars[first]
        star2 = stars[second]

        x1 = star1["x"] - 1
        y1 = star1["y"] - 1

        x2 = star2["x"] - 1
        y2 = star2["y"] - 1

        steps = max(abs(x2 - x1), abs(y2 - y1))

        if steps > 0:
            for i in range(steps + 1):

                x = round(x1 + (x2 - x1) * i / steps)
                y = round(y1 + (y2 - y1) * i / steps)

                if grid[y][x] == " ":

                    if x1 == x2:
                        grid[y][x] = "|"

                    elif y1 == y2:
                        grid[y][x] = "-"

                    elif (x2 - x1) * (y2 - y1) > 0:
                        grid[y][x] = "\\"

                    else:
                        grid[y][x] = "/"

    # Place stars over the lines
    for star in stars:

        x = star["x"] - 1
        y = star["y"] - 1

        grid[y][x] = STAR_SYMBOL

    # Display the map
    print("+" + "-" * WIDTH + "+")

    for row in grid:
        print("|" + BLUE + "".join(row) + RESET + "|")

    print("+" + "-" * WIDTH + "+")

    print("Total stars:", len(stars))
    print("Total connections:", len(connections))


# ==================================================
# STEP 4: NAME YOUR CONSTELLATION
# ==================================================

def name_constellation():
    if not stars:
        print("Create stars before saving!")
        return

    print("\n========== NAME YOUR CONSTELLATION ==========")

    name = input("Enter a constellation name: ").strip()

    if name == "":
        print("Please enter a name.")
        return

    constellation = {
        "name": name,
        "stars": [star.copy() for star in stars],
        "connections": [list(c) for c in connections],
        "symbol": STAR_SYMBOL
    }

    constellations.append(constellation)

    print(PURPLE + f"\n'{name}' has been added to your universe!" + RESET)


# ==================================================
# STEP 5: RANDOM GALAXY GENERATOR
# ==================================================

def random_galaxy():
    global stars, connections

    print("\n========== RANDOM GALAXY GENERATOR ==========")

    number = get_number("How many stars? (3-12): ", 3, 12)

    stars = []
    connections = []

    positions = set()

    while len(positions) < number:

        x = random.randint(1, WIDTH)
        y = random.randint(1, HEIGHT)

        positions.add((x, y))

    for x, y in positions:
        stars.append({"x": x, "y": y})

    # Connect stars in a random chain
    for i in range(number - 1):
        connections.append((i, i + 1))

    print(YELLOW + "\nYour random galaxy has been created!" + RESET)

    show_constellation()


# ==================================================
# STEP 6: SAVE AND LOAD CREATIONS
# ==================================================

def save_data():
    data = {
        "constellations": constellations
    }

    try:
        with open(SAVE_FILE, "w") as file:
            json.dump(data, file, indent=4)

        print(CYAN + "Your universe has been saved!" + RESET)

    except OSError:
        print("Could not save your universe.")


def load_data():
    global constellations

    if not os.path.exists(SAVE_FILE):
        constellations = []
        return

    try:
        with open(SAVE_FILE, "r") as file:
            data = json.load(file)

        constellations = data.get("constellations", [])

        print(
            f"Welcome back! "
            f"{len(constellations)} saved creations loaded."
        )

    except (OSError, json.JSONDecodeError):
        constellations = []
        print("Could not load saved creations.")


def save_and_load_menu():
    print("\n========== SAVE AND LOAD ==========")
    print("1. Save universe")
    print("2. Reload saved universe")
    print("3. Return to menu")

    choice = input("Choose an option: ")

    if choice == "1":
        save_data()

    elif choice == "2":
        load_data()

    elif choice == "3":
        return

    else:
        print("Invalid option.")


# ==================================================
# STEP 7: CONSTELLATION CHALLENGE GAME
# ==================================================

def constellation_challenge():
    print("\n========== CONSTELLATION CHALLENGE ==========")

    print("Choose a challenge:")
    print("1. Create a Triangle")
    print("2. Create a Diamond")

    choice = input("Your choice: ")

    if choice == "1":
        required_stars = 3
        required_connections = 3
        shape = "Triangle"

    elif choice == "2":
        required_stars = 4
        required_connections = 4
        shape = "Diamond"

    else:
        print("Invalid challenge.")
        return

    print(f"\nYour mission: Create a {shape}!")
    print(f"You need {required_stars} stars.")
    print(f"You need {required_connections} connections.")

    stars.clear()
    connections.clear()

    add_stars()
    connect_stars()

    show_constellation()

    if (
        len(stars) == required_stars
        and len(connections) == required_connections
    ):
        print(YELLOW + "\nCHALLENGE COMPLETED!" + RESET)
        print(f"Congratulations! You created a {shape}!")
        print("You earned 100 galaxy points!")

    else:
        print("\nChallenge not completed yet.")
        print("Try again and follow the requirements!")


# ==================================================
# STEP 8: STAR SYMBOLS AND THEMES
# ==================================================

def choose_theme():
    global STAR_SYMBOL

    print("\n========== CHOOSE YOUR GALAXY THEME ==========")

    print("1. Purple Galaxy (*)")
    print("2. Blue Galaxy (+)")
    print("3. Golden Galaxy (@)")
    print("4. Pink Galaxy (o)")

    choice = input("Choose your theme: ")

    if choice == "1":
        STAR_SYMBOL = "*"
        print(PURPLE + "Purple Galaxy selected!" + RESET)

    elif choice == "2":
        STAR_SYMBOL = "+"
        print(BLUE + "Blue Galaxy selected!" + RESET)

    elif choice == "3":
        STAR_SYMBOL = "@"
        print(YELLOW + "Golden Galaxy selected!" + RESET)

    elif choice == "4":
        STAR_SYMBOL = "o"
        print(CYAN + "Pink Galaxy selected!" + RESET)

    else:
        print("Invalid theme.")


# ==================================================
# STEP 9: MY UNIVERSE COLLECTION
# ==================================================

def show_collection():
    print("\n========== MY UNIVERSE COLLECTION ==========")

    if not constellations:
        print("You haven't saved any constellations yet!")
        return

    total_stars = 0
    total_connections = 0

    for i, constellation in enumerate(constellations):

        print(f"\n{i + 1}. {constellation['name']}")

        print("   Stars:", len(constellation["stars"]))

        print(
            "   Connections:",
            len(constellation["connections"])
        )

        total_stars += len(constellation["stars"])
        total_connections += len(constellation["connections"])

    print("\n========== UNIVERSE STATISTICS ==========")

    print("Total constellations:", len(constellations))
    print("Total stars:", total_stars)
    print("Total connections:", total_connections)


def delete_constellation():
    if not constellations:
        print("There are no saved creations to delete.")
        return

    show_collection()

    number = get_number(
        "\nEnter the number to delete (0 to cancel): ",
        0,
        len(constellations)
    )

    if number == 0:
        return

    deleted = constellations.pop(number - 1)

    print(f"'{deleted['name']}' has been deleted.")

    save_data()


def view_constellation():
    if not constellations:
        print("No saved constellations available.")
        return

    show_collection()

    number = get_number(
        "\nWhich constellation would you like to view? ",
        1,
        len(constellations)
    )

    selected = constellations[number - 1]

    print("\nConstellation:", selected["name"])

    print("Stars:", selected["stars"])
    print("Connections:", selected["connections"])

    # Temporarily display the selected creation
    global stars, connections, STAR_SYMBOL

    old_stars = stars
    old_connections = connections
    old_symbol = STAR_SYMBOL

    stars = selected["stars"]
    connections = [tuple(c) for c in selected["connections"]]
    STAR_SYMBOL = selected.get("symbol", "*")

    show_constellation()

    stars = old_stars
    connections = old_connections
    STAR_SYMBOL = old_symbol


# ==================================================
# STEP 10: FINAL MENU AND POLISH
# ==================================================

def show_menu():
    print(PURPLE + "\n========================================")
    print("             STAR CREATOR")
    print("========================================" + RESET)

    print("1.  Add your own stars")
    print("2.  Connect stars")
    print("3.  View your star map")
    print("4.  Name and save constellation")
    print("5.  Random galaxy generator")
    print("6.  Save and load universe")
    print("7.  Constellation challenge")
    print("8.  Choose galaxy theme")
    print("9.  View universe collection")
    print("10. View a saved constellation")
    print("11. Delete a constellation")
    print("12. Exit")

    print("=" * 40)


def main():

    show_title()
    create_galaxy()

    print("Welcome, Star Creator!")

    load_data()

    while True:

        show_menu()

        choice = input("\nEnter your choice: ")

        if choice == "1":
            add_stars()

        elif choice == "2":
            connect_stars()

        elif choice == "3":
            show_constellation()

        elif choice == "4":
            name_constellation()

        elif choice == "5":
            random_galaxy()

        elif choice == "6":
            save_and_load_menu()

        elif choice == "7":
            constellation_challenge()

        elif choice == "8":
            choose_theme()

        elif choice == "9":
            show_collection()

        elif choice == "10":
            view_constellation()

        elif choice == "11":
            delete_constellation()

        elif choice == "12":
            print()
            save_data()

            print(PURPLE + "========================================")
            print("       THANK YOU, STAR CREATOR!")
            print("========================================" + RESET)

            print("Keep dreaming among the stars!")
            print("Goodbye!")

            break

        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
```