# Floating Point
## Quest
This section will cover a picky detail about how computers store numerical values. While you might not encounter this specific problem very often, it's important to be aware of it when writing your program to avoid bugs. You know that Python has int for whole numbers and float for decimals. 

Floats, or **floating-point** values as they are officially called, get their name from the way the decimal point can *float* to different positions in the number, changing the value that is represented. float values can be written as a regular decimal, like 3.14, or in scientific notation with the letter ‘e’ or ‘E’, to represent the order of magnitude like this:

> 1.2e23 ⇒ 1.2 * 10^23 \
1.0e-4 ⇒ 1.0 * 10^-4

Your computer only has so much memory. If you have a number like ⅓, storing that as a float would require an infinite amount of memory (0.333333333333…). This means we can only store a value like ⅓ as an approximation. We talk about the **precision** of a floating-point number as how many decimal places of the true value are accurately recorded.
* 0.3 is an approximation of ⅓ 
* 0.33 is a more precise approximation
* 0.333 is an even more precise approximation

Your computer can store decimal values very precisely, up to 17 decimal places of precision, but this means there are some values too small to be stored in a float (think of something like 1.0e1000000000).

When programming, you might use a math expression to calculate a decimal value. However, if the result of that expression is a value too small to be stored accurately, Python will **truncate** or cut off the tail end of the value, resulting in a loss of precision. This can lead to all sorts of weird quirks when doing arithmetic, mainly resulting from the stored value being slightly greater or less than the true value: 

```python
$ python
>>> 0.1 * 3
0.30000000000000004
```

Check out what happens when we run this program. The code continuously divides a value by 10 until, eventually, Python can’t store so much precision and just rounds it down.

```python
def main():
   value = 1
   while value > 0:
      print(value)
      value /= 10
   print(value)

if __name__ == '__main__':
	main()
```
=> Run >_Show

When Python truncates the end of a floating-point number, the result is a value incredibly close to but not quite exactly the desired value. The difference between the approximation is small, sure, but it could still be disastrous for your code. Below is an example of common errors related to floating-point precision:

```python
def main():
    # The actual value stored in this variable is 0
    denominator = 1E-1000000

    # ZeroDivisionError (You can't divide by 0)
    value = 10 / denominator

    if denominator == 0:
        # This code should never run because we get an error above
        print("Something has gone horribly wrong :(")

if __name__ == '__main__':
    main()
```
=> Run >_Show