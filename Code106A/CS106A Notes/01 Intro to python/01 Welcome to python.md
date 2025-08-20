# Welcome to Python 

## Quest
Greetings, eager traveler! Your adventures in programming have led you to the foot of a tall, beautiful mountain! Today marks the beginning of your journey through Python, a journey that will inspire you and teach you so many wonderful things about computers and how they work. Python is used every day by professional programmers to build amazing new things, and you get to learn how it works! So, are you ready? Let’s look at our first Python program!

## A Blank Python Program
Before you get started writing anything, there are a few things you must add to every Python program you write. Here is a template to start writing your program:

```python
def main():
    # Your code goes here




if __name__ == '__main__':
    main()
```

Every Python program in this class must have a main function. We’ll explain what a function is soon and how to create one of your own. To start, you will define the main function with the line def main(): and your code will go “inside” the main function by indenting every line of your code once. The lines at the very bottom are required to tell the computer what it should do when you run the program. They are pointing the computer to where the first line of code is. You’ll have to memorize this template going forward, though you can always come back here later to refresh your memory.

## High-Low
This is Python code for a game called `High-Low`. The computer picks a secret number, and you try to guess it. After each guess, the computer tells you whether you are too high or too low. 

*Note: The secret number will always be a whole number, never a decimal. If you guess anything that’s not a number, like a word or a weird symbol, the program might break. If that happens, just run it again to reset everything.*

```python
import random

def main():
    # Program selects a new random number
    secret_number = random.randint(1,100)

    guess_str = input("I am thinking of a number from 1 to 100. What number am I thinking of? ")
    guess = int(guess_str)

    while guess != secret_number:
        if guess > secret_number:
            guess_str = input("Nope! That guess was too high! Try again. ")
        if guess < secret_number:
            guess_str = input("Sorry! That guess was too low! Take another guess. ")
        guess = int(guess_str)
    print("You guessed my number! Way to go!")


if __name__ == '__main__':
    main()
```
=> Run Cde  => Show


Believe it or not, by the end of this section, **you** will be able to write this program yourself. It may look like a lot right now, but we are going to go through everything used in this program step by step! Notice this program still follows our template from earlier. Even complex programs like this one still need a main function.


If you’re feeling lost right now, don’t worry. It’s ok if none of this makes any sense to you yet; we are here to learn! You got this! Continue learning below with our first lesson: commenting!


## Commenting
Can you find the line that starts with a hashtag in the High-Low program above?

```python
# Program selects a new random number
```

As you write longer and more complicated programs, it will get much harder to understand exactly what your program is doing just by looking at it. It can be helpful to leave notes for yourself or anyone else reading your code to tell the reader what the program does. Comments are a way to write bits of descriptive text in your program that Python will ignore when running it. There are two ways to add comments to your code:

### Single-Line Commenting: 
Using the `#` symbol begins a single-line comment. Anything written after the `#` on the same line will not be interpreted as code and is skipped when the program is run.



### Block Commenting: 
Sometimes you want to write longer comments which can take up multiple lines. It would be a pain to add a `#` for each line you use. Instead, we enclose the comment block with three single or double quotes `(''' or """)`, and everything between them gets "commented out" 

*Note: just make sure to be consistent with using single or double quotes.*

```python
'''
Nothing in this entire block of text will affect the program.
We can safely include as much text as we want here, even text that looks like code. If I write something like:
if condition:
    do_something()

This may look like code to you, but Python will still ignore it. Block commenting is very useful if you want to comment out a section of code without totally erasing it.
'''

if condition: # Only this text will be ignored on this line
    """
    This is another block comment, but notice how this one 
    is indented. Unlike single-line comments, block
    comments must be appropriately indented if they are 
    nested inside other code such as the "if" statement above. 
    """
    do_something()
    do_something_else()

    
do_this_one_after_the_if_finishes()

# And now the program is done
```

Without all of the comments, the only code that will affect the program's outcome looks like this:

```python
if condition:
    do_something()
    do_something_else()
do_this_one_after_the_if_finishes()
```

Comments make your programs much longer, but they are very important for helping readers know what’s going on. Always include them where it is helpful!

# Interpreted vs Compiled
You should know that Python treats single-line and block comments differently. To understand why, we first have to explain a little more about how Python works. Python is what’s known as an **interpreted language**. When you run code in an interpreted language, another program called the **interpreter** reads your code and tells the computer what to do as the program is run or during **run-time**. This is different from other languages like Java or C++, which are compiled languages. With a **compiled language**, a **compiler** translates your code into **binary**, the language your computer understands, before the program is run, during **compile-time**. The computer itself then reads that binary and runs it. 

Ok, now we can explain commenting! The distinction between single and block comments is that a single-line comment is fully ignored by the interpreter, while a block comment is valid code that has no effect on the outcome of the program. If the interpreter sees a hashtag, it thinks to itself, “Great, I can skip this part!” With block comments, however, the interpreter doesn’t ignore the comment at all; it's just that the comment doesn't require the computer to do anything. The interpreter reads it as, “Ok, there’s a comment here!” and continues on.

So, why should you care? All of this is really to say that you need to properly indent block comments that are nested inside of something (like a loop or function). If you forget, Python might warn you or your code might break. If the block comment is not nested inside of anything, you can safely leave it unindented. This idea is illustrated in the above example. Do you see why we indented one block comment but not the other?

## Console
In order to run Python programs, we use something called the **console**. The console allows you to run programs and see the result of whatever you run.

The console is where you will see error messages, prompts for user input, and output from print statements (user input and print statements will be covered in future sections). To run a program in the  console, you write your program name after the keyword python (or python3, depending on your computer):

```python
python filename.py
```


For instance, if our `High-Low` program was stored in a file called `high_low.py`, we could run it in the console like this: 

**console**

```python
$ python high_low.py
# program runs
# results are displayed here below
```

If the program you just ran raises an error, an error message appears in the console explaining what went wrong. Error messages look something like this: 

**console**

```python
$ python high_low.py
Traceback (most recent call last):
File "high_low.py", line 3
SyntaxError: invalid syntax 
```

Don’t worry about what that error message means yet. For now, we just want to be able to see how an error message would appear in the console. 

*Important Note: make sure to include the `.py` in the file name and avoid spaces when naming files. Otherwise, you might get an error that has nothing to do with your code.*

**console**

```python
$ python high_low
[Errno 2] No such file or directory
```