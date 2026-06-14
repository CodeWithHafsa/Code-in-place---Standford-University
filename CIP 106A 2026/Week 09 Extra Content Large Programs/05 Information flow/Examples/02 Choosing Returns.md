## Example 02 - Choosing Returns

There are times where we want to return different things from a function based on some condition. To practice this idea, imagine that we want to check if someone is an adult. We might check their age and return different things depending on how old they are!

We've provided you with the `ADULT_AGE` variable which has the `age` a person is legally classified as an adult (in the United States). Fill out the `is_adult(age)` function, which returns `True` if the function takes an age that is greater than or equal to `ADULT_AGE`. If the function takes an age less than `ADULT_AGE`, return `False` instead.

Here are two sample runs of the program, one for each return option (user input in bold italics):

(Entered age is an adult age)

>> How old is this person?: **35** \
True

(Entered age is not an adult age)

>> How old is this person?: **7** \
False

---

```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

ADULT_AGE = 18 # U.S. adult age 

def is_adult(age):
    # TODO: Delete the line below and write your code here
    pass
    
########## No need to edit code beyond this point :) ##########

def main():
    age = int(input("How old is this person?: "))
    print(is_adult(age))
    

if __name__ == "__main__":
    main()
```

## Answer

```python
ADULT_AGE = 18 # U.S. age 

def is_adult(age):
    if age >= ADULT_AGE:
        return True
    
    return False
    
########## No need to edit code beyond this point :) ##########

def main():
    age = int(input("How old is this person?: "))
    print(is_adult(age))
    

if __name__ == "__main__":
    main()
```

### Output

```
% python main.py
How old is this person?: 35
True
```