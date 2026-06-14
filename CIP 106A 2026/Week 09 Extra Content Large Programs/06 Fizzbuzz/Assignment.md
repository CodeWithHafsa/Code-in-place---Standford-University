## Assignment
In the game Fizz Buzz, players take turns counting up from one. If a player’s turn lands on a number that’s divisible by 3, she should say “Fizz” instead of the number, and if it lands on a number that’s divisible by 5, she should say “Buzz” instead of the number. If the number is both a multiple of 3 and of 5, she should say "Fizzbuzz" instead of the number. A spectator sport, it is not. 

What it is, however, is an interesting problem in control flow and parameter usage. Write a function called fizzbuzz which accepts as a parameter an integer called n. The function should return what a player should say if it is the number n on their turn. 

Here are a few examples: 

```python
fizzbuzz(8) # returns 8 
fizzbuzz(10) # returns "Buzz" 
fizzbuzz(3) # returns "Fizz"
```

Next, complete your program by writing a main function that plays Fizz Buzz up to 17. Here's a sample run of the program: 

```
1 
2 
Fizz 
4 
Buzz 
Fizz 
7 
8 
Fizz 
Buzz 
11 
Fizz 
13 
14 
Fizzbuzz 
16 
17 
```

Recall that in order to check if a number is divisible by a value, you can use the remainder operator %. Want to check if some number n is divisible by 5? When you divide n by 5 the remainder should equal 0:  

```python
# checks if n is divisible by 5 
is_divisible = n % 5 == 0
```

---

```python
MAX_VALUE = 17

def main():
    # modify this starter code to call fizzbuzz
    # on every number from 1 to MAX_VALUE
    to_say = fizzbuzz(1)
    print(to_say)

def fizzbuzz(n):
    """
    Takes in a positive integer (n) and returns
    what the player should say at that value.
    Here are a few examples:
    fizzbuzz(3) returns "Fizz"
    fizzbuzz(15) returns "Fizzbuzz"
    fizzbuzz(2) returns 2
    """
    # TODO: fill in this function
    return n

if __name__ == '__main__':
    main()
```

## Answer

```python
MAX_VALUE = 17

def main():
    for i in range(1, MAX_VALUE + 1):
        print(fizzbuzz(i))


def fizzbuzz(n):
    if n % 3 == 0 and n % 5 == 0:
        return "Fizzbuzz"
    elif n % 3 == 0:
        return "Fizz"
    elif n % 5 == 0:
        return "Buzz"
    else:
        return n


if __name__ == '__main__':
    main()
```