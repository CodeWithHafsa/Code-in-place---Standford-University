## Assignment
Assignment
Write a program that has a user play a memory game using lists. 
This Python programming assignment will guide you through the exciting process of creating your own memory game, a classic and engaging exercise that tests your ability to remember and match pairs of items. In this game the cards will be represented as numbers in a list and their location will be indices of the list. By completing this project, you will practice critical list concepts. Not only will this enhance your problem-solving skills, but you will also have a lot of fun as you watch the game come to life and challenge yourself or your friends to find all the pairs.

![alt text](image.png)

Here is a demo of a fully implemented solution: [Memory List Game Demo](https://codeinplace.stanford.edu/public/share/bJVFHPEFfntixP3swoLg)

### Milestone #1: Create the truth list.
Use a for loop to create a list that has the values  0  through  N_PAIRS - 1  twice. So for example if  NUM_PAIRS = 3 as in the example, your list should have this value:
```
[0, 0, 1, 1, 2, 2]
```

### Milestone #2: Shuffle the list. 
The python random library has a special function called shuffle which will randomly order the values in a list. Call that function on your list and then print out the result. Print out the list to make sure it looks shuffled! Assuming that your list from the previous milestone was named truth
```
random.shuffle(truth)
print(truth)
```

### Milestone #3: Create a displayed list
In this program you will need to keep track of a separate list, which is the one to display to the user. We use the '*' symbol to denote that a value is hidden to the user (otherwise we display the value). Initially displayed should be a list of '*' values which is the same length as truth. If  NUM_PAIRS = 3:

```
['*', '*', '*', '*', '*', '*']
```

### Milestone #4: Get a valid index from the user
Write logic to get a valid index from the user. A valid index must be greater than or equal to 0, it must be less than or equal to the index of the last element in the list. It also must be one where the value of the displayed list at that index must be '*' (otherwise it is an index which has already been guessed). If the user does not enter a valid index, ask them to give you a new index. We recommend that you define a new function `get_valid_index` which takes in the displayed list and returns the valid index the user entered.

### Milestone #5: Check correct.
Get two valid inputs from the user and check if there is a match. If there is a match, you should reveal those values in the displayed list. Otherwise, if the values don't match, you should tell the user the values, but do not update the displayed list. Of course, you should first make sure the user didn't enter the same index twice. Here are a few examples. Imagine the current value of displayed and truth lists are as follows:

```
[2, 1, 1, 2, 0, 0] # truth_list
['*', '*', '*', '*', 0, 0] # displayed_lis
```

Here is an example turn where the user does not get a match (user input is in blue):
```
['*', '*', '*', '*', 0, 0]
Enter an index: 0
Enter an index: 1
Value at index 0 is 2
Value at index 1 is 1
No match. Try again. Press Enter to continue... 
```

Here is an example turn where the user does get a match (user input is in blue):
```
['*', '*', '*', '*', 0, 0]
Enter an index: 0
Enter an index: 3
Match!
```

Since the user got a match the display list will be updated to [2, '*', '*', 2, 0, 0]

### Milestone #6: Play multiple turns.

The user should play until all the pairs have been correctly located. Between turns make sure to call `clear_terminal`. At the end of the game, tell the user that they have won by printing something like`'Congratulations! You won!'`

### Given Code
```python
import random

NUM_PAIRS = 3

def main():
    """
    You should write your code here. Make sure to delete 
    the 'pass' line before starting to write your own code.
    """
    pass

def clear_terminal():
    for i in range(20):
      print('\n')

if __name__ == '__main__':
    main()
```

## Answer
```python
import random

NUM_PAIRS = 3

def main():
    # Milestone 1: Create the truth list
    truth_list = []
    for i in range(NUM_PAIRS):
        truth_list.append(i)
        truth_list.append(i)

    # Milestone 2: Shuffle the list
    random.shuffle(truth_list)
    # Uncomment the next line for debugging
    # print("Shuffled truth list:", truth_list)

    # Milestone 3: Create a displayed list with '*'
    displayed_list = ['*'] * len(truth_list)

    # Milestone 6: Game loop
    while '*' in displayed_list:
        clear_terminal()
        print(displayed_list)
        
        index1 = get_valid_index(displayed_list, "Enter the first index: ")
        index2 = get_valid_index(displayed_list, "Enter the second index: ", disallowed=[index1])

        val1 = truth_list[index1]
        val2 = truth_list[index2]

        print(f"Value at index {index1} is {val1}")
        print(f"Value at index {index2} is {val2}")

        if val1 == val2:
            print("Match!")
            displayed_list[index1] = val1
            displayed_list[index2] = val2
        else:
            print("No match. Try again.")
            input("Press Enter to continue...")

    clear_terminal()
    print(displayed_list)
    print("🎉 Congratulations! You won!")

def get_valid_index(displayed_list, prompt, disallowed=[]):
    while True:
        try:
            index = int(input(prompt))
            if index < 0 or index >= len(displayed_list):
                print(f"Index must be between 0 and {len(displayed_list) - 1}.")
            elif displayed_list[index] != '*':
                print("That index is already revealed. Choose another.")
            elif index in disallowed:
                print("You already chose that index. Choose a different one.")
            else:
                return index
        except ValueError:
            print("Please enter a valid number.")

def clear_terminal():
    for _ in range(20):
        print('\n')

if __name__ == '__main__':
    main()
```