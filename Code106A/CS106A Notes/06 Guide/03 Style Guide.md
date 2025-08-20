# Style Guide
## Introduction to Programming Style in Python
*Created by Juliette Woodrow*

As you start to write your first programs, it’s important to understand the concept of programming style and why it is essential in the development process. In this handout, we will discuss the importance of good programming style and provide guidelines to help you write clean and maintainable code.

## Why is Programming Style Important?
Good programming style is essential for several reasons:

1. It makes your code easier to read and understand.
2. It helps you and others identify and fix bugs more quickly.
3. It enables better collaboration with other programmers.
4. It leads to more maintainable and reusable code.

“Readability” is the key factor to consider when it comes to programming style. Code readability is crucial for understanding, maintaining, and collaborating on a coding project. Writing readable code makes it easier for you and others to identify and fix bugs, build upon existing code, and work together on projects. In this handout we will discuss many strategies for writing code that is easy to read and understand.

Now, let’s dive into some specific programming style guidelines for Python:

## Descriptive Variable and Function Names
Choosing descriptive variable and function names is an essential aspect of writing clean and maintainable code. Meaningful names make it easier for you and others to understand the purpose of each component in your code, reducing the need for extensive comments and making your code more self-explanatory. In Python, we follow the snake_case naming convention for variables and functions. Here are some guidelines to help you choose the right names:

### 1. Descriptive names: 
Select clear and descriptive names for your variables and functions. This makes it easier for you and others to quickly grasp the functionality of your program.

*Example: Functions for a robot navigating a maze*

```python
# Good
def move_to_wall():
    …..

# Bad
def robot_moving():
    …..
```

A robot could move in a lot of ways, so we need to be more specific and descriptive when choosing the name of the function so that it is easier to understand exactly what the function does.

### 2. Snake case: 
In Python, use snake_case for variable and function names. This means using lowercase letters and separating words with underscores. This naming convention is easy to read and is the standard practice in Python.

*Example:*

```python
# Good
def calculate_total_price(price, tax_rate):
    total_price = price * (1 + tax_rate)
    return total_price

# Bad
def CalculateTotalPrice(p, tr):
    x = p * (1 + tr)
    return x
```

In the second example, it is harder to understand what the function does. Though the person writing the function likely knows that p means price and tr means tax rate, these names are not clear to other people reading the code (and the author if they look back at this code later). Though the function name is clear, it is not written in snake case. In python programs, it is standard to use snake case for all function names.

### 3. Avoid Python Keywords as Names
In addition to picking descriptive names, there are certain python keywords that we do not want to use when naming our own variables and functions as that can be confusing. Python keywords that should not be used as function or variable names: `False, True, None, and, as, assert, async, await, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield.`

By following these guidelines and using descriptive variable and function names written in snake_case, you can greatly improve the readability and maintainability of your Python code.

## Using Whitespace to Improve Code Readability
Whitespace helps visually separate different sections of your code and makes it easier to understand the structure and flow of your program. To effectively use whitespace for better code readability, follow these guidelines:

1. Use consistent indentation to show the hierarchy of your code blocks, typically 4 spaces per indentation level in Python. Luckily, a tab is typically 4 spaces. So you can just hit the tab button instead of typing out 4 spaces each time.
2. Separate function definitions with two blank lines to clearly distinguish between them.
3. Add a single blank line between logical sections within a function to group related lines of code together.
4. Surround operators with spaces to make expressions easier to read. Instead of `x=3+4` you should write `x = 3 + 4`. 

By following these whitespace guidelines, you can make your code more visually appealing and easier to navigate. This may seem time consuming, but it will save you lots of time in your editing and debugging process.

## Comments
Comments help you and others understand the purpose and functionality of your code, making it easier to debug, maintain, and collaborate on projects. However, it’s also essential to strike the right balance between commenting and not over-commenting. There are two standard types of comments in python. In-line comments are comments that start with a # and go only to the end of the line. Docstring comments are comments inside a set of three triple quotes and can be more than one line. We discuss below when to use each type of comment. Here are some guidelines for using comments effectively in your code:

### 1. Comment for each function: 
Write a short comment for each function in your program to explain its purpose and how it works. This helps others quickly understand the function’s role and functionality within the code. Comments should go below the def and before the code body to make it clear which function this comment belongs to. It is standard in python for comments at the top of each function to be inside of a doc string as shown below.

Example:

```python
def calculate_area(radius):
    """Calculate the area of a circle given its radius."""
    area = 3.14 * radius ** 2
    return area
```

### 2. Comment at the top of each file: 
Include a comment at the beginning of each file in your program, describing its overall purpose and any important information about its contents. This helps provide context for the code in the file and makes it easier for others to understand how it fits into the larger project. It is standard in Python to place file header comments inside a doc string

Example:

```python
"""
Filename: geometry.py
Author: Juliette
Description: This module contains functions for calculating the area, perimeter, and volume of various geometric shapes.
"""
…
your_code_here
…
```

### 3. Inline comments for complex code: 
Use inline comments to provide explanations for any code that might be difficult to understand or requires additional clarification. Avoid writing comments for straightforward code, as this can clutter your code and make it harder to read.

Example:

```python
# Good
def calculate_discount(price, discount_rate):
    if discount_rate <= 0.1:
        discount = price * discount_rate
    elif discount_rate <= 0.2:
        # Apply an additional 2% discount for rates between 10% and 20%
        discount = price * (discount_rate + 0.02)  
    else:
        discount = price * 0.25  # Maximum discount of 25%

    return discount

# Some redundant / unnecessary comments
def calculate_discount(price, discount_rate):
    if discount_rate <= 0.1:  # Check if discount rate is less than or equal to 10%
        discount = price * discount_rate  # Calculate discount
    elif discount_rate <= 0.2:  # Check if discount rate is less than or equal to 20%
        discount = price * (discount_rate + 0.02)  # Calculate discount with additional 2%
    else:  # Discount rate is greater than 20%
        discount = price * 0.25  # Calculate discount with maximum 25% rate

    return discount
```

In the “Good” example, the in-line comments are used to provide clear explanations for any non-obvious or potentially confusing parts of the code, such as the additional 2% discount applied for rates between 10% and 20%, and the maximum discount of 25%.

In the “redundant / unnecessary comments” example, the in-line comments are overly wordy and explain parts of the code that are already clear enough. This may distract the reader and make the code harder to understand.

## Decomposition
Decomposition is the process of breaking down a complex problem into smaller, more manageable parts. In programming, this often means dividing your code into smaller, reusable functions. This helps make your code easier to understand, debug, and maintain. Let’s discuss some guidelines to follow when decomposing your code:

### 1. Do one thing: 
Each function should have a single responsibility, meaning it should only do one conceptual thing, like building a hospital, not building a hospital and then moving to the next hospital. This makes your code easier to reuse and modify in the future. It will also make the debugging process easier because you will be able to narrow the issue down to a single function.

### 2. Know what it does by looking at its name: 
Choose function names that clearly describe their purpose, so you can understand what they do just by looking at their names. This improves code readability and reduces the need for extensive comments.

### 3. Less than 10 lines, 3 levels of indentation: 
Keep your functions short (preferably less than 10 lines) and limit the levels of indentation to 3 or fewer. Note that 10 lines / 3 levels of indentation is not a strict rule. Rather these are guidelines to keep in mind as you are starting out in your programming journey. This helps keep your code readable and maintainable, as it’s easier to understand the logic and flow of shorter functions.

### 4. Reusable and easy to modify: 
Write code that is easy to reuse and modify by using functions. This allows you to save time and effort when making changes or building upon your existing codebase.

## Constants and Magic Numbers
In programming, it’s important to understand the concept of constants and magic numbers, as well as how to use them properly. This section will explain what constants and magic numbers are and provide guidelines for using them effectively in your code.

## Constants
Constants are values that do not change during the execution of a program. They are used to give meaningful names to certain values, making the code easier to understand. In Python, constants are typically defined in upper snake case, which uses uppercase letters with words separated by underscores.

Example:

```python
PI = 3.14159
GRAVITY = 9.81
MAX_CONNECTIONS = 100
```

By using constants, you can easily update the value in one place if it needs to change, without having to search for and modify multiple occurrences of the same value throughout your code.

## Magic Numbers
Magic numbers are hardcoded values that appear directly in your code without any explanation of their meaning or purpose. These values can make your code difficult to understand and maintain, as it’s not clear where they come from or why they are being used.

Example:
```python
# Good
PI = 3.14159
area = PI * radius ** 2

# Bad
area = 3.14159 * radius ** 2
```

To avoid magic numbers in your code, replace magic numbers with named constants, as shown in the example above.

## Parameters
Parameters are pieces of information that functions need to use when we call them. You can think of them as inputs to the function. By using parameters, functions can work with different inputs without changing the code inside the function. This makes the function more adaptable and easy to use in various situations. Parameters help functions focus on the information they receive as input and not depend on information from other parts of the program. Using parameters is another example of good programming style.


Let’s consider an example where we want to create a function that adds two numbers together. First, let’s look at a version without using parameters:

```python
# Without parameters
def add_numbers():
    a = 5
    b = 3
    result = a + b
    print(result)

add_numbers()  # Prints out: 8

# If we want to add different numbers, we need to change the values of 'a' and 'b' inside the function
def add_numbers():
    a = 7
    b = 4
    result = a + b
    print(result)

add_numbers()  # Prints out: 11
```

In the above example, we have to change the values of a and b inside the function every time we want to add different numbers. Now, let’s rewrite the function using parameters:

```python
# With parameters
def add_numbers(a, b):
    result = a + b
    print(result)

add_numbers(5, 3)  # Prints out: 8
add_numbers(7, 4)  # Prints out: 11
```

By using parameters, we can now call the add_numbers function with different inputs without changing the code inside the function. This makes the function more flexible and reusable, allowing us to easily add different pairs of numbers without modifying the function itself.

### Advantages of using parameters:

### 1. Modularity: 
Functions with parameters work independently and can be used in different parts of your program or even in other projects without any problems.
### 2. Ease of maintenance: 
When you need to change a function’s behavior, you’ll only have to change the code inside the function. This won’t affect the rest of your program.
### 3. Simpler testing: 
It’s easier to test functions that use parameters because you can provide different inputs to check how the function behaves in various scenarios without changing the function itself.

## Conclusion
Remember that your code is not only meant for computers to execute but also for humans to read and understand. By consistently practicing good programming style, you will develop strong coding habits that will benefit you and your collaborators in the long run, making you a more effective and efficient programmer.