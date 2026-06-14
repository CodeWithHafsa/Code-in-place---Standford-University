## Assignment
Your task: Write a program in the editor, that makes Karel pick up all the beepers on the first row of this world.

If you are feeling stuck ask a question on the public discussion forum:
https://codeinplace.stanford.edu/cip6/forum

After your program finishes, Karel's world should have no beepers, like so:

![alt text](image.png)

```python
from karel.stanfordkarel import *

# File: piles.py
# -----------------------------
# The warmup program defines a "main"
# function which should make Karel
# pick up all the beepers in the world.
def main():
    move()
    # your code here
   
   
   
# don't edit these next two lines
# they tell python to run your main function
if __name__ == '__main__':
    main()
````

## Answer
```python
from karel.stanfordkarel import *

# File: piles.py
# -----------------------------
# This program makes Karel pick up all the beepers
# on the first row of the world.

def main():
    while front_is_clear():
        pick_up_beepers()
        move()
    # Pick up any beepers at the last corner (where move isn't possible)
    pick_up_beepers()

def pick_up_beepers():
    while beepers_present():
        pick_beeper()

# don't edit these next two lines
if __name__ == '__main__':
    main()
```