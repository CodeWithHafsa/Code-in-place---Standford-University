## Assignment
Write a program that asks the user to enter the secret code to unlock a treasure chest. The secret code is **unicorn**.

If the user enters the correct secret code, print: **The treasure chest opens!**
Otherwise, print: **Access denied! The treasure stays locked.**

Here is example output from running this program:

```
Enter the secret code: dragon
Access denied! The treasure stays locked.
```

Another example output:
```
Enter the secret code: unicorn
The treasure chest opens!
```

Code

```python
def main():
    secret_code = input("Enter the secret code: ")

    if secret_code == "unicorn":
        print("The treasure chest opens!")
    else:
        print("Access denied! The treasure stays locked.")


if __name__ == "__main__":
    main()
```

