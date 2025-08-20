# Basic Arithmetic

## What is an Algorithm?
An algorithm is a step-by-step procedure or set of rules to solve a specific problem or perform a computation.

## Common Basic Algorithms
## Linear Search
Find if an element exists in a list by checking elements one by one.

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

print(linear_search([3, 5, 7, 9], 7))  # Output: 2
```

## Binary Search (on sorted arrays)
Efficiently find an element by repeatedly dividing the search interval in half.

```python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1

print(binary_search([1, 3, 5, 7, 9], 5))  # Output: 2
```

## Bubble Sort
Sorts a list by repeatedly swapping adjacent elements if they are in the wrong order.

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]

arr = [64, 34, 25, 12, 22]
bubble_sort(arr)
print(arr)  # Output: [12, 22, 25, 34, 64]
```

## Factorial (Recursion)

Calculates the factorial of a number 𝑛 (i.e, 𝑛!=𝑛×(𝑛−1)×...×1n!=n×(n−1)×...×1).

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n-1)

print(factorial(5))  # Output: 120
```