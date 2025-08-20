## Exploring Colors
You may have noticed that when we make graphical objects, we can add color to them by adding an optional color argument when we make a shape. For example, the below code would make a red circle.

```
canvas.create_oval(x1, y1, x2, y2, color="red")
```

However, we can technically represent lots more colors with much more nuance than "red", "brown", or any other string. This can be done via hex codes. The idea behind hex codes is that we specify exactly how much red, green, and blue we want to see on the screen. We format hex codes as a string in the form of "#RRGGBB". Each color component is individual from one another and are written in base-16. For example, red is equivalent to the hex code "#FF0000". This means that the below code would also make a red circle, just like the code above!

```
canvas.create_oval(x1, y1, x2, y2, color="#FF0000")
```

For this problem, we have provided three circles: one is red, one is blue, and one is white (making it hidden since the background is white). Modify the code to change the white circle's color to instead be purple so we can see it!

You can go online to find lots of different hex codes for all sorts of colors for later projects! :)

*(Hint: Purple is the color we get when we mix/add red and blue together. What do we think the hex code would look like with that information?)*

### Given Code
```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

from graphics import Canvas
    
CANVAS_WIDTH = 400
CANVAS_HEIGHT = 400

def main():
    canvas = Canvas(CANVAS_WIDTH, CANVAS_HEIGHT)
    
    # TODO: Replace the "#FFFFFF" color parameter to make a purple circle!
    canvas.create_oval(CANVAS_WIDTH/2 - 75, 225, CANVAS_WIDTH/2 + 75, 375, color="#FFFFFF")
    
    # There is no need to edit code beyond this point
    
    # Draw a red circle
    canvas.create_oval(25, 25, 175, 175, color="#990000")
    
    # Draw a plus sign
    canvas.create_line(190, 100, 210, 100)
    canvas.create_line(200, 90, 200, 110)
    
    # Draw a blue circle
    canvas.create_oval(CANVAS_WIDTH/2 + 25, 25, CANVAS_WIDTH/2 + 175, 175, color="#000099")
    
    # Draw an arrow
    canvas.create_line(200, 170, 200, 210)
    canvas.create_line(200, 210, 190, 190)
    canvas.create_line(200, 210, 210, 190)
    

if __name__ == '__main__':
    main()
```

## Answer
```python
from graphics import Canvas
    
CANVAS_WIDTH = 400
CANVAS_HEIGHT = 400

def main():
    canvas = Canvas(CANVAS_WIDTH, CANVAS_HEIGHT)

    # Notice how we just added the "#990000" and "#000099" hex codes together to make "#990099"?
    # This is because we are literally adding the amounts of red and blue we want to make purple!
    canvas.create_oval(CANVAS_WIDTH/2 - 75, 225, CANVAS_WIDTH/2 + 75, 375, color="#990099")
    
    # There is no need to edit code beyond this point

    # Draw a red circle
    canvas.create_oval(25, 25, 175, 175, color="#990000")
    
    # Draw a plus sign
    canvas.create_line(190, 100, 210, 100)
    canvas.create_line(200, 90, 200, 110)
    
    # Draw a blue circle
    canvas.create_oval(CANVAS_WIDTH/2 + 25, 25, CANVAS_WIDTH/2 + 175, 175, color="#000099")
    
    # Draw an arrow
    canvas.create_line(200, 170, 200, 210)
    canvas.create_line(200, 210, 190, 190)
    canvas.create_line(200, 210, 210, 190)
    

if __name__ == '__main__':
    main()
```