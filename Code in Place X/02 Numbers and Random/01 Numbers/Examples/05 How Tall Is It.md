## How Tall Is It?

Ask the AI how tall a landmark is, then work out how many of you it would take to reach the top.

Your program should:
1. Ask the user to name a landmark, and to give their own height in meters.
2. Ask call_gpt how tall that landmark is, in meters.
3. Turn the AI’s answer into a number, divide the landmark’s height by the user’s, and print the result rounded to two decimal places.

Here is example output from running this program:

```
Name a landmark: Eiffel Tower
How tall are you in meters? 1.7
The Eiffel Tower is 330.0 meters tall.
That is about 194.12 of you stacked up!
```

Here is the thing worth remembering: call_gpt hands back a **string**, exactly like input does. It does not matter that the answer looks like a number. Until you call float on it, Python will not divide with it.

That is also why the prompt ends with "Respond with a number only". If the AI replied 330 meters, float would be handed text it cannot turn into a number, and the program would stop right there.


#### Answer

```python
from ai import call_gpt

def main():
    landmark = input("Name a landmark: ")
    my_height = float(input("How tall are you in meters? "))

    # Ask for a number only, so that float() has something it can convert
    prompt = f"How tall is the {landmark} in meters? Respond with a number only, nothing else."
    height_text = call_gpt(prompt)
    height = float(height_text)

    print(f"The {landmark} is {height} meters tall.")
    print(f"That is about {round(height / my_height, 2)} of you stacked up!")

if __name__ == "__main__":
    main()
```