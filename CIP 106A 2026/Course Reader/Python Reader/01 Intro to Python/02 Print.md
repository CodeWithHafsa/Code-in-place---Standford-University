# <center> Print </center>

## Quest

Get ready... because you are about to experience a rite of passage for all new programmers: writing your first <span style="color: #bd66a3">Hello World </span> program! To do this, we will learn about the <span style="color: #191970">**print** </span>  function, the first of many new tools. Let’s see how it works!

## Printing to the Console

The <span style="color: #191970">**print** </span> function simply writes text to the console. When reading a **print statement**, the computer takes whatever you put between the parentheses of the function, such as a word, number, or sentence, and displays it directly in the console. We will use this function often in our programs whenever we want the computer to communicate something to the user. Below is our <span style="color: #bd66a3">Hello World </span> program, which prints <span style="color: #22C55E"> "Hello, world!"  </span> when executed. Run the program to see <span style="color: #191970">**print** </span> in action!

```python
def main():
    print("Hello, world!")

if __name__ == '__main__':
    main()
```

#### Output
```
Hello, world!
```

## Basics of Function Anatomy

As we mentioned before, it is what's inside the parentheses in a print statement that tells the computer what to print. Many times, a function will need a bit of extra information before it can do its job. <span style="color: #191970">**print** </span>, 

for example, doesn’t know what you want it to write unless you tell it! The text you give <span style="color: #191970">**print** </span> is called an argument, and we put the **arguments** of a function inside those parentheses at the end. In the code below, functions like <span style="color: #7777a8">main( ) </span>  don’t have any arguments. They can do their job without any extra info from the programmer, so we just leave the parentheses empty.

## Printing on a new line

After printing something to the console, Python moves down to the next line so that any additional text is separated from what you just printed. We see this come up when using multiple <span style="color: #191970">**print** </span> statements in the same sentence:

```python
def main():
    print("hello, world!")
    print("hello, trees!")
    print("hello, animals!")

if __name__ == '__main__':
    main()
```

#### Output
```
hello, world!
hello, trees!
hello, animals!
```

## What can you print? 

<span style="color: #191970">**print** </span>  works for many different types of text, including words, numbers, and symbols. If you want to print a number, just put the number in as an argument. If you want to put a word or a sentence, you need to surround it with quotation marks to tell the computer that it is looking at written words instead of Python code. 

<span style="color: #191970">**print** </span>  doesn’t write out the quotation marks, but you have to include them so that Python understands what you mean.

```python
def main():
    # Output: 2
    print(2)

    # Output: 3.14
    print(3.14)
	
    # Output: Hello
    print("Hello")

    # Output: Python is cool!
    print("Python is cool!")

    # Output: I luv 2 code!
    print("I luv 2 code!")

    # Notice that even though 2 is a number, it still 
    # goes inside the quotation marks! print understands numbers
    # AND sentences that contain numbers


if __name__ == '__main__':
    main()
```

#### Output
```
2
3.14
Hello
Python is cool!
I luv 2 code!
```

## <span style="color: #22C55E"> "" </span> vs <span style="color: #22C55E"> '' </span> 

In other programming languages, there is a difference between single and double quotation marks. 

However, in Python, they are mostly equivalent. You can enclose words and sentences with either single or double quotes, but not both! 

```python
def main():
    print("Hello, world!") # Perfect
    print('Hello, world!') # Yep!
    print("Hello, world!') # Very Bad!!!


if __name__ == '__main__':
    main()
```

#### Output
```
SyntaxError: unterminated string literal (detected at line 4)
```

We can be strategic about which set of quotes we want to use. 

If your text contains single quotes, you should use double quotes:

```python
 print("no, you didn't") # ->  no, you didn't 
```

If your text contains double quotes, you should use single quotes:

```python
 print('"Good morning!" said the cat') # ->  "Good morning!" said the cat  
```

## Printing Variables with f-strings

Often, we want to print a sentence that includes the value of a variable. One common way to do this in Python is with an **f-string**. 

An f-string is a string with the letter f before the quotation marks. Inside the string, you can put variables inside curly braces {
}.

```python
def main():
    name = "Karel"

    # Output: Hello, Karel!
    print(f"Hello, {name}!")


if __name__ == '__main__':
    main()
```

#### Output
```
Hello, Karel!
```

---
The <span style="color: #22C55E"> f </span>  before the string tells Python to fill in the value of anything inside curly braces. Here is another example:

```python
def main():
    name = "Karel"
    age = 5

    # Output: Karel is 5 years old.
    print(f"{name} is {age} years old.")


if __name__ == '__main__':
    main()
```

#### Output
```
Karel is 5 years old.
```

---
You can think of an f-string as a sentence with blanks that Python fills in using the values of your variables. For example:

```python
def main():
    num_apples = 3
    num_bananas = 4

    # Output: I have 3 apples and 4 bananas.
    print(f"I have {num_apples} apples and {num_bananas} bananas.")


if __name__ == '__main__':
    main()
```

#### Output
```
I have 3 apples and 4 bananas.
```

f-strings are especially useful when you want your printed output to look like a natural sentence!

## Advanced (Optional) Reading

There is a third type of quotation mark, and you’ve already seen it before! Remember block comments? Well, more generally, a block comment is just a sentence or paragraph that fits on multiple lines. We use triple quotation marks for these multi-line paragraphs, and we could tell the computer to print one out:


```python
def main():
    """
    You probably won't need to use triple quotation marks
    very often, but it is an extra tool you have available
    to you if you need it. 

    Now, we're going to print this
    whole paragraph to the console!
    """
    print("""
    You probably won't need to use triple quotation marks
    very often, but it is an extra tool you have available
    to you if you need it. 

    Now, we're going to print this
    whole paragraph to the console!
    """)

if __name__ == '__main__':
    main()
```

#### Output
```
You probably won't need to use triple quotation marks
very often, but it is an extra tool you have available
to you if you need it.

Now, we're going to print this
whole paragraph to the console!
```

## Separating Multiple Arguments

<span style="color: #191970">**print** </span> can take in more than one value and print all of them together on a single line. We separate each value with a comma, and Python handles all the spacing for us. Multiple values do not have to be of the same type, and you can mix and match however you like:

```python
def main():
    # Output: My name is Kylen!
    print("My name is", "Kylen!")

    # Output: "My name is Claire and I have 15 friends."
    print("My name is", "Claire", "and I have", 15, "friends.")


if __name__ == '__main__':
    main()
```

#### Output

```
My name is Kylen! 
My name is Claire and I have 15 friends.
```

## Escape Characters

When you press the return key to move to a new line, do you know how your computer keeps track of where the new line should begin? 

**Escape characters** are special symbols you can add between your quotation marks to stylize the text in various ways. Each escape character starts with a backward slash <span style="color: #22C55E"> \ </span> followed by a special code. There are several escape characters you can use, but below are the most common ones:

| Code | Meaning | Example | Result |
|------|---------|---------|--------|
| \’   | Single Quote| <span style="color: #76ce85"> ‘I\’m a programmer!’ </span>  | I’m a programmer |
| \n | New Line | <span style="color: #76ce85"> “Good\nMorning” </span> | Good <br> Morning |
| \t | Tab | <span style="color: #76ce85"> “Good\tMorning”  </span> | Good &nbsp;&nbsp;&nbsp;&nbsp; Morning
| \b | Backspace | <span style="color: #76ce85"> ‘Pytho\bn’ </span>  | Pythn |

