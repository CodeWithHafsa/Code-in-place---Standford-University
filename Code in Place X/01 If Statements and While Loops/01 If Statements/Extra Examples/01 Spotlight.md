## 01 Spotlight

Write a program that decides whether you should go or stop based on the color of a traffic light.

Start with a variable called light that stores the current color of the traffic light. If light is "green", print "Go!". Otherwise, print "Stop."

---
### Code
```python
def main():
    light = "red"

    if light == "green":
        print("Go!")
    else:
        print("Stop.")

if __name__ == "__main__":
    main()
```

Output

```
Stop.
```