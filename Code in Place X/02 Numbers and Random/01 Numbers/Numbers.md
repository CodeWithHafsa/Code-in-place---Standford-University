## Numbers

*Sierra Wang and Juliette Woodrow*

* [CiPX: Numbers](https://youtu.be/qB6-bzeCGrU?si=5PUkwpE6fmicmXtw)
* [CiPX: Numbers 2](https://youtu.be/vrCKcMDacvA?si=OtPxtd10-OPLZ4C0)


### Example 01 - One Plus Two

What does this program print?

```python
main.py
def main():
    x = "1"
    y = "2"
    z = x + y
    print(z)

if __name__ == "__main__":
    main()
```

1. 3
2. 12
3. 1 + 2
4. Nothing. This is an error.

**Answer:** Option 2 - 12

---

### Example 02 - Mars Weight

Mars has about 37.8% as much gravity as Earth. Add this line to compute what the user would weigh there.

```python
EARTH_TO_MARS_WEIGHT_RATIO = 0.378

def main():
    weight_on_earth = input("Enter a weight on Earth: ")
    weight_on_earth = float(weight_on_earth)
    weight_on_mars = weight_on_earth * EARTH_TO_MARS_WEIGHT_RATIO
    weight_on_mars = round(weight_on_mars, 2)
    print(f"The equivalent weight on Mars: {weight_on_mars}")

if __name__ == "__main__":
    main()
```

Output:
```
% python main.py
Enter a weight on Earth: 120
The equivalent weight on Mars: 45.36
% python main.py
Enter a weight on Earth: 10
The equivalent weight on Mars: 3.7800000000000002
% python main.py
Enter a weight on Earth: 10
The equivalent weight on Mars: 3.78
```

---

### Example 03 - Order of Operations

What does this program print?

```python
main.py
def main():
    x = 10
    y = 3
    print(x + y * 2)

if __name__ == "__main__":
    main()
```

1. 26
2. 16
3. 20
4. 13

**Answer:** Option 2 - 16

---

### Example 04 - Leftovers

17 candies are shared evenly between 5 kids. What does this print?

```python
main.py
def main():
    candies = 17
    kids = 5
    leftovers = candies % kids
    print(leftovers)

if __name__ == "__main__":
    main()
```

1. 3
2. 2
3. 3.4
4. 85

**Answer:** Option 2 => 2

---

### Example 05 - Countdown

```python
def main():
    counter = int(input("Enter a starting number: "))

    while counter > 0:
        print(counter)
        counter = counter - 1

    print("Blast off!!!")
```

Output:

```
% python main.py
Enter a starting number: 5
5
4
3
2
1
Blast off!!!

% python main.py
Enter a starting number: 0
Blast off!!!
```