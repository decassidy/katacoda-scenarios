
![Python Logo](./assets/python-logo.png)

---
We can create a function that writes the Fibonacci series to an arbitrary boundary:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: def fib(n):    # write Fibonacci series up to n
   ...:     """Print a Fibonacci series up to n."""
   ...:     a, b = 0, 1
   ...:     while a < n:
   ...:         print(a, end=' ')
   ...:         a, b = b, a+b
   ...:     print()
   ...:

In [2]: # Now call the function we just defined:

In [3]: fib(2000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597	
</code></pre>

The keyword [def](https://docs.python.org/3.8/reference/compound_stmts.html#def) introduces a function definition. It must be followed by the function name and the parenthesized list of formal parameters. The statements that form the body of the function start at the next line, and must be indented.

The first statement of the function body can optionally be a string literal; this string literal is the function’s documentation string, or docstring. (More about docstrings can be found in the section **[Documentation Strings](https://docs.python.org/3.8/tutorial/controlflow.html#tut-docstrings)**.) There are tools which use docstrings to automatically produce online or printed documentation, or to let the user interactively browse through code; it’s good practice to include docstrings in code that you write, so make a habit of it.

The execution of a function introduces a new symbol table used for the local variables of the function. More precisely, all variable assignments in a function store the value in the local symbol table; whereas variable references first look in the local symbol table, then in the local symbol tables of enclosing functions, then in the global symbol table, and finally in the table of built-in names. Thus, global variables and variables of enclosing functions cannot be directly assigned a value within a function (unless, for global variables, named in a [global](https://docs.python.org/3.8/reference/simple_stmts.html#global) statement, or, for variables of enclosing functions, named in a [nonlocal](https://docs.python.org/3.8/reference/simple_stmts.html#nonlocal) statement), although they may be referenced.

The actual parameters (arguments) to a function call are introduced in the local symbol table of the called function when it is called; thus, arguments are passed using call by value (where the value is always an object reference, not the value of the object). 1 When a function calls another function, a new local symbol table is created for that call.

A function definition associates the function name with the function object in the current symbol table. The interpreter recognizes the object pointed to by that name as a user-defined function. Other names can also point to that same function object and can also be used to access the function:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: fib
Out[1]: &lt;function __main__.fib(n)&gt;

In [2]: f = fib

In [3]: f(100)
0 1 1 2 3 5 8 13 21 34 55 89
</code></pre>

Coming from other languages, you might object that `fib` is not a function but a procedure since it doesn’t return a value. In fact, even functions without a [return](https://docs.python.org/3.8/reference/simple_stmts.html#return) statement do return a value, albeit a rather boring one. This value is called `None` (it’s a built-in name). Writing the value `None` is normally suppressed by the interpreter if it would be the only value written. You can see it if you really want to using [print()](https://docs.python.org/3.8/library/functions.html#print):

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: fib(0)

In [2]: print(fib(0))

None
</code></pre>

It is simple to write a function that returns a list of the numbers of the Fibonacci series, instead of printing it:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: def fib2(n):  # return Fibonacci series up to n
   ...:     """Return a list containing the Fibonacci series up to n."""
   ...:     result = []
   ...:     a, b = 0, 1
   ...:     while a < n:
   ...:         result.append(a)    # see below
   ...:         a, b = b, a+b
   ...:     return result
   ...:

In [2]: f100 = fib2(100)    # call it

In [3]: f100                # write the result
Out[3]: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
</code></pre>

This example, as usual, demonstrates some new Python features:

>The [return](https://docs.python.org/3.8/reference/simple_stmts.html#return) statement returns with a value from a function. return without an expression argument returns `None`. Falling off the end of a function also returns `None`.

>The statement `result.append(a)` calls a method of the list object `result`. A method is a function that ‘belongs’ to an object and is named `obj.methodname`, where `obj` is some object (this may be an expression), and `methodname` is the name of a method that is defined by the object’s type. Different types define different methods. Methods of different types may have the same name without causing ambiguity. (It is possible to define your own object types and methods, using classes, see [Classes](https://docs.python.org/3.8/tutorial/classes.html#tut-classes)) The method `append()` shown in the example is defined for list objects; it adds a new element at the end of the list. In this example it is equivalent to `result = result + [a`]`, but more efficient.


![CassidyMedia Logo](./assets/wallpaper_without_slogan2.png)

Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)