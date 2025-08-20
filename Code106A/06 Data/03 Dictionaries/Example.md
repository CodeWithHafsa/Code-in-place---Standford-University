## Example
#### Choose your own adventure
Select actions to complete the program. Follow the instructions provided in the blue box.

```python
"""
Write a program that can get the value associated
with the key "Kenya"
"""

def main():
    my_dict = {
        "Kenya":"Nairobi", 
        "Malaysia":"Kuala Lumpur",
        "Spain":"Madrid"
    }
    value = my_dict['Kenya']
    print(value)

if __name__ == '__main__':
    main()
```