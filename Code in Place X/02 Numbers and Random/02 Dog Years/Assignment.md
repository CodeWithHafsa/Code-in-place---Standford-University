## Dog Years

## Assignment
Write a program which asks a user to input an age in calendar years, and converts it to the equivalent age in dog years.

Dogs have different lifespans than humans. Thus their age is sometimes reported in "dog years" which are scaled to be comparable to human ages. On average, every calendar year is equal to **7.18 dog years**. To convert 3 calendar years to dog years, you multiply 3 * 7.18 to get 21.54 dog years. That means, if your dog is 3 years old, they're past their teenage years!

Your program will take in an age in calendar years, multiply that age by 7.18 and report the resulting dog years. Here's a sample run of the program:

```
Enter an age in calendar years: 10
That's 71.8 in dog years!
```

#### Answer

```python
# Each year for a human is like 7.18 years for a dog
DOG_YRS_MULTIPLIER = 7.18  # Each year for a human is like 7.18 years for a dog

def main():
    # Get how old someone is in human years. Make sure to cast it to a float!
    human_age = float(input("Enter an age in calendar years: "))

    # Convert the human years to dog years using a constant multiplier and print the result out
    print("That's " + str(human_age * DOG_YRS_MULTIPLIER) + " in dog years!")

if __name__ == '__main__':
    main()
```