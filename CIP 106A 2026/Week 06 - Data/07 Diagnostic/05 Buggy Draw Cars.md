## Assignment
(Suggested 12 mins)

Consider the following buggy code:

```python
from graphics import Canvas

def main():
    # draws two cars
    canvas = Canvas(400, 400)
    x = 10
    y = 10
    draw_car()

    x = 100
    y = 100
    draw_car()

def draw_car():
    # draws a car at the location x, y
    # you can assume that math offsets for the rectangles are correct
    canvas.create_rectangle(x, y, x + 50, y + 20)
    canvas.create_rectangle(x + 10, y - 10, x + 40, y + 20)

if __name__ == '__main__':
    main()
```


The programmer wants to draw two cars, one at location (10, 10) and another at location (100, 100). When they run their program they get a "NameError" and the IDE complains that inside draw_car it doesn't know what canvas, x, or y mean.

Fix this program so that the location information is correctly given to draw_car. You can make changes to both draw_car and main. Write a comments for each line you changed.

Note that you should assume that the offsets in draw_car are correct. You are not meant to be worrying about the canvas coordinates, rather the control flow of the program.

## Concepts

This problem focused on defining functions that include some inputs, known as parameters, and practicing how to use them the right way when you want to run these functions. It also touches on graphics. 
There are many methods to make this program draw two cars successfully. But, a fully correct solution should update the draw_car function according to the instructions mentioned in the comment. That requires adding parameters to the draw_car function, and then passing in canvas, x, and y when calling draw_car from the main function. 

If you found this question challenging you can check out the Information Flow and Graphics lessons. 

---

**Given Code**

```python
from graphics import Canvas

def main():
    # draws two cars
    canvas = Canvas(400, 400)
    x = 10
    y = 10
    draw_car()

    x = 100
    y = 100
    draw_car()

def draw_car():
    # draws a car at the location x, y
    # you can assume that math offsets for the rectangles are correct
    canvas.create_rectangle(x, y, x + 50, y + 20)
    canvas.create_rectangle(x + 10, y - 10, x + 40, y + 20)

if __name__ == '__main__':
    main()
```

## Answer

```python
from graphics import Canvas

def main():
    # draws two cars
    canvas = Canvas(400, 400)

    x = 10
    y = 10
    draw_car(canvas, x, y)   # CHANGED: pass canvas, x, y as arguments

    x = 100
    y = 100
    draw_car(canvas, x, y)   # CHANGED: pass canvas, x, y as arguments


def draw_car(canvas, x, y):  # CHANGED: add parameters to receive values
    # draws a car at the location x, y
    canvas.create_rectangle(x, y, x + 50, y + 20)
    canvas.create_rectangle(x + 10, y - 10, x + 40, y + 20)


if __name__ == '__main__':
    main()
```