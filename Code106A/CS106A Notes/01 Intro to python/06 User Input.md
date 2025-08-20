# User Input
## Quest
Wow! You have mastered the world of variables and basic arithmetic in Python! You can now store information in variables and do operations with those variables if they represent numbers. This is great for when you have data that you want the program to remember, but what if you want to store input from the user? 

The syntax of the `input` function is written below: 
```python
answer = input('message/prompt to the user')
```

The message inside the parentheses will be outputted to the console just like the inside of a print statement. Then the console will wait for the user to respond and hit enter. Whatever the user responds with will be stored in the variable answer. 

Here’s another example of what this might look like running in the console: 

```python
def main():
    print('hello there')
    user_status = input('how are you? ')
    print('you said: ' + user_status)

if __name__ == "__main__":
    main()
```
=> Run >_Show

*Note: running this in the reader should create an input text box, but the prompt may not be there. Just type in your response and hit enter to see the result.* 

An important thing to note is that the value stored from a call to input will always be a string type. If you wish to get an int or float value, you have to use the built-in type conversion functions that we talked about in the `arithmetic section`:

```python
def main():
    x = input('enter a value:')
    print(x)
    print(float(x) / 2)

if __name__ == "__main__":
    main()
```
=> Run >_Show

*Note: running this in the reader should create an input text box, but the prompt may not be there. Just type in a numerical value and hit `enter` to see the result.* 

A question that you might be having is what happens if the user doesn’t input anything? If the user just hits enter, then the value stored in the variable will just be nothing.  

```python
def main():
	x = input('enter a value: ')
	print(x)

if __name__ == "__main__":
	main()
```
=> Run >_Show

*Note: running this in the reader should create an input text box, but the prompt may not be there. Just hit enter to see what happens when the user doesn't input anything.*

As you can see, the result is just a blank screen instead of an error. 