## Assignment

## Mars Weight
A few years ago, NASA made history with the first controlled flight on another planet. Its latest Mars Rover, Perseverance, has onboard a 50cm high helicopter called Ingenuity. Ingenuity made its third flight, during which it flew faster and further than it had on any of its test flights on Earth. Interestingly, Ingenuity uses Python  for some of its flight modeling software!

![alt text](/image.png)

When programming Ingenuity, one of the things that NASA engineers need to account for is the fact that due to the weaker gravity on Mars, an Earthling's weight on Mars is 37.8% of their weight on Earth. Write a Python program that prompts an Earthling to enter their weight on Earth and prints their calculated weight on Mars. The output should be rounded to two decimal places when necessary. Python has a round function which can help you with this. You pass in the value to be rounded and the number of decimal places to use.

### Sample Run

```
$ python marsweight.py
Enter a weight on Earth: 120
The equivalent weight on Mars: 45.36
```


```python
"""
Prompts the user for a weight on Earth
and prints the equivalent weight on Mars.
"""

def main():
    # Fill this function out!
    pass

if __name__ == "__main__":
    main()
```


## Answer

```python
# Mars gravity is about 37.8% of Earth's gravity
MARS_GRAVITY_PERCENT = 0.378

def main():
    # 1. Get input from the user
    earth_weight_str = input("Enter a weight on Earth: ")
    
    # 2. Convert the input string to a float (decimal number)
    earth_weight = float(earth_weight_str)
    
    # 3. Calculate the weight on Mars
    mars_weight = earth_weight * MARS_GRAVITY_PERCENT
    
    # 4. Print the result (rounded to 2 decimal places if needed)
    print("The equivalent weight on Mars: " + str(round(mars_weight, 2)))

if __name__ == '__main__':
    main()
```

## Key

```python
"""
Prompts the user for a weight on Earth
and prints the equivalent weight on Mars.
"""

# We use constants!
MARS_MULTIPLE = 0.378

def main():
    earth_weight_str = input('Enter a weight on Earth: ')

    # Get the numeric value since input() returns a value in string form
    earth_weight = float(earth_weight_str)

    # Having a variable for each piece of information is a good habit
    mars_weight = earth_weight * MARS_MULTIPLE
    rounded_mars_weight = round(mars_weight, 2)


    # Note the string concatenation!
    print(f'The equivalent weight on Mars: {rounded_mars_weight}')

if __name__ == '__main__':
    main()
```

#### Some Key Points
* input -> to enter something
* output -> to print somegthing from console
* Formatting two types: Concate and f-string formatting
* Variable - a box to hold information 
* Data types - any type like integar, string that hold memory
* Types: Integar, Float, String, Bool (there size in bytes)
* Constant - value never changes and remain same throughout
* Typecasting/Typeconvesrion - changing from one data type to another
