## Nested Data

* [CiPX: Nested Data](https://youtu.be/ngk3HOfZVDk?si=mWrKkNIvnrhbyHhc)


### Example 01 - Key, Then Index

What does this program print?

```python
def main():
    by_kind = {
        "cat": ["Mochi", "Tofu"],
        "dog": ["Biscuit"],
    }
    print(by_kind["cat"][1])

if __name__ == "__main__":
    main()
```

* Tofu
* Biscuit
* Mochi
* ['Mochi', 'Tofu']

#### Explanation:

- `by_kind["cat"]` retrieves the list `["Mochi", "Tofu"]`.
- `[1]` selects the second item in the list.
- The second item is `"Tofu"`.

### Correct Answer:

```
Tofu
```

***Remember:*** You can access a list inside a dictionary by using the dictionary key first, then the list index:

```python
dictionary["key"][index]
```

----

### Example 02 - Key, Then Key

What does this program print?

```python
def main():
    shelter = {
        "Mochi": {"kind": "cat", "age": 3},
        "Kiwi": {"kind": "bird", "age": 6},
    }
    print(shelter["Kiwi"]["age"])

if __name__ == "__main__":
    main()
```

* 3
* An error, because "Kiwi" is not an index
* {'kind': 'bird', 'age': 6}
* 6

#### Explanation:

→ `shelter["Kiwi"]` accesses the dictionary for Kiwi. \
→ `["age"]` retrieves Kiwi's age.\
→ Kiwi's age is `6`.

#### Correct Answer:

```
6
```

***Remember:*** You can access nested dictionaries using multiple keys:

```python
dictionary["outer_key"]["inner_key"]
```

This is called **nested dictionary access**.

---

### Example 03 - One Bracket at a Time

What does this program print?

```python
def main():
    shelter = {
        "cats": [
            {"name": "Mochi", "toys": ["ball", "mouse"]},
            {"name": "Tofu", "toys": ["string"]},
        ],
    }
    print(shelter["cats"][0]["toys"][1])

if __name__ == "__main__":
    main()
```

* ball
* mouse
* ['ball', 'mouse']
* string

#### Explanation:

- `shelter["cats"][0]` selects the first cat, Mochi.
- `["toys"]` selects `["ball", "mouse"]`.
- `[1]` selects the second item in the list, which is `"mouse"`.

#### Correct Answer:

```python
mouse
```

---

### Example 04 - Loop Over the Inside

What does this program print?

```python
def main():
    by_kind = {
        "cat": ["Mochi", "Tofu"],
        "dog": ["Biscuit", "Rex"],
    }
    for name in by_kind["dog"]:
        print(name)

if __name__ == "__main__":
    main()
```

* cat \
dog 
* Biscuit \
Rex
* dog
* ['Biscuit', 'Rex']

#### Explanation:

- `by_kind["dog"]` retrieves the list `["Biscuit", "Rex"]`.
- The `for` loop goes through each name in the list.
- `print(name)` prints each name on a separate line.

#### Correct answer:

```text
Biscuit
Rex
```

---

### Example 05 - Change the Inside

What does this program print?

```python
def main():
    shelter = {
        "Mochi": {"kind": "cat", "age": 3},
        "Kiwi": {"kind": "bird", "age": 6},
    }
    shelter["Kiwi"]["age"] = 7
    print(shelter["Kiwi"])

if __name__ == "__main__":
    main()
```

* 7
* An error, because shelter has no key "age"
* {'kind': 'bird', 'age': 6}
* {'kind': 'bird', 'age': 7}

#### Explanation:

- `shelter["Kiwi"]` accesses Kiwi's dictionary.
- `["age"] = 7` updates Kiwi's age from 6 to 7.
- `print(shelter["Kiwi"])` prints the entire updated dictionary.

#### Correct answer: 

```python
{'kind': 'bird', 'age': 7}
```

---

### Example 06 - New Arrivals

The shelter keeps a list of names for each kind of animal. A new dog just arrived. Run it and name the dog Rex.

```python
def main():
    by_kind = {
        "cat": ["Mochi", "Tofu", "Pip"],
        "dog": ["Biscuit"],
    }
    name = input("New dog's name: ")
    by_kind["dog"].append(name)
    print(by_kind["dog"])
    print(len(by_kind["cat"]))

if __name__ == "__main__":
    main()
```

Output:

```
New dog's name: Rex
['Biscuit', 'Rex']
```

### Example 07 - Shelter Records

Now the shelter keeps a dictionary for each pet, inside one big dictionary. Run it.

```python
def main():
    shelter = {
        "Mochi": {"kind": "cat", "age": 3},
        "Biscuit": {"kind": "dog", "age": 1},
        "Kiwi": {"kind": "bird", "age": 6},
    }
    shelter["Biscuit"]["age"] += 1
    for name in shelter:
        pet = shelter[name]
        age = pet["age"]
        print(f"{name} is {age}")

if __name__ == "__main__":
    main()
```

Output:

```
Mochi is 3
Biscuit is 2
Kiwi is 6
```