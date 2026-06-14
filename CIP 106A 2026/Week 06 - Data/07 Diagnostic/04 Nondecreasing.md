## Assignment
(Suggested 15 mins)
![alt text](image-1.png)
*A simple way to achieve great things in life is to make small forward progress every day. Non-decreasing progress is one of the principles behind modern AI.*

Write a program that asks the user to enter a sequence of "non-decreasing" numbers one at a time. Numbers are non-decreasing if each number is greater than or equal to the last.

When the user enters a number which is smaller than their previously entered value, the program is over. Tell the user how long their sequence was.

---
Here is an example (values entered by the user are bolded and italicized for clarity, but they don't need to be in your program):

Enter a sequence of non-decreasing numbers. 

Enter num: -1 
Enter num: 0 
Enter num: 1 
Enter num: 3.12 
Enter num: 99 
Enter num: 99 
Enter num: 42 
Thanks for playing! 
Sequence length: 6


## A few notes:
* Include the **intro message**, `Enter a sequence of non-decreasing numbers.`
* Include the **exit message**, `Thanks for playing!`.
* Include the **exit message**, `Sequence length:` followed by the length of the sequence.
* The length of the sequence does not include the very last number entered as it is "decreasing"
* Your program should accept floating point numbers.
* The sequence only ends when one number is strictly less than the last.
* You do not have to handle the case where the user enters a value which is not a number (say "abc").
* The user can start with any number, positive or negative.

**Note** that the shortest possible sequence is 1. A sequence with a single number can't be decreasing. A sequence with two numbers can be decreasing.
## Concepts

This problem mixes variables with control flow. This problem required you to use variables in new ways, on the. fly. If you were able to solve it, that is certainly a good sign that you have mastered the core concepts. If you knew all of the concepts (loops, variables, input and print) and your challenge was putting it together I have good news, with practice that will become natural.

In class we went over the guess number program which was our introduction to variables with control flow. If this problem was challenging, we recommend reviewing that lesson. 

## More examples:
Enter a sequence of non-decreasing numbers. 

```
Enter num: 5 
Enter num: 4 
Thanks for playing! 
Sequence length: 1
```


Enter a sequence of non-decreasing numbers. 

```
Enter num: 1 
Enter num: 2.7 
Enter num: 3 
Enter num: 4 
Enter num: 2 
Thanks for playing! 
Sequence length: 4
```


Enter a sequence of non-decreasing numbers. 

```
Enter num: -5 
Enter num: -5
Enter num: -5 
Enter num: -6 
Thanks for playing! 
Sequence length: 3
```

---

**Given Code**

```python
def main():
    # TODO write your solution here
    pass 


if __name__ == "__main__":
    main()
```


## Answer

```python
def main():
    print("Enter a sequence of non-decreasing numbers.")

    count = 0

    prev = float(input("Enter num: "))
    count += 1

    while True:
        current = float(input("Enter num: "))

        if current < prev:
            break

        count += 1
        prev = current

    print("Thanks for playing!")
    print(f"Sequence length: {count}")


if __name__ == "__main__":
    main()
```
