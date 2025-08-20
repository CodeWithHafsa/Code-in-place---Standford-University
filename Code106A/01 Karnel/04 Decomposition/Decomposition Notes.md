## Chapter 4: Decomposition
The process of breaking a program down into smaller pieces is called **decomposition**, and the component parts of a large problem are called **subproblems**.

As an example, the problem of filling the hole in the roadway can be decomposed into the following subproblems:

* Move up to the hole
* Fill the hole by dropping a beeper into it
* Move on to the next corner

The main function would look like this:

```python
def main():
move()
fill_pothole()
move()
```

The correspondence with the outline is immediately clear, and everything would be great if only you could get Karel to understand what you mean by **fill_pothole()**. 

Given the power to define functions, implementing fill_pothole() is extremely simple. All you have to do is define a fill_pothole() function whose body consists of the commands you have already written to do the job, like this:

```python
def fill_pothole():
turn_right()
move()
put_beeper()
turn_around()
move()
turn_right()
```

## Example

```python
from karel.stanfordkarel import *
def main():
   move()
   fill_pothole()
   move()

# Fills the pothole beneath Karel's current position by 
# placing a beeper on that corner. For this function to work 
# correctly, Karel must be facing east immediately above the 
# pothole. When execution is complete, Karel will have 
# returned to the same square and will again be facing east.
def fill_pothole():
   turn_right()
   move()
   put_beeper()
   turn_around()
   move()
   turn_right()

# Turns Karel 90 degrees to the right. 
def turn_right():
   turn_left()
   turn_left()
   turn_left()

# Turns Karel around 180 degrees. 
def turn_around():
   turn_left()
   turn_left()
```