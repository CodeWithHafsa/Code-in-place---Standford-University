## Weighted Coin

Write a program which will flip a weighted coin.

Coin flips are usually fair, but they can be cheated. A weighted coin is a coin where the probability of heads isn't 50%. Your code should use the random module to "flip" a coin where the probability of heads is 70% and print the outcome (heads or tails).


```python
"""
File: weightedcoin.py
----------------------
Write a program which will flip a weighted coin.

This is a worked example. This code is starter code; you should edit and run it to solve the problem. You can click the blue show solution button on the left to see the answer if you get too stuck or want to check your work!

Note: The starter code for this example is the solution.
"""

from random import randint

def main():
    # randint(1, 10) gives each integer from 1 through 10 an equal chance.
    # Seven of those ten outcomes represent heads, so heads has probability 70%.
    flip = randint(1, 10)
    if flip <= 7:
        print("Heads!")
    else:
        print("Tails!")


# There is no need to edit code beyond this point

if __name__ == '__main__':
    main()
```