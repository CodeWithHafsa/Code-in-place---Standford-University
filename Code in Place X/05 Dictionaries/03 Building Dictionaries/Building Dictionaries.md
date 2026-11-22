## Building Dictionaries

* [CiPX: Looping and building a dictionary](https://youtu.be/oTN4aVP87Gk?si=ZlzdiHa5tzK426-G)

### Example 01 - What does the loop give you?

What does this program print?

```
def main():
    team = {"Ada": "goalie", "Ben": "striker"}
    for player in team:
        print(player)

if __name__ == "__main__":
    main()
```

* goalie \
striker

* Ada \
Ben

* Ada goalie \
Ben striker

* An error, because you cannot loop over a dictionary

**Correct Answer:**  

Ada \
Ben

**Explanation:**

When you loop over a Python dictionary directly, it loops through its keys by default.

```
team = {"Ada": "goalie", "Ben": "striker"}

for player in team:
    print(player)
```

* First iteration: player = "Ada"
* Second iteration: player = "Ben"

**Remember:**

* `for player in team `→ keys
* `team.values()` → values
* `team.items()` → keys and values together.

---

### Example 02 - Add or Replace

What does this program print?

```
def main():
    stock = {"apples": 3}
    stock["pears"] = 5
    stock["apples"] = 10
    print(len(stock))
    print(stock["apples"])

if __name__ == "__main__":
    main()
```

* 2 \
10

* 3 \
10

* 2 \
3

* 3 \
13

**Correct Answer:**  

2 \
10

**Explanation:**

* ```stock = {"apples": 3}``` \
One key: "apples" with value 3.

* ```stock["pears"] = 5``` \
Adds a new key "pears" with value 5.\
Now there are 2 keys.

* ```stock["apples"] = 10```\
Updates the existing apples value from 3 to 10.\
Does not add a new key.

* ```print(len(stock))```\
Prints 2 because there are two keys.

* ```print(stock["apples"])```\
Prints 10.

Final output:
```
2
10
```

---

### Example 03 - Nicknames

This program asks for names and nicknames until you press enter. Run it, give two people nicknames, then press enter.

```python
def main():
    nicknames = {}
    name = input("Name: ")
    while name != "":
        nickname = input(f"Nickname for {name}: ")
        nicknames[name] = nickname
        name = input("Name: ")
    print(f"Nicknames saved: {len(nicknames)}")
    for name in nicknames:
        print(f"{name} goes by {nicknames[name]}")

if __name__ == "__main__":
    main()
```

Output:

```
Name: Ana
Nickname for Ana: Annie
Name: Ben
Nickname for Ben: Benny
Name: Cleo
Nickname for Cleo: C
Name:
Nicknames saved: 3
Ana goes by Annie
Ben goes by Benny
Cleo goes by C
```