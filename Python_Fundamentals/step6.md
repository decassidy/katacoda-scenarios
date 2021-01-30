
![Python Logo](./assets/python-logo.png)

___

Of course, we can use Python for more complicated tasks than adding two and two together. For instance, we can write an initial sub-sequence of the Fibonacci series as follows:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> # Fibonacci series:
... # the sum of two elements defines the next
... a, b = 0, 1
>>> while a < 10:
...     print(a)
...     a, b = b, a+b
...
0
1
1
2
3
5
8</code></pre>

Start a python interactive session: `python3.8`{{execute}}

Execute the following steps:

1. Copy the follow comment line in the interactive python terminal: `# Fibonacci series:`{{copy}} and press <kbd>Enter</kbd>
<br/><br/>
2. Copy the following comment line: `# the sum of two elements defines the next`{{copy}} and press <kbd>Enter</kbd>
<br/><br/>
3. Copy the following variables: `a, b = 0, 1`{{copy}} and press <kbd>Enter</kbd>
<br/><br/>
4. Copy the following line: `while a < 10:`{{copy}} and press <kbd>Enter</kbd>
<br/><br/>
5. Tap the <kbd>Space</kbd> bar 4 times and copy the follwing line: `print(a)`{{copy}} and press <kbd>Enter</kbd>
<br/><br/>
6. Tap the <kbd>Space</kbd> bar 4 times and copy the following line: `a, b = b, a+b`{{copy}} and press <kbd>Enter</kbd> 2 times to execute the loop.

This example introduces several new features.

* The first line contains a multiple assignment: the variables `a` and `b` simultaneously get the new values 0 and 1. On the last line this is used again, demonstrating that the expressions on the right-hand side are all evaluated first before any of the assignments take place. The right-hand side expressions are evaluated from the left to the right.<br/>

* The [while](https://docs.python.org/3.8/reference/compound_stmts.html#while) loop executes as long as the condition (here: `a < 10`) remains true. In Python, like in C, any non-zero integer value is true; zero is false. The condition may also be a string or list value, in fact any sequence; anything with a non-zero length is true, empty sequences are false. The test used in the example is a simple comparison. The standard comparison operators are written the same as in C: `<` (less than), `>` (greater than), `==` (equal to), `<=` (less than or equal to), `>=` (greater than or equal to) and `!=` (not equal to).<br/>

* The body of the loop is indented: indentation is Python’s way of grouping statements. At the interactive prompt, you have to type a tab or space(s) for each indented line. In practice you will prepare more complicated input for Python with a text editor; all decent text editors have an auto-indent facility. When a compound statement is entered interactively, it must be followed by a blank line to indicate completion (since the parser cannot guess when you have typed the last line). Note that each line within a basic block must be indented by the same amount.<br/>

* The [print()](https://docs.python.org/3.8/library/functions.html#print) function writes the value of the argument(s) it is given. It differs from just writing the expression you want to write (as we did earlier in the calculator examples) in the way it handles multiple arguments, floating point quantities, and strings. Strings are printed without quotes, and a space is inserted between items, so you can format things nicely, like this:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> i = 256*256
>>> print('The value of i is', i)
The value of i is 65536</code></pre>

The keyword argument end can be used to avoid the newline after the output, or end the output with a different string:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> a, b = 0, 1
>>> while a < 1000:
...     print(a, end=',')
...     a, b = b, a+b
...
0,1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,</code></pre>

![CassidyMedia Logo](./assets/wallpaper_without_slogan2.png)

Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)