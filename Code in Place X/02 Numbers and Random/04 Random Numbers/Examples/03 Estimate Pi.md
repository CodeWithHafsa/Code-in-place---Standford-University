## Estimate Pi

Estimate π using random numbers. Pick NUM_POINTS random points (x, y), each coordinate between 0 and RADIUS, and count how many land inside the quarter circle of radius RADIUS. A point is inside when x² + y² ≤ RADIUS².

The fraction of points inside gets close to π / 4, so print 4 × inside / NUM_POINTS as your estimate.

```python
"""
File: estimatepi.py
-------------------
Estimate pi by "throwing" random points at a square and counting
how many land inside the quarter circle. The fraction inside
gets close to pi / 4, so 4 times that fraction estimates pi. Check out
the optional video which walks through solving this! 

Don't worry if this math looks too complicated! You do 
not need to know it for CIPX. This is just a fun, optional,
example for anyone curious :) and hopefully it shows the power 
of what you can do with the skills you already have! 
"""

from random import randint

RADIUS = 10000
NUM_POINTS = 100000

def main():
    inside = 0
    points = 0

    while points < NUM_POINTS:
        x = randint(0, RADIUS)
        y = randint(0, RADIUS)
        if is_in_circle(x, y):
            inside = inside + 1
        points = points + 1

    print(4 * inside / NUM_POINTS)


def is_in_circle(x, y):
    return x * x + y * y <= RADIUS * RADIUS

if __name__ == "__main__":
    main()
```

