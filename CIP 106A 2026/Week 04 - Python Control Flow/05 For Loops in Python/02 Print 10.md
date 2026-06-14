## Example 02 - Print 10 
Write a program that prints the first 10 numbers in order. Use a for loop.

```
1
2
3
4
5
6
7
8
9
10
```


---
```python
def main():
    print("Your code here")

if __name__ == '__main__':
    main()
```

## Answer

```python
def main():
    for i in range(10):
        next_value = i + 1
        print(next_value)

if __name__ == '__main__':
    main()
```