## Assignment
Write a Fill in the Blank program (similar to the one in the Print Input Lesson). Your program should request three strings from the user:

1. a color
2. an adjective
3. a goal you would like to achieve 

The story should then fill in the template:\
At dawn the sky turned [color], and the air felt\
[adjective]. I decided today I will finally [goal].

---
Here is an example run of the program:
```
A color: blue   
An adjective: smelly  
A goal you would like to achieve: eat fewer bugs  
At dawn the sky turned blue, and the air felt smelly. I decided today I will finally eat fewer bugs.
```

Here is another example run of the program:
```
A color: pink    
An adjective: friendly   
A goal you would like to achieve: learn to code   
At dawn the sky turned pink, and the air felt friendly. I decided today I will finally learn to code.
```

Note that the autograder is really particular about formatting. Your input prompts must be exactly:
```python 
"A color: "
"An adjective: "
"A goal you would like to achieve: "
```

---
### Given Code
```python
"""
Example of a Fill in the Blank program, like the one from the lesson.
The user will enter three words (a color, an adjective and a goal).
We will then turn them into a one sentence story.
"""

def main():
    color = input("A color: ")

if __name__ == "__main__":
    main()
```

## Answer
```python
def main():
    color = input("A color:")
    adjective = input("An adjective:")
    goal = input("A goal you would like to achieve: ")

    print("At dawn the sky turned " + color + ", and the air felt " + adjective + ". I decided today I will finally " + goal + ".")

if __name__ == "__main__":
    main()
```