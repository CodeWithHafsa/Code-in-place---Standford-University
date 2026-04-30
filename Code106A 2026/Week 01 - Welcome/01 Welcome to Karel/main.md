## Readings
**Chapter 1: Introducing Karel the Robot**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter1.html

**Chapter 2: Programming Karel**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter2.html

**Chapter 3: Defining New Functions**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter3.html

**Chapter 4: Decomposition**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter4.html

**Chapter 5: For Loops**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter5.html

**Chapter 6: While Loops**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter6.html

**Chapter 7: If Statements**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter7.html

**Chapter 8: Stepwise Refinement**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter8.html

**Chapter 9: Extra Karel Features**
https://compedu.stanford.edu/karel-reader/docs/python/en/chapter9.html

**Chapter 10: Reference**
https://compedu.stanford.edu/karel-reader/docs/python/en/reference.html

**Code**
https://compedu.stanford.edu/karel-reader/docs/python/en/ide.html


## Document:
A cheat-sheet with the structure of the Karel programming language. See the Karel Reader for more details:

### Base Karel commands
```python
move()
turn_left()
put_beeper()
pick_beeper()
```

### Karel program structures

This is the structure of a Karel program

```python
from karel.stanfordkarel import *

# Comments can be included in any part
# of a program. They start with a #
# and include the rest of the line.
# the computer will ignore them, but they
# are very helpful for human readers!

def main():
    # code to execute

# declarations of other functions

# necessary boilerplate to start execution
if __name__ == '__main__':
    main()
```

```python
# example program to move, put_beeper, move
def main():
    move()
    put_beeper()
    move()

# necessary boilerplate to start execution
if __name__ == '__main__':
    main()
```

### Function Declaration:

```python
def name():
    # body of the function.
```

```python
# example: turn_right
def turn_right():
    turn_left()
    turn_left()
    turn_left()
```


### Conditions:

```python
if condition:
    # code run if condition passes
```

```python
if condition:
    # code block for "yes"
else:
    #code block for "no"
```

```python
# example: a safe move
if front_is_clear():
    move()
```


### For Loop:

```python
for i in range(count):
    # code to repeat
```

```python
# example: place 100 beepers
for i in range(100):
    put_beeper()
```


### While Loop:

```python
while condition:
    # code to repeat
```

```python
# example: move karel to the next wall
while front_is_clear():
    move()
```


### Names of the conditions

```python
# karel conditions
front_is_clear()
beepers_present()
beepers_in_bag()
left_is_clear()
right_is_clear()
facing_north()
facing_south()
facing_east()
facing_west()
```

```python
# opposites
front_is_blocked()
no_beepers_present()
no_beepers_in_bag()
left_is_blocked()
right_is_blocked()
not_facing_north()
not_facing_south()
not_facing_east()
not_facing_west()
```


### Additional commands:

For advanced Karel programs you can use these three secret commands

```python
random(p)
paint_corner(color)  # use "transparent" to remove colors
corner_color_is(color)
```


Here is a simple program that shows each of the advanced commands

```python
def main():
    # this will pass 80% of the time
    if random(0.8):
        # create a blue square
        paint_corner("blue")
    # checks if the current square is blue
    if corner_color_is("blue"):
        move()
```