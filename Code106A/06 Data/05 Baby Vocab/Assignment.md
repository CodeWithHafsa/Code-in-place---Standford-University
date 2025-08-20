## Assignment
Parenthood is an exciting time with lots happening! One of the most memorable things as a parent when you have a baby is hearing them speak their first word. However, it can also be interesting to see what words your baby learns and say the most as they grow!

To explore our interest in a baby's vocabulary, write a program that loops over a list of words made by a baby, counts the appearance of each word, and then makes a histogram from counts. For the histogram formatting, have the words appear vertically and the bars appear horizontally. For the bars, represent each appearance of a word with a singular 'x'. See below for an example. We've already loaded the list of words from a file for you in the starter code. Check it out if you'd like. :)

Histograms can be thought of as a chart that looks like a bunch of connected bars. Each bar represents different groups or ranges of numbers. The height of each bar shows how many things (like data points or occurrences) fall into that group. In this case, each bar will belong to a word the baby said and how tall the bar is depends on how many times the baby said that specific word.

When you're done, your output should look similar to this:

```
mom   : xxxxxxxxxxxxxxxxxxxxxxx
dad   : xxxxxxxxxxxxxxxx
juice : xxxxxxx
apple : xxx
hi    : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
bye   : xxxxxxxxxxxxxxxxx
no    : xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

In the above example, the word "mom" would have been said 23 times, "dad" would have been said 16 times, and so on.

### Given Code
```python
def main():
    words = load_words_from_file("words.txt")
    # TODO: your code here :)

def print_histogram_bar(word, count):
    """
    Prints one bar in the histogram.
    
    Uses formatted strings to do so. The 
        {word : <8}
    adds white space after a string to make
    the string take up 8 total characters of space.
    This makes all of our words on the left of the 
    histogram line up nicely. On the other end,
        {'x' * count}
    takes the 'x' string and duplicates it by 'count'
    number of times. So 'x' * 5 would be 'xxxxx'.
    
    Calling print_histogram_bar("mom", 7) would print:
        mom     : xxxxxxx
    """
    print(f"{word : <8}: {'x' * count}")

def load_words_from_file(filepath):
    """
    Loads words from a file into a list and returns it.
    We assume the file to have one word per line.
    Returns a list of strings. You should not modify this
    function.
    """
    words = []
    with open(filepath, 'r') as file_reader:
        for line in file_reader.readlines():
            cleaned_line = line.strip()
            if cleaned_line != '':
                words.append(cleaned_line)
    
    return words


if __name__ == '__main__':
    main()
```

## Answer

```python
from collections import Counter

def main():
    words = load_words_from_file("words.txt")
    
    # Count the frequency of each word using Counter
    word_counts = Counter(words)
    
    # Print the histogram bars for each word
    for word, count in word_counts.items():
        print_histogram_bar(word, count)

def print_histogram_bar(word, count):
    """
    Prints one bar in the histogram.
    
    Uses formatted strings to do so. The 
        {word : <8}
    adds white space after a string to make
    the string take up 8 total characters of space.
    This makes all of our words on the left of the 
    histogram line up nicely. On the other end,
        {'x' * count}
    takes the 'x' string and duplicates it by 'count'
    number of times. So 'x' * 5 would be 'xxxxx'.
    
    Calling print_histogram_bar("mom", 7) would print:
        mom     : xxxxxxx
    """
    print(f"{word : <8}: {'x' * count}")

def load_words_from_file(filepath):
    """
    Loads words from a file into a list and returns it.
    We assume the file to have one word per line.
    Returns a list of strings. You should not modify this
    function.
    """
    words = []
    with open(filepath, 'r') as file_reader:
        for line in file_reader.readlines():
            cleaned_line = line.strip()
            if cleaned_line != '':
                words.append(cleaned_line)
    
    return words

if __name__ == '__main__':
    main()
```