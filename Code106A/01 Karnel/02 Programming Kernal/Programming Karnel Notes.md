# Chapter 2: Programming Karel

The simplest style of Karel program uses text to specify a sequence of built-in commands that should be executed when the program is run. Consider the simple Karel program below. The text on the left is the program. The state of Karel's world is shown on the right:

```python
# comment
# File: FirstKarel.py
# -----------------------------
# The FirstKarel program defines a "main" 
# function with three commands. These commands cause  
# Karel to move forward one block, pick up a beeper
# and then move ahead to the next corner.
from karel.stanfordkarel import *

# function definition
def main():
   move()  #body of the function definition
   pick_beeper()
   move()
   turn_left()
   move()
   turn_left()
   turn_left()
   turn_left()
   move()
   move()
   put_beeper()
   move()
```

**Output:**\
![alt text](Images/image03.png)

# Example Code

```python
# This tells python who Karel is!
from karel.stanfordkarel import *

# this program executes in a special function called main
def main():
    move()
    pick_beeper()
    move()
    turn_left()
    move()
    turn_right()
    move()
    put_beeper()
    move()

# the definition of turn_right
def turn_right():
    turn_left()
    turn_left()
    turn_left()

# This is "boilerplate" code which launches your code
# when you hit the run button
if __name__ == '__main__':
    main()
```