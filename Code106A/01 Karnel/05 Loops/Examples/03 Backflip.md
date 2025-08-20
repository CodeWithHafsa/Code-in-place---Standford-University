## Question # 03 - Backflip
Get Karel to do a cool backflip by turning left 4 times.

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

from karel.stanfordkarel import *

def main():
    """
    Makes Karel do a sick backflip!!
    """
    pass # Delete this line and write your code here! :)


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

## Answer
```python
from karel.stanfordkarel import *

def main():
    """ Makes Karel do a sick backflip!! """
    # Since we are turning a known number of times, we can use a for-loop to repeat turn_left()
    for i in range(4):
        turn_left()


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```

### Output
![alt text](Images/image03.png)