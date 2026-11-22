## Lists of Dictionaries

* [CiPX: Lists of Dictionaries](https://youtu.be/hjFIWOE43IA?si=6GxSeP5fqDIEsAHA)

### Example 01 - Index, Then Key

What does this program print?

```
def main():
    pets = [
        {"name": "Mochi", "kind": "cat", "age": 3},
        {"name": "Biscuit", "kind": "dog", "age": 1},
        {"name": "Kiwi", "kind": "bird", "age": 6},
    ]
    print(pets[1]["name"])

if __name__ == "__main__":
    main()
```

* Biscuit
* An error, because pets is a list
* Mochi
* {"name": "Biscuit", "kind": "dog", "age": 1}

#### Explanation: 
→ `pets` is a list containing three dictionaries.\
→ `pets[1]` accesses the second dictionary (indexing starts at 0).\
→ `pets[1]["name"]` retrieves the value of the `"name"` key.

#### Correct Answer:  

```
Biscuit
```

---

### Example 02 - How Long?

What does this program print?

```
def main():
    pets = [
        {"name": "Mochi", "kind": "cat", "age": 3},
        {"name": "Kiwi", "kind": "bird", "age": 6},
    ]
    print(len(pets))
    print(len(pets[0]))

if __name__ == "__main__":
    main()
```

* 6 \
3

* 3 \
2

* 2 \
3

* 2 \
2

#### Explanation: 
→ `len(pets)` → Returns the number of dictionaries in the list. There are 2 dictionaries.

→ `len(pets[0])` → Returns the number of key-value pairs in the first dictionary. There are 3 (name, kind, age).

#### Correct Answer:  
```
2 
3
```

#### Remember:
* len(list) -- counts the number of elements in a list.
* len(dictionary) -- counts the number of keys in a dictionary.
---

### Example 03 - Each Time Around

What does this program print?

```
def main():
    pets = [
        {"name": "Mochi", "kind": "cat", "age": 3},
        {"name": "Biscuit", "kind": "dog", "age": 1},
        {"name": "Kiwi", "kind": "bird", "age": 6},
    ]
    for pet in pets:
        print(pet["kind"])

if __name__ == "__main__":
    main()
```

* Mochi\
Biscuit\
Kiwi

* kind\
kind\
kind

* cat\
dog\
bird

* An error, because pet is a list

#### Explanation: 
→ `for pet in pets:` loops through each dictionary in the `pets` list.

→ `pet["kind"]` retrieves the value associated with the `"kind"` key.

→ Each iteration prints the pet's kind.

#### Correct Answer:  

```
cat
dog
bird
```

***Remember:***
A `for` loop iterates through each item in a list, and you can access dictionary values using their keys, such as `pet["kind"]`.

---


### Example 04 - Count the Cats

This program should count the cats in the shelter, but the loop is empty. Inside the loop, which line checks whether this pet is a cat?

```
def main():
    pets = [
        {"name": "Mochi", "kind": "cat"},
        {"name": "Biscuit", "kind": "dog"},
        {"name": "Tofu", "kind": "cat"},
    ]
    count = 0
    for pet in pets:
        if pet["kind"] == "cat":
            count += 1
    print(f"The shelter has {count} cats.")

if __name__ == "__main__":
    main()
```

---

### Example 05 - Shelter Intake

This program asks for pets until you press enter. Run it and add three pets.

```
def make_pet(name, kind):
    return {"name": name, "kind": kind}


def main():
    pets = []
    name = input("Pet name: ")
    while name != "":
        kind = input(f"What kind of animal is {name}? ")
        pets.append(make_pet(name, kind))
        name = input("Pet name: ")
    print(f"The shelter has {len(pets)} pets.")
    for pet in pets:
        print(pet["name"])

if __name__ == "__main__":
    main()
```

Output:
```
Pet name: Mochi
What kind of animal is Mochi? cat
Pet name: Biscuit
What kind of animal is Biscuit? dog
Pet name: Kiwi
What kind of animal is Kiwi? bird
Pet name: 
The shelter has 3 pets.
Mochi
Biscuit
Kiwi
```


