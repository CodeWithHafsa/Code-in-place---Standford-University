## Assignment
(Suggested 7 mins)

Print out each of the numbers 1 through 100 and whether that number is even or odd.

100 is specified using a constant `MAX_NUMBER`.

Here is what the output looks like when MAX_NUMBER = 100

```
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
10 is even
11 is odd
12 is even
13 is odd
14 is even
15 is odd
16 is even
17 is odd
18 is even
19 is odd
20 is even
21 is odd
22 is even
23 is odd
24 is even
25 is odd
26 is even
27 is odd
28 is even
29 is odd
30 is even
31 is odd
32 is even
33 is odd
34 is even
35 is odd
36 is even
37 is odd
38 is even
39 is odd
40 is even
41 is odd
42 is even
43 is odd
44 is even
45 is odd
46 is even
47 is odd
48 is even
49 is odd
50 is even
51 is odd
52 is even
53 is odd
54 is even
55 is odd
56 is even
57 is odd
58 is even
59 is odd
60 is even
61 is odd
62 is even
63 is odd
64 is even
65 is odd
66 is even
67 is odd
68 is even
69 is odd
70 is even
71 is odd
72 is even
73 is odd
74 is even
75 is odd
76 is even
77 is odd
78 is even
79 is odd
80 is even
81 is odd
82 is even
83 is odd
84 is even
85 is odd
86 is even
87 is odd
88 is even
89 is odd
90 is even
91 is odd
92 is even
93 is odd
94 is even
95 is odd
96 is even
97 is odd
98 is even
99 is odd
100 is even
```

## Concepts

One important thing to know is how to use the "index" variable in a for loop. This problem was designed to test that idea. 

To review how to use the index in a for loop, check out the for loop lesson.

Computing if a number is even or odd is covered in the python control flow lesson.

### Given

```python
# print numbers from 1 up until MAX_NUMBER, inclusive
MAX_NUMBER = 100

def main():
    pass
    # TODO: your code here

if __name__ == "__main__":
    main()
```

## Answer

```python
# print numbers from 1 up until MAX_NUMBER, inclusive
MAX_NUMBER = 100

def main():
    for i in range(1, MAX_NUMBER + 1):
        if i % 2 == 0:
            print(f"{i} is even")
        else:
            print(f"{i} is odd")

if __name__ == "__main__":
    main()
```


## Key Answer

```python
# print numbers from 1 up until MAX_NUMBER, inclusive
MAX_NUMBER = 100

def main():
    for number in range(1, MAX_NUMBER + 1):
        if number % 2 == 0:
            print(f"{number} is even")
        else:
            print(f"{number} is odd")

if __name__ == "__main__":
    main()
```