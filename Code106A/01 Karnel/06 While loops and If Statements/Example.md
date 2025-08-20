## Example # 01:
This is a worked example. It shows a simple while loop that makes Karel move to the end of the wall, no matter how long the world is!

```python
"""
This is a worked example. It shows a simple while loop 
that makes Karel move to the end of the wall, no matter
how long the world is!
"""

from karel.stanfordkarel import *

def main():
    while front_is_clear():
        move()

# There is no need to edit code beyond this point
if __name__ == '__main__':
    main()
```

## Example # 02:
This is a worked example. It shows an example of Karel using a while loop to place a row of beepers.

```python
"""
This is a worked example. It shows an example of Karel
using a while loop to place a row of beepers
"""

from karel.stanfordkarel import *

def main():
    while front_is_clear():
        put_beeper()
        move()
    # needed because of the fence-post bug
    put_beeper()


# There is no need to edit code beyond this point
if __name__ == '__main__':
    main()
```

## Example # 03
This is a worked example. Karel will "invert" each beeper in the first row. To invert a beeper: if there was a beeper pick it up. Otherwise, put one down.

```python
"""
This is a worked example. Karel will "invert" each beeper 
in the first row. To invert a beeper: if there was a beeper
pick it up. Otherwise, put one down.
"""

from karel.stanfordkarel import *

def main():
    # invert beeper on each corner in the row
    while front_is_clear():
        invert_beeper()
        move()
    # fence-post bug correction
    invert_beeper()

def invert_beeper():
    """ flips whether or not there is a beeper """
    if beepers_present():
        pick_beeper()
    else:
        put_beeper()


# There is no need to edit code beyond this point
if __name__ == '__main__':
    main()
```