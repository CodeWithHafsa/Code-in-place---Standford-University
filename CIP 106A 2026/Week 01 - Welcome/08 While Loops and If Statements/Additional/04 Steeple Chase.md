## Example - Steeple Chase

The program that Mehran works through in assignment 2. 

This program allows Karel to run a "Steeple Chase" (like a hurdles race, but with arbitrarily large hurdles) where: 

* Karel starts at position (1, 1), facing East (aka right). 
* The steeple chase is guaranteed to be 9 columns long. 
* There can be arbitrarily many hurdles that can be of arbitrary size, located between any two corners in the world. 
* Karel should "jump" each hurdle one at a time. For example, if you were to execute the SteepleChase program, you would see something like the following before-and-after diagram

![alt text](image.png)

## Answer

```python
"""
File: SteepleChaseKarel.py
--------------------------
Karel runs a steeple chase that is 9 avenues long.
Hurdles are of arbitrary height and placement.
"""

"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!

Note: The starter code for this example is the solution.
"""

from karel.stanfordkarel import *


def main():
    """
    To run a race that is 9 avenues long, we need to move
    forward or jump hurdles 8 times. Let's use a for-loop for this!
    """
    for i in range(8):
        if front_is_clear():  # If there is no hurdle to jump, move
            move()
        else:  # If there is a hurdle (the front is blocked)
            jump_hurdle()


def jump_hurdle():
    """
    Pre-condition:  Facing East at bottom of hurdle
    Post-condition: Facing East at bottom in next avenue after hurdle
    """
    ascend_hurdle()
    move()
    descend_hurdle()


def ascend_hurdle():
    """
    Pre-condition:  Facing East at bottom of hurdle
    Post-condition: Facing East immediately above hurdle
    """
    turn_left()  # Face North
    
    # While there is a wall on the Eastern side of Karel, move up a row
    while right_is_blocked():
        move()
        
    turn_right()  # Face East


def descend_hurdle():
    """
    Pre-condition:  Facing East above and immediately after hurdle
    Post-condition: Facing East at bottom of hurdle
    """
    turn_right()  # Face South
    move_to_wall()  # Move to row 1
    turn_left()  # Face East


def move_to_wall():
    """
    Pre-condition:  None
    Post-condition: Facing first wall in whichever direction
                    Karel was facing previously
    """
    while front_is_clear():
        move()


def turn_right():
    """
    Pre-condition:  None
    Post-condition: Karel is facing to the right of whichever
                    direction Karel was facing previously
    """
    for i in range(3):
        turn_left()


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```