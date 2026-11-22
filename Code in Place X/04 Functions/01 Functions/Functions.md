## Functions

* [CiPX: Functions](https://youtu.be/4p4ffo6PP0w?si=uGXVZkOQII9mzC_F)

### Example 01 - Does it Run?

What does this program print?

```python
def greet():
    print("Hello!")

def main():
    print("Start")

if __name__ == "__main__":
    main()
```

* Hello! \
Start

* Start \
Hello!

* Start

* Hello!

**Correct Answer:** Start

**Explanation:**

- `greet()` is defined but never called.
- `main()` is called because `__name__ == "__main__"` is true.
- Therefore, only `print("Start")` executes.

---

### Example 02 - Nothing comes back

What does this program print?

```python
def price(nights):
    print(nights * 120)

def main():
    total = price(3)
    print(f"Your total is ${total}.")

if __name__ == "__main__":
    main()
```

* 360 \
Your total is $360.

* 360 \
Your total is $None.

* Your total is $360.

* An error, because you can't store the result of a function that prints

**Correct Answer:** 
```text
360
Your total is $None.
```

**Explanation:**

1. `price(3)` calculates `3 * 120` and prints `360`.
2. However, the `price()` function does not have a `return` statement, so it returns `None` by default.
3. Therefore, `total = price(3)` assigns `None` to `total`.
4. The final print statement displays `Your total is $None.`

Remember: `print()` displays a value, while `return` sends a value back to the caller.

---

### Example 03 - Swap the labels

Read this program first. main passes a variable called `human_age` to `dog_years`, but `dog_years` calls its parameter `age`. Run it and enter 10.

```python
def dog_years(age):
    return age * 7

def main():
    human_age = int(input("How old are you? "))
    print(f"In dog years you are {dog_years(human_age)}!")

if __name__ == "__main__":
    main()
```

Output:

```
How old are you? 10
In dog years you are 70!
```

---

### Example 04 - Same name, Different box

What does this program print?

```python
def shout(word):
    return word.upper() + "!"

def main():
    word = "quiet"
    print(shout("loud"))

if __name__ == "__main__":
    main()
```

* LOUD!
* QUIET!
* LOUD! QUIET!
* An error, because word is defined twice

**Correct answer:** LOUD!

**Explanation**

1. `shout("loud")` passes `"loud"` into the function.
2. `word.upper()` converts `"loud"` to uppercase: `"LOUD"`.
3. `+ "!"` adds an exclamation mark.
4. `print()` displays the returned value.

The variable `word = "quiet"` inside `main()` is not used because the function receives `"loud"` as its argument.

----

### Example 05 - Inorder

What does this program print?

```python
def describe(name, age):
    return f"{name} is {age}"

def main():
    print(describe(30, "Ada"))

if __name__ == "__main__":
    main()
```

* Ada is 30
* 30 is Ada
* An error, because 30 is not a name
* Nothing

**Correct answer:** 30 is Ada


**Explanation**

1. `describe(30, "Ada")` passes `30` as `name` and `"Ada"` as `age`.
2. Python assigns arguments based on their position, not their meaning.
3. The f-string combines them into `"30 is Ada"`.

---

### Example 06 - Initials

he function `all_initials(team)` goes through each name in the list and creates a string `result` with the first initial of each name, so this should print out `ABC`. Run it and see what it actually prints!

```python
def initial(name):
    return f"{name[0]}."

def all_initials(team):
    result = ""
    for name in team:
        result = result + initial(name)
    return result

def main():
    team = ["Ada", "Ben", "Cleo"]
    print(all_initials(team))

if __name__ == "__main__":
    main()
```

Output:
```
A.B.C
```

---

### Example 07 - Two ways out

What does this program print?

```python
def check(n):
    if n > 10:
        return "big"
    return "small"

def main():
    print(check(50))

if __name__ == "__main__":
    main()
```

* big
* small
* bigsmall
* big \
small

**Correct answer:** big 

**Explanation:**
1. `check(50)` passes `50` into the function.
2. The condition `n > 10` is checked.
3. Since `50 > 10` is `True`, the function returns `"big"`.
4. `print()` displays the returned value.

---

### Example 08 - A question, answered

What does this program print?

```python
def is_long(word):
    return len(word) > 5

def main():
    if is_long("hello"):
        print("long word")
    else:
        print("short word")

if __name__ == "__main__":
    main()
```

* long word
* short word
* True
* An error, because a function call can't be an if condition


**Correct answer:** short word

**Explanation:**

1. `is_long("hello")` checks the length of `"hello"`.
2. `len("hello")` is `5`.
3. `5 > 5` is `False`.
4. Therefore, the `else` block executes.

---

### Example 09 - Zed's snack check

Python has a handy way to check if a letter is inside a string: the word in. For example, "a" in "cat" is True, and "z" in "cat" is False. Zed the robot only eats foods with a z in them. What does this program print?

```python
def will_eat(food):
    return "z" in food

def main():
    print(will_eat("pizza"))
    print(will_eat("pasta"))

if __name__ == "__main__":
    main()
```

* True \
False
* False \
True
* True \
True
* An error, because in only works in a for loop

**Correct answer:**  
```text
True
False
```

**Explanation:**

1. `will_eat("pizza")` checks whether `"z"` is in `"pizza"`. It is, so it returns `True`.
2. `will_eat("pasta")` checks whether `"z"` is in `"pasta"`. It isn't, so it returns `False`.

Remember: The `in` keyword checks whether something exists inside a string.

