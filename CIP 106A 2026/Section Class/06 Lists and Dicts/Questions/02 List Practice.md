## Assignment

## Problem #2: List Practice
Now practice writing code with lists! Implement the functionality described in the comments

#### Given Code

```python
def main():
    # Create a list called `fruit_list` that contains the following fruits: 
    # 'apple', 'banana', 'orange', 'grape', 'pineapple'.
    
    
    # Print the length of the list.

    
    # Add 'mango' at the end of the list. 


    # Print the updated list.
    
if __name__ == "__main__":
    main()
```

## Answer

```python
def main():
    #   Create a list called `fruit_list` that contains the following fruits: 
    # 'apple', 'banana', 'orange', 'grape', 'pineapple'.
    fruit_list = ['apple', 'banana', 'orange', 'grape', 'pineapple']

    # Print the length of the list
    print(len(fruit_list))

    # Add 'mango' at the end of the list
    fruit_list.append('mango')

    # Print the updated list
    print(fruit_list)

if __name__ == "__main__":
    main()
```

## Key

### List Practice Solution

```python
def main():
    # Create a list called `fruit_list` that contains the following fruits: 'apple', 'banana', 'orange', 'grape', 'pineapple'.
    fruit_lst = ['apple', 'banana', 'orange', 'grape', 'pineapple']
    
    # Print the length of the list.
    lst_length = len(fruit_lst)
    print(lst_length)

    # Add 'mango' at the end of the list. 
    fruit_lst.append('mango')

    # Print the updated list.
    print(fruit_lst)

if __name__ == '__main__':
    main()
```