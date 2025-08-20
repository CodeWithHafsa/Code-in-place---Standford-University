## Chapter 3: Defining New Functions
In this pattern, name represents the name you have chosen for the new function. To complete the definition, all you have to do is provide the sequence of commands in the lines after the colon, which are all indented by one tab. For example, you can define turn_right() as follows:

```python
def turn_right():
turn_left()
turn_left()
turn_left()
```

Similarly, you could define a new turn_around() function like this:

```python
def turn_around():
turn_left()
turn_left()
```

## Example
```python
# File: BeeperPickingKarel.py
# -----------------------------
# The BeeperPickingKarel program defines a "main" 
# function with three commands. These commands cause  
# Karel to move forward one block, pick up a  
# beeper and then move ahead to the next corner.
from karel.stanfordkarel import *
def main():
   move()
   pick_beeper()
   move()
   turn_left()
   move()
   turn_right()
   move()
   move()
   put_beeper()
   move()

def turn_right():
   turn_left()
   turn_left()
   turn_left()
```