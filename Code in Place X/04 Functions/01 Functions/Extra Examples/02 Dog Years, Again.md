## Dog Years, Again

Your program should:
1. Define a function `dog_years(age)` that **returns** that age multiplied by 7.
2. Ask the user how old they are, as a whole number.
3. Print their age in dog years.
4. Print what their age in dog years will be next year.

Here is example output from running this program:

```
How old are you? 10
You are 70 in dog years.
Next year you will be 77.
```

The last line is the interesting one. You can write `dog_years(age + 1)`: Python works out the addition first, and hands the answer through the door. An argument does not have to be a plain variable. Anything that produces a value will do.

Nothing here is new except the shape. The multiplication is the same one you wrote in week two; it has just moved inside a function with a name that says what it does.


### Answer

```python
def dog_years(age):
    return age * 7

def main():
    age = int(input("How old are you? "))
    print(f"You are {dog_years(age)} in dog years.")
    age_next_year = age + 1
    print(f"Next year you will be {dog_years(age_next_year)}.")

if __name__ == "__main__":
    main()
```