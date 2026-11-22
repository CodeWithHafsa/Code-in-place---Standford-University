## Random Numbers

* [CiPX: Random](https://youtu.be/xhttliU9rks?si=AGP4cjEjNSyCwGuD)
* [CiPX: Random - Guess My Number](https://youtu.be/jvetvVGSkRs?si=z8ios-eHt3iSXr7t)
* [CiPX - Random (Optional) Estimate Pi](https://youtu.be/Q48lBeagAvk?si=Bdd-dnGBCOaPke7l)

#### Question - Waht numbers can appear?
What is the largest number randint(1, 6) can return? Enter a whole number.

**Answer**: 6


---

### Example 01 - Two Dice

```python
from random import randint

def main():
    # Add the two dice rolls below.
    die1 = randint(1, 6)
    print(f"First die: {die1}")
    die2 = randint(1, 6)
    print(f"Second die: {die2}")
    print(f"Total: {die1 + die2}")

if __name__ == "__main__":
    main()
```

Output

```
% python main.py
First die: 4
Second die: 3
Total: 7
% python main.py
First die: 2
Second die: 4
Total: 6
```

---

#### Question - Should the secret number change?
In Guess My Number, should the secret number change after each guess? Choose Yes or No.

* Yes
* No

**Answer**: No

---

### Example 02 - Roll Until Six

Add a while loop that keeps going until the roll is 6.

```python
from random import randint

def main():
    roll = None
    print("Rolling until we get a 6...")
    while roll != 6:
        roll = randint(1, 6)
        print('Roll:', roll)
    print("Last roll:", roll)

if __name__ == "__main__":
    main()
```

Output:

```
% python main.py
Rolling until we get a 6...
Roll: 5
Roll: 6
Last roll: 6
```