## elif, and, or, not

* [CiPX: if/elif, and/or/not](https://youtu.be/i-DX2kwsxVo?si=_9SGSoD55RXXfj5D)

### Example 01 - Only One Runs

What does this program print?

```python
def main():
    score = 85
    if score >= 90:
        print("A")
    elif score >= 80:
        print("B")
    elif score >= 70:
        print("C")
    else:
        print("Keep practicing")

if __name__ == "__main__":
    main()
```

* B \
C
* A
* B
* B \
C \
Keep practicing

#### Explanation:

The value of `score` is `85`.

Python checks the conditions from top to bottom:

1. `score >= 90` → `85 >= 90` → False.
2. `score >= 80` → `85 >= 80` → True.
3. Python executes `print("B")` and skips the remaining conditions.

#### Correct Answer:

```
B
```

***Remember:*** In an `if / elif / else` structure, only the first condition that evaluates to `True` gets executed.

---


### Example 02 - Two Ifs

What does this program print?

```python
def main():
    temp = 30
    if temp > 25:
        print("hot")
    if temp > 15:
        print("warm")
    else:
        print("cold")

if __name__ == "__main__":
    main()
```

* hot \
warm
* hot \
cold
* hot
* warm

#### Explanation:

The important thing here is that there are two separate `if` statements, not an `if / elif` structure.

Let's check them one by one:

1. `temp > 25` → `30 > 25` → True, so it prints `"hot"`.
2. `temp > 15` → `30 > 15` → True, so it prints `"warm"`.
3. The `else` belongs to the second `if`. Since that condition is True, `"cold"` is skipped.

#### Correct Answer:

```
hot
warm
```

***Remember:***

- Two separate `if` statements can both execute.
- An `else` belongs to its nearest unmatched `if`.
- `if / elif / else` executes only one matching branch.

---

### Example 03 - and, or, not

What does this program print?

```python
def main():
    kind = "dog"
    age = 4
    if kind == "dog" and age < 2:
        print("puppy")
    elif not kind == "cat":
        print("not a cat")
    else:
        print("cat")

if __name__ == "__main__":
    main()
```

* puppy
* puppy \
not a cat
* cat
* not a cat


#### Explanation:

Given:

```python
kind = "dog"
age = 4
```

Python checks the conditions from top to bottom:

1. `kind == "dog" and age < 2`
   - `"dog" == "dog"` → True
   - `4 < 2` → False
   - True AND False = False
2. `not kind == "cat"`
   - `"dog" == "cat"` → False
   - `not False` → True
3. Python executes:


```python
print("not a cat")
```

#### Correct Answer:

```
not a cat
```

***Remember:***

- `and` → Both conditions must be True.
- `not` → Reverses True to False and False to True.
- `elif` runs only when the preceding `if` condition is False.


---

### Example 04 - A Sneaky Bug

What does this program print?

```python
def main():
    kind = "bird"
    if kind == "cat" or "dog":
        print("cat or dog")
    else:
        print("something else")

if __name__ == "__main__":
    main()
```

* something else
* cat or dog
* An error, because "dog" is not a comparison
* Nothing

#### Explanation:

This is a common Python mistake involving the `or` operator.

The condition is:

```python
if kind == "cat" or "dog":
```

Python evaluates it as:

```python
if (kind == "cat") or ("dog"):
```

Step by step:

1. `kind == "cat"` → False (because kind is `"bird"`).
2. `"dog"` → True (because non-empty strings are truthy).
3. `False or True` → True.

Therefore, Python executes:

```python
print("cat or dog")
```

#### Correct Answer:

```text
cat or dog
```


---

### Example 05 - Shelter Report

What does this program print?

```python
def main():
    pets = [
        {"name": "Mochi", "kind": "cat", "age": 3},
        {"name": "Biscuit", "kind": "dog", "age": 1},
        {"name": "Kiwi", "kind": "bird", "age": 6},
    ]
    for pet in pets:
        name = pet["name"]
        if pet["kind"] == "dog" and pet["age"] < 2:
            print(f"{name} is a puppy!")
        elif pet["kind"] == "cat" or pet["kind"] == "dog":
            print(f"{name} needs a walk or a nap.")
        else:
            print(f"{name} is something else.")

if __name__ == "__main__":
    main()
```

* Mochi needs a walk or a nap.  \
Biscuit needs a walk or a nap. \
Kiwi is something else.

* Mochi needs a walk or a nap. \
Biscuit is a puppy! \
Kiwi is something else.

* Mochi needs a walk or a nap. \
Biscuit is a puppy! \
Biscuit needs a walk or a nap. \
Kiwi is something else.

* Mochi needs a walk or a nap. \
Biscuit is a puppy! \
Kiwi needs a walk or a nap.

#### Explanation:

The `for` loop checks each pet one by one.

1. Mochi

- Kind = `"cat"`
- The first condition (dog and age less than 2) → False.
- The `elif` condition (cat or dog) → True.

Prints:

```text
Mochi needs a walk or a nap.
```

2. Biscuit

- Kind = `"dog"`
- Age = `1`
- First condition: `pet["kind"] == "dog" and pet["age"] < 2`
- True and True = True.

Prints:

```text
Biscuit is a puppy!
```

3. Kiwi

- Kind = `"bird"`
- First condition → False.
- `elif` condition → False.
- Executes `else`.

Prints:

```text
Kiwi is something else.
```

#### Correct Answer:

```text
Mochi needs a walk or a nap.
Biscuit is a puppy!
Kiwi is something else.
```

***Remember:*** In an `if / elif / else` structure, Python executes only the first matching condition. Once a condition is True, it skips the remaining branches.

----

### Example 06 - Biscuit Grows Up

Biscuit is 4 now. What does this program print?

```python
def main():
    pets = [
        {"name": "Mochi", "kind": "cat", "age": 3},
        {"name": "Biscuit", "kind": "dog", "age": 4},
        {"name": "Kiwi", "kind": "bird", "age": 6},
    ]
    for pet in pets:
        name = pet["name"]
        if pet["kind"] == "dog" and pet["age"] < 2:
            print(f"{name} is a puppy!")
        elif pet["kind"] == "cat" or pet["kind"] == "dog":
            print(f"{name} needs a walk or a nap.")
        else:
            print(f"{name} is something else.")

if __name__ == "__main__":
    main()
```

* Mochi needs a walk or a nap.\
Biscuit is a dog.\
Kiwi is something else.

* Mochi needs a walk or a nap.\
Biscuit is a puppy!\
Kiwi is something else.

* Mochi needs a walk or a nap.\
Kiwi is something else.

* Mochi needs a walk or a nap.\
Biscuit needs a walk or a nap.\
Kiwi is something else.

#### Explanation:

Let's check each pet:

1. Mochi

- Kind = `"cat"`, age = 3.
- First condition → False.
- `elif` condition → True.
- Prints: `Mochi needs a walk or a nap.`

2. Biscuit

- Kind = `"dog"`, age = 4.
- First condition: `age < 2` → False.
- `elif` condition: dog or cat → True.
- Prints: `Biscuit needs a walk or a nap.`

3. Kiwi

- Kind = `"bird"`.
- First condition → False.
- `elif` condition → False.
- Executes `else`.

Prints: `Kiwi is something else.`


#### Correct Answer:

```text
Mochi needs a walk or a nap.
Biscuit needs a walk or a nap.
Kiwi is something else.
```

***Remember:*** Since Biscuit is now 4, the puppy condition (`age < 2`) is False, but Biscuit still satisfies the `elif` condition because its kind is `"dog"`.

---