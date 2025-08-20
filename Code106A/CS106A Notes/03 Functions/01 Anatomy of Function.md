# Anatomy of Function
A function, in a programming context, typically consists of a name, parameters (inputs), a function body containing the logic, and an optional return value. Functions are defined to perform specific tasks and can be reused with different inputs to produce outputs. 

## Components of a Function:
**Name:** A descriptive identifier for the function, usually in snake_case (e.g., calculate_average).
**Parameters:** These are inputs to the function, allowing it to work with varying data.
**Function Body:** The block of code where the function's logic is executed.
**Return Value (Optional):** A value that the function sends back to the caller after completing its task. 


## Example (Python):
```python
def calculate_average(a, b):  # Parameters: a and b
    sum = a + b          # Function body: calculates the sum
    return sum / 2       # Returns the average
```

## Key Concepts:
### Function Definition:
This is where you define the function, specifying its name, parameters, and logic.

### Function Call:
When you use the function name followed by parentheses and arguments (if any), you're calling or invoking the function.

### Activation Record:
During a function call, a memory block (activation record) is allocated to store parameters, local variables, and return information.

### Return:
The return statement sends a value back to the caller, and when reached, the function's execution is complete. 