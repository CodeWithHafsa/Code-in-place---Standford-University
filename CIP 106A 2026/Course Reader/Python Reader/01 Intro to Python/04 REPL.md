# <center> REPL </center>

## Quest
A few sections ago, we learned about the console, a great place to see the results of our programs and print statements. Now, we can talk about another way to evaluate lines of code called the <span style="color: #c56b9d"> **REPL** </span>.

<span style="color: #c56b9d"> **REPL** </span> stands for **Read-Eval-Print Loop**. It exists on most computer systems in the form of some sort of application that lets you execute code or commands (terminal in Mac, Windows terminal, or command shell in Windows). 

To use <span style="color: #c56b9d"> **REPL** </span> in the terminal, you can simply type **python**: 

```python
% python
>>> 
```

The triple arrow shows up to let you know that you have entered the <span style="color: #c56b9d"> **REPL** </span>. You can type any line of Python code and hit enter and then the terminal will **read** the line, **evaluate** it, and **print** the results out to the user just like we would see in the Python Console!

---
The <span style="color: #c56b9d"> **REPL** </span>. is a great way to evaluate quick lines of code or even test small bits of code before putting them into a program. 

```python
% python
>>> x = "the REPL is kind of cool"
>>> x
the REPL is kind of cool
```

---
One important thing to note: the <span style="color: #c56b9d"> **REPL** </span> evaluates Python code just like a normal interpreter. If the code contains an <span style="color: #c52a37"> error </span> the error message will show up in the REPL just like it would in the Python console. 

```python
% python
>>> x = 
File "<stdin>", line 1
    x =
       ^
SyntaxError: invalid syntax
```

---

The only case where this is not true is when the <span style="color: #c56b9d"> **REPL** </span> thinks that you simply have yet to finish a line. For example, for unclosed parentheses, sometimes the <span style="color: #c56b9d"> **REPL** </span> will simply output three dots … to show you that you have yet to finish the statement: 

```python
% python
>>> print("this line will not error"
...
...)
this line will not error 
```

Each time you press return, you will be met with … until you close the parentheses. Then, the line will execute. 

You can exit the <span style="color: #c56b9d"> **REPL** </span> by typing quit() and you should see your normal starting terminal line: 

```python
% python
>>> quit()
% 
```

So now you know how to execute Python code using two different systems, the console and the <span style="color: #c56b9d"> **REPL** </span>! The console is for longer programs and programs you want to save for later. The <span style="color: #c56b9d"> **REPL** </span> is great for quick lines of code and testing the outcome of really short programs. To see some more examples of the cool things that you can do in the <span style="color: #c56b9d"> **REPL** </span>, head to the `next section` on basic arithmetic!