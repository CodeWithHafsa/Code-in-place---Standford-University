# For-each Loops
## Quest
For-loops are a great tool for repeating some code multiple times. When it comes to containers, it is often that we want to write code that repeats for *each item* in the container. Python gives us a simple way to do that!

## For-Each Loops
If you have a container like a list or a dictionary (which we will learn about next), we use a **for-each loop** to repeat once for every item in the container. Here's how that looks in Python:
```python
for element in container:
    # Each time we loop, element becomes the next item in the list
```

## Iterating over Lists
For-each loops work differently on different containers. The only container we have looked at so far is lists, so we'll focus on them for now. \
With lists, the iterator element loops over all the values in the list. You can change the name of `element` to be whatever you like, just as long as the name hasn't been used yet:

```python
colors = ["Red", "Yellow", "Blue"]

# Instead of printing the whole list, we print each individual element
for color in colors:
    print(color)
```
=> Run >_Show

In general, you only use regular for loops on a list when you need to know the index of the items in the loop.

## Fun Fact
We just finished telling you about the difference between a regular for loop with this notation, for i in range(...), and a for-each loop. Fun fact, a regular for loop is technically also a for-each loop because range returns a sequence of numbers to be iterated over.