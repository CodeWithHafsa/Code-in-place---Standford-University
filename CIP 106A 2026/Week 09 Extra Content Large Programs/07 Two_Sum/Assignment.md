## Assignment

## Prompt
In the problem TwoSum, you are tasked with writing a program that checks whether a list of integers can add up to a target value. For example, if you are given a list [1, 2, 3, 4] and a target value of 6, your TwoSum program should return true since 2 and 4 add up to 6.

```python
two_sum([2, 7, 11, 15], 9)     # returns True (2 + 7 = 9)
two_sum([1, 2, 3, 4], 8)       # returns False (no such pair)
two_sum([5, 5], 10)            # returns True (5 + 5 = 10)
two_sum([4], 8)                # returns False (need at least 2 numbers)
```

Write a function called `two_sum` that takes two parameters:

* `nums:` a list of integers
* `target:` an integer target sum

```
True 
False 
True 
False
```

The function should return True if **any two distinct elements** in the list sum to the target value. Otherwise, return False.

---

```python
def main():
    """
    Calls two_sum_finder on a few sample inputs.
    You can add more test cases here to check your work!
    """
    print(two_sum([2, 7, 11, 15], 9))     # Expected: True
    print(two_sum([1, 2, 3, 4], 8))       # Expected: False
    print(two_sum([5, 5], 10))            # Expected: True
    print(two_sum([4], 8))                # Expected: False

def two_sum(nums, target):
    """
    Returns True if any two distinct elements in the list `nums`
    add up to the value `target`. Otherwise, returns False.

    Examples:
    two_sum([2, 7, 11, 15], 9) -> True
    two_sum([1, 2, 3, 4], 8) -> False
    """
    # TODO: implement this function
    return False

if __name__ == '__main__':
    main()
```

## Answer

```python
def main():
    print(two_sum([2, 7, 11, 15], 9))     # True
    print(two_sum([1, 2, 3, 4], 8))       # False
    print(two_sum([5, 5], 10))            # True
    print(two_sum([4], 8))                # False


def two_sum(nums, target):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return True
    return False


if __name__ == '__main__':
    main()
```