## Slices

* [CiPX: Slices of Lists](https://youtu.be/z8T7v3KgCcQ?si=3PL9FoZymlXHrtzq)

### Example 01 - Slice It

What does this program print?

```python
def main():
    nums = [10, 20, 30, 40, 50]
    print(nums[1:3])

if __name__ == "__main__":
    main()
```

* [30, 40]
* [10, 20, 30]
* [20, 30]
* [20, 30, 40]


#### Explanation:

In Python, list slicing uses this syntax:

```python
list[start:end]
```

- `start = 1` → Starts at index 1 (value `20`).
- `end = 3` → Stops before index 3 (value `40`).

So it includes:

- Index 1 → `20`
- Index 2 → `30`

#### Correct Answer:

```
[20, 30]
```

***Remember:*** Python slicing includes the starting index but excludes the ending index.

----

### Example 02 - Leave Off an End

What does this program print?

```python
def main():
    line = ["Ana", "Ben", "Cleo", "Dev", "Eli"]
    print(line[:2])
    print(line[2:])

if __name__ == "__main__":
    main()
```

* ['Ana', 'Ben'] \
['Ben', 'Cleo', 'Dev', 'Eli']

* ['Ana', 'Ben', 'Cleo'] \
['Cleo', 'Dev', 'Eli']
 
* ['Ana', 'Ben'] \
['Cleo', 'Dev', 'Eli']

* ['Ana', 'Ben'] \
['Dev', 'Eli']

#### Explanation:

Python list slicing:

- `line[:2]` → Takes elements from the beginning up to (but not including) index 2.
- `line[2:]` → Takes elements from index 2 to the end.

So:

- `line[:2]` → `['Ana', 'Ben']`
- `line[2:]` → `['Cleo', 'Dev', 'Eli']`

#### Correct Answer:

```
['Ana', 'Ben']
['Cleo', 'Dev', 'Eli']
```

***Remember:***

- `[:n]` → First `n` elements.
- `[n:]` → From index `n` to the end.

----

### Example 03 - All Except the Last Two

What does this program print?

```python
def main():
    nums = [10, 20, 30, 40, 50]
    print(nums[:len(nums) - 2])

if __name__ == "__main__":
    main()
```

* [10, 20, 30]
* [30]
* [10, 20, 30, 40]
* [40, 50]

#### Explanation:

Let's break it down:

```python
nums = [10, 20, 30, 40, 50]
len(nums)  # 5
len(nums) - 2  # 3
```

Now the slicing becomes:

```python
nums[:3]
```

This takes elements from the beginning up to (but not including) index 3.

- Index 0 → 10
- Index 1 → 20
- Index 2 → 30

#### Correct Answer:

```
[10, 20, 30]
```

***Remember:*** `nums[:3]` returns the first 3 elements because the ending index is excluded.

---


### Example 04 - Glue them together

What does this program print?

```python
def main():
    nums = [10, 20, 30, 40, 50]
    print([nums[0]] + nums[3:])

if __name__ == "__main__":
    main()
```

* [40, 50]
* [10, 30, 40, 50]
* An error, because you cannot add two lists
* [10, 40, 50]

#### Explanation:

Let's break down the expression:

```python
[nums[0]] + nums[3:]
```

1. `nums[0]` → Gets the first element: `10`.
2. `[nums[0]]` → Creates a list: `[10]`.
3. `nums[3:]` → Gets elements from index 3 to the end: `[40, 50]`.
4. `+` → Combines (concatenates) the two lists.

So:

```python
[10] + [40, 50]
```

#### Correct Answer:

```text
[10, 40, 50]
```

***Remember:***

- `+` can concatenate two lists in Python.
- Both operands must be lists for list concatenation.

---

### Example 05 - One Item or a List of One

What does this program print?

```python
def main():
    words = ["hi", "there", "friend"]
    print(words[0] + words[2:])

if __name__ == "__main__":
    main()
```

* hifriend
* An error, because words[0] is a string, not a list
* ['hi', 'friend']
* ['friend']

#### Explanation:

Let's break it down:

```python
words = ["hi", "there", "friend"]
```

- `words[0]` → `"hi"` (a string).
- `words[2:]` → `["friend"]` (a list).

The expression becomes:

```python
"hi" + ["friend"]
```

Python cannot concatenate a string and a list using `+`. This causes a TypeError.

#### Correct answer: 

```
An error, because `words[0]` is a string, not a list.
```

***Remember:***

- String + String = String
- List + List = List
- String + List = TypeError

---

### Example 06 - To-Do-List

Here is your to-do list for today. Run it.

```python
def main():
    todo = ["walk dog", "buy milk", "call Ana", "wash car", "nap", "read"]
    todo = todo[:len(todo) - 2]
    todo = [todo[0]] + todo[3:]
    print(todo)

if __name__ == "__main__":
    main()
```

Output:

```
['walk dog', 'wash car']
```