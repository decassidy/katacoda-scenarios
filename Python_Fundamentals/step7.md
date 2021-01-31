
![Python Logo](./assets/python-logo.png)

___
Besides the [while](https://docs.python.org/3.8/reference/compound_stmts.html#while) statement just introduced, Python uses the usual flow control statements known from other languages, with some twists.

## `if` Statements

Perhaps the most well-known statement type is the [if](https://docs.python.org/3.8/reference/compound_stmts.html#if) statement. For example:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">In [1]: x = int(input("Please enter an integer: "))
Please enter an integer: 40

In [2]: if x < 0:
   ...:     x = 0
   ...:     print('Negative changed to zero')
   ...: elif x == 0:
   ...:     print('Zero')
   ...: elif x == 1:
   ...:     print('Single')
   ...: else:
   ...:     print('More')
   ...: 
More
</code></pre>

---

### Hands-On Exercise

1. Execute the follow code snippet into the ipython session: `x = int(input("Please enter an integer: "))`{{execute}}<br/><br/>
2. Type any integer number in the `Please enter an integer: ` input line and press <kbd>Enter</kbd>.<br/><br/>
3. Execute the following code snippet `if x < 0:`{{execute}}.<br/><br/>
4. Execute the following code snippet `x = 0`{{execute}}.<br/><br/>
5. Execute the following code snippet `print('Negative changed to zero')`{{execute}}.</kbd><br/><br/>
6. Press the <kbd>&lt;</kbd> key 4 times and execute the following code snippet `elif x == 0:`{{execute}}.<br/><br/>
7. Execute the following code snippet `print('Zero')`{{execute}}.<br/><br/>
8. Press the <kbd>&lt;</kbd> key 4 times and execute the following code snippet `elif x == 1:`{{execute}}.<br/><br/>
9. Execute the following code snippet `print('Single')`{{execute}}.<br/><br/>
10. Press the <kbd>&lt;</kbd> key 4 times and execute the following code snippet `else:`{{execute}}.<br/><br/>
11. Execute the following code snippet `print('More')`{{execute}} and press <kbd>Enter</kbd> 1 times to exit flow control statements.<br/><br/>


---

There can be zero or more [elif](https://docs.python.org/3.8/reference/compound_stmts.html#elif) parts, and the [else](https://docs.python.org/3.8/reference/compound_stmts.html#else) part is optional. The keyword ‘`elif`’ is short for ‘`else if`’, and is useful to avoid excessive indentation. An `if … elif … elif … sequence` is a substitute for the switch or case statements found in other languages.

## `for` Statements

The [for](https://docs.python.org/3.8/reference/compound_stmts.html#for) statement in Python differs a bit from what you may be used to in C or Pascal. Rather than always iterating over an arithmetic progression of numbers (like in Pascal), or giving the user the ability to define both the iteration step and halting condition (as C), Python’s for statement iterates over the items of any sequence (a list or a string), in the order that they appear in the sequence. For example:
<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: # Measure some strings:

In [2]: words = ['cat', 'window', 'defenestrate']

In [3]: for w in words:
   ...:     print(w, len(w))
   ...:
cat 3
window 6
defenestrate 12
</code></pre>

Code that modifies a collection while iterating over that same collection can be tricky to get right. Instead, it is usually more straight-forward to loop over a copy of the collection or to create a new collection:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py"># Strategy:  Iterate over a copy
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]

# Strategy:  Create a new collection
active_users = {}
for user, status in users.items():
    if status == 'active':
        active_users[user] = status	
</code></pre>

## The [range()](https://docs.python.org/3.8/library/stdtypes.html#range) Function

If you do need to iterate over a sequence of numbers, the built-in function [range()](https://docs.python.org/3.8/library/stdtypes.html#range) comes in handy. It generates arithmetic progressions:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: for i in range(5):
   ...:     print(i)
   ...:
0
1
2
3
4	
</code></pre>

The given end point is never part of the generated sequence; `range(10)` generates 10 values, the legal indices for items of a sequence of length 10. It is possible to let the range start at another number, or to specify a different increment (even negative; sometimes this is called the ‘step’):

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">range(5, 10)
   5, 6, 7, 8, 9

range(0, 10, 3)
   0, 3, 6, 9

range(-10, -100, -30)
  -10, -40, -70	
</code></pre>

To iterate over the indices of a sequence, you can combine [range()](https://docs.python.org/3.8/library/stdtypes.html#range) and [len()](https://docs.python.org/3.8/library/functions.html#len) as follows:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: a = ['Mary', 'had', 'a', 'little', 'lamb']

In [2]: for i in range(len(a)):
   ...:     print(i, a[i])
   ...:
0 Mary
1 had
2 a
3 little
4 lamb	
</code></pre>

In most such cases, however, it is convenient to use the [enumerate()](https://docs.python.org/3.8/library/functions.html#enumerate) function, see **[Looping Techniques](https://docs.python.org/3.8/tutorial/datastructures.html#tut-loopidioms)**.

A strange thing happens if you just print a range:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: print(range(10))
range(0, 10)	
</code></pre>

In many ways the object returned by [range(https://docs.python.org/3.8/library/stdtypes.html#range)]() behaves as if it is a list, but in fact it isn’t. It is an object which returns the successive items of the desired sequence when you iterate over it, but it doesn’t really make the list, thus saving space.

We say such an object is [iterable](https://docs.python.org/3.8/glossary.html#term-iterable), that is, suitable as a target for functions and constructs that expect something from which they can obtain successive items until the supply is exhausted. We have seen that the for statement is such a construct, while an example of a function that takes an iterable is [sum()](https://docs.python.org/3.8/library/functions.html#sum):

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: sum(range(4))  # 0 + 1 + 2 + 3
Out[1]: 6	
</code></pre>

Later we will see more functions that return iterables and take iterables as arguments. Lastly, maybe you are curious about how to get a list from a range. Here is the solution:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: list(range(4))
Out[1]: [0, 1, 2, 3]	
</code></pre>

In scenario **[Data Structures](https://docs.python.org/3.8/tutorial/datastructures.html#tut-structures)**, we will discuss in more detail about [list()](https://docs.python.org/3.8/library/stdtypes.html#list).

## `break` and `continue` Statements, and `else` Clauses on Loops

The [break](https://docs.python.org/3.8/reference/simple_stmts.html#break) statement, like in C, breaks out of the innermost enclosing [for](https://docs.python.org/3.8/reference/compound_stmts.html#for) or [while](https://docs.python.org/3.8/reference/compound_stmts.html#while) loop.

Loop statements may have an else clause; it is executed when the loop terminates through exhaustion of the iterable (with [for](https://docs.python.org/3.8/reference/compound_stmts.html#for)) or when the condition becomes false (with [while](https://docs.python.org/3.8/reference/compound_stmts.html#while)), but not when the loop is terminated by a [break](https://docs.python.org/3.8/reference/simple_stmts.html#break) statement. This is exemplified by the following loop, which searches for prime numbers:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: for n in range(2, 10):
   ...:     for x in range(2, n):
   ...:         if n % x == 0:
   ...:             print(n, 'equals', x, '*', n//x)
   ...:             break
   ...:     else:
   ...:         # loop fell through without finding a factor
   ...:         print(n, 'is a prime number')
   ...:
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3	
</code></pre>

(Yes, this is the correct code. Look closely: the `else` clause belongs to the [for](https://docs.python.org/3.8/reference/compound_stmts.html#for) loop, not the [if](https://docs.python.org/3.8/reference/compound_stmts.html#if) statement.)

When used with a loop, the `else` clause has more in common with the `else` clause of a [try](https://docs.python.org/3.8/reference/compound_stmts.html#try) statement than it does with that of [if](https://docs.python.org/3.8/reference/compound_stmts.html#if) statements: a [try](https://docs.python.org/3.8/reference/compound_stmts.html#try) statement’s `else` clause runs when no exception occurs, and a loop’s `else` clause runs when no `break` occurs. For more on the [try](https://docs.python.org/3.8/reference/compound_stmts.html#try) statement and exceptions, see **[Handling Exceptions](https://docs.python.org/3.8/tutorial/errors.html#tut-handling)**.

The [continue](https://docs.python.org/3.8/reference/simple_stmts.html#continue) statement, also borrowed from C, continues with the next iteration of the loop:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: for num in range(2, 10):
   ...:     if num % 2 == 0:
   ...:         print("Found an even number", num)
   ...:         continue
   ...:     print("Found an odd number", num)
   ...:
Found an even number 2
Found an odd number 3
Found an even number 4
Found an odd number 5
Found an even number 6
Found an odd number 7
Found an even number 8
Found an odd number 9	
</code></pre>

## `pass` Statements

The [pass](https://docs.python.org/3.8/reference/simple_stmts.html#pass) statement does nothing. It can be used when a statement is required syntactically but the program requires no action. For example:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">In [1]: while True:
    ...:    pass  # Busy-wait for keyboard interrupt (Ctrl+C)	
</code></pre>

This is commonly used for creating minimal classes:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">In [1]: class MyEmptyClass:
    ...:    pass	
</code></pre>

Another place [pass](https://docs.python.org/3.8/reference/simple_stmts.html#pass) can be used is as a place-holder for a function or conditional body when you are working on new code, allowing you to keep thinking at a more abstract level. The `pass` is silently ignored:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">In [1]: def initlog(*args):
    ...:    pass  # Remember to implement this!	
</code></pre>

![CassidyMedia Logo](./assets/wallpaper_without_slogan2.png)

Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)