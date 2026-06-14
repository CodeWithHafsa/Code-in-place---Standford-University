## Example 05 -Greetings

We've written a helper function for you called `greet(name)` which takes as input a string `name` and prints a greeting. Write some code in `main()` to get the user's name and then greet them, being sure to **call the** `greet(name)` **helper function**.

Here's a sample run of the program (user input in **bold italics**):

>> What's your name? **Karel** \
Greetings Karel!

---

```python
"""
This is a worked example. This code is starter code; you should edit and run it to 
solve the problem. You can click the blue show solution button on the left to see 
the answer if you get too stuck or want to check your work!
"""

def main():
	pass # delete this and write your code here!

# There is no need to edit code beyond this point

def greet(name):
	return "Greetings " + name + "!"
	
	
if __name__ == '__main__':
    main()
```

## Answer

```python
def main():
    name = input("What's your name? ")
    print(greet(name))

# There is no need to edit code beyond this point

def greet(name):
    return "Greetings " + name + "!"
	
if __name__ == '__main__':
    main()
```