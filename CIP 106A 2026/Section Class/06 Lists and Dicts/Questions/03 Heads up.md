## Assignment

## Problem #3: Heads Up
Our next goal is to learn how to read data from files. Loading data from a file can be useful for many final projects. Write a program that runs a console version of the phone game Heads Up!

#### How the game is played remotely:
When it is your turn, close your eyes. \
A word will be displayed in the HeadsUp program. \
The rest of the section will try and describe it without saying the word. \
You have to guess the word as quickly as possible.

#### Milestones
Milestone #1: Read the provided function that loads all of the words from the file cswords.txt into a list. \
Milestone #2: Then, show a randomly chosen word from the list \
Milestone #3: Repeat: wait for the user to hit enter, then show another word.

---

#### Given Code

```python
import random

# Name of the file to read in!
FILE_NAME = 'cswords.txt'

def get_words_from_file():
    """
    This function has been implemented for you. It opens a file, 
    and stores all of the lines into a list of strings. 
    It returns a list of all lines in the file. 
    """
    lines = []
    with open(FILE_NAME) as f:
        for line in f:
            # removes whitespace characters (\n) from the start and end of the line
            line = line.strip() 
            # if the line was only whitespace characters, skip it 
            if line != "":
                lines.append(line)
                
    return lines


def main():
    # your code here :) 
    

if __name__ == '__main__':
    main()
```

## Answer

```python
import random

# Name of the file to read in!
FILE_NAME = 'cswords.txt'

def get_words_from_file():
    """
    This function has been implemented for you. It opens a file, 
    and stores all of the lines into a list of strings. 
    It returns a list of all lines in the file. 
    """
    f = open(FILE_NAME)

    lines = []

    for line in f:
        # removes whitespace characters (\n) from the start and end of the line
        line = line.strip()

        # if the line was only whitespace characters, skip it
        if line != "":
            lines.append(line)

    return lines

def play_game(words):
    while True:
        # choose a random word
        random_word = random.choice(words)

        # show the word
        print(random_word)

        # wait for user to press Enter
        input()

def main():
    words = get_words_from_file()
    play_game(words)

if __name__ == '__main__':
    main()
```

## Key

### Heads Up Solution

```python
import random

# Name of the file to read in!
FILE_NAME = 'cswords.txt'

def get_words_from_file():
    """
    This function has been implemented for you. It opens a file, 
    and stores all of the lines into a list of strings. 
    It returns a list of all lines in the file. 
    """
    f = open(FILE_NAME)
    lines = []
    for line in f:
        # removes whitespace characters (\n) from the start and end of the line
        line = line.strip() 
        # if the line was only whitespace characters, skip it 
        if line != "":
            lines.append(line)
    return lines

def play_game(words):
    while True:
        random_word = random.choice(words)
        input(random_word)

def main():
    words = get_words_from_file()
    play_game(words)

if __name__ == '__main__':
    main()
```