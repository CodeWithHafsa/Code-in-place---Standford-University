## Assignment

## Planetary Weight Calculator
Mars is not the only planet in our solar system with its own unique gravity. In fact, each planet has a different gravitational constant, which affects how much an object would weigh on that planet. Below is a list of the constants for each planet compared to Earth's gravity:

- Mercury: 37.6%
- Venus: 88.9%
- Mars: 37.8%
- Jupiter: 236.0%
- Saturn: 108.1%
- Uranus: 81.5%
- Neptune: 114.0%

Write a Python program that prompts an Earthling to enter their weight on Earth and then to enter the name of a planet in our solar system. The program should then use if statements to find the correct gravitational constant for the selected planet and calculate the person's weight on that planet. Finally, the program should print the calculated weight, rounded to 2 decimal places. 

### Sample Run

```
$ python planetaryweight.py
Enter a weight on Earth: 120
Enter a planet: Mars
The equivalent weight on Mars: 45.36
```

### Sample Run

```
$ python planetaryweight.py
Enter a weight on Earth: 150
Enter a planet: Jupiter
The equivalent weight on Jupiter: 354.0
```

---

```python
"""
Prompts the user for a weight on Earth
and a planet (in separate inputs). Then 
prints the equivalent weight on that planet.

Note that the user should type in a planet with 
the first letter as uppercase, and you do not need
to handle the case where a user types in something 
other than one of the planets (that is not Earth). 
"""

def main():
    # Fill this function out!
    pass

if __name__ == "__main__":
    main()
```


## Answer

```python
"""
Prompts the user for a weight on Earth
and a planet (in separate inputs). Then 
prints the equivalent weight on that planet.

Note that the user should type in a planet with 
the first letter as uppercase, and you do not need
to handle the case where a user types in something 
other than one of the planets (that is not Earth). 
"""

# Conversion of constants
Mercury_Gravity= 0.376
Venus_Gravity = 0.889
Mars_Gravity = 0.378
Jupiter_Gravity = 0.236
Saturn_Gravity = 0.1081
Uranus_Gravity = 0.815
Neptune_Gravity = 1.140

def main():
    # Prompt for the user for weight on Earth
    earth_weight = float(input("Enter a weight on Earth: "))

    # Prompt for the user for planet name 
    planet = input("Enter a planet: ").strip().capitalize()

    if planet == "Mercury":
        gravity_constant = Mercury_Gravity
    
    elif planet == "Venus":
        gravity_constant = Venus_Gravity

    elif planet == "Mars":
        gravity_constant = Mars_Gravity
    
    elif planet == "Jupiter":
        gravity_constant = Jupiter_Gravity

    elif planet == "Saturn":
        gravity_constant = Saturn_Gravity
    
    elif planet == "Uranus":
        gravity_constant = Uranus_Gravity

    else planet == "Neptune":
        gravity_constant = Neptune_Gravity

    #  Calulcate and print the results
    calculated_weight = round(earth_weight * constants, 2)
    print(f" The equivalent weight on {planet}:  {calculated_weight}")

if __name__ == "__main__":
    main()
```

## Key

```python
"""
Prompts the user for a weight on Earth
and a planet (in separate inputs). Then 
prints the equivalent weight on that planet.

Note that the user should type in a planet with 
the first letter as uppercase, and you do not need
to handle the case where a user types in something 
other than one of the planets (that is not Earth). 
"""

MERCURY_GRAVITY = 0.376
VENUS_GRAVITY = 0.889
MARS_GRAVITY = 0.378
JUPITER_GRAVITY = 2.36
SATURN_GRAVITY = 1.081
URANUS_GRAVITY = 0.815
NEPTUNE_GRAVITY = 1.14
EARTH_GRAVITY = 1.0

def main():
    # Prompt the user for their weight on Earth
    earth_weight = float(input("Enter a weight on Earth: "))

    # Prompt the user for the name of a planet
    planet = input("Enter a planet: ")

    # Determine the gravitational constant for the selected planet
    if planet == "Mercury":
        gravity_constant = MERCURY_GRAVITY
    elif planet == "Venus":
        gravity_constant = VENUS_GRAVITY
    elif planet == "Mars":
        gravity_constant = MARS_GRAVITY
    elif planet == "Jupiter":
        gravity_constant = JUPITER_GRAVITY
    elif planet == "Saturn":
        gravity_constant = SATURN_GRAVITY
    elif planet == "Uranus":
        gravity_constant = URANUS_GRAVITY
    else:
        # can assume user types in one of these planets, so this can be an else instead of elif
        gravity_constant = NEPTUNE_GRAVITY

    # Calculate the equivalent weight on the selected planet
    planetary_weight = earth_weight * gravity_constant
    rounded_planetary_weight = round(planetary_weight, 2)

    # Print the result
    print(f"The equivalent weight on {planet}: {rounded_planetary_weight}")

if __name__ == "__main__":
    main()
```
