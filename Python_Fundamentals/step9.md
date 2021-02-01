
![Python Logo](./assets/python-logo.png)

---

It is also possible to define functions with a variable number of arguments. There are three forms, which can be combined.

## Default Argument Values

The most useful form is to specify a default value for one or more arguments. This creates a function that can be called with fewer arguments than it is defined to allow. For example:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def ask_ok(prompt, retries=4, reminder='Please try again!'):
    while True:
        ok = input(prompt)
        if ok in ('y', 'ye', 'yes'):
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise ValueError('invalid user response')
        print(reminder)	
</code></pre>

This function can be called in several ways:

- giving only the mandatory argument: `ask_ok('Do you really want to quit?')`

- giving one of the optional arguments: `ask_ok('OK to overwrite the file?', 2)`

- or even giving all arguments: `ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')`

This example also introduces the [in](https://docs.python.org/3.8/reference/expressions.html#in) keyword. This tests whether or not a sequence contains a certain value.

The default values are evaluated at the point of function definition in the defining scope, so that

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">i = 5

def f(arg=i):
    print(arg)

i = 6
f()	
</code></pre>

will print `5`.

**Important warning**: The default value is evaluated only once. This makes a difference when the default is a mutable object such as a list, dictionary, or instances of most classes. For example, the following function accumulates the arguments passed to it on subsequent calls:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))	
</code></pre>

This will print

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">[1]
[1, 2]
[1, 2, 3]	
</code></pre>

If you don’t want the default to be shared between subsequent calls, you can write the function like this instead:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L	
</code></pre>

## Keyword Arguments

Functions can also be called using [keyword arguments](https://docs.python.org/3.8/glossary.html#term-keyword-argument) of the form `kwarg=value`. For instance, the following function:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")	
</code></pre>

accepts one required argument (`voltage`) and three optional arguments (`state`, `action`, and `type`). This function can be called in any of the following ways:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword	
</code></pre>

but all the following calls would be invalid:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">parrot()                     # required argument missing
parrot(voltage=5.0, 'dead')  # non-keyword argument after a keyword argument
parrot(110, voltage=220)     # duplicate value for the same argument
parrot(actor='John Cleese')  # unknown keyword argument	
</code></pre>

In a function call, keyword arguments must follow positional arguments. All the keyword arguments passed must match one of the arguments accepted by the function (e.g. `actor` is not a valid argument for the `parrot` function), and their order is not important. This also includes non-optional arguments (e.g. `parrot(voltage=1000)` is valid too). No argument may receive a value more than once. Here’s an example that fails due to this restriction:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> def function(a):
...     pass
...
>>> function(0, a=0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: function() got multiple values for keyword argument 'a'	
</code></pre>

When a final formal parameter of the form `**name` is present, it receives a dictionary (see [Mapping Types — dict](https://docs.python.org/3.8/library/stdtypes.html#typesmapping)) containing all keyword arguments except for those corresponding to a formal parameter. This may be combined with a formal parameter of the form *name (described in the next subsection) which receives a tuple containing the positional arguments beyond the formal parameter list. (`*name` must occur before `**name`.) For example, if we define a function like this:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def cheeseshop(kind, *arguments, **keywords):
    print("Do you have any", kind, "?")
    print("I'm sorry, we're all out of", kind)
    for arg in arguments:
        print(arg)
    print("-" * 40)
    for kw in keywords:
        print(kw, ":", keywords[kw])	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">cheeseshop("Limburger", "It's very runny, sir.",
           "It's really very, VERY runny, sir.",
           shopkeeper="Michael Palin",
           client="John Cleese",
           sketch="Cheese Shop Sketch")	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">Do you have any Limburger ?
I'm sorry, we're all out of Limburger
It's very runny, sir.
It's really very, VERY runny, sir.
----------------------------------------`
shopkeeper : Michael Palin
client : John Cleese
sketch : Cheese Shop Sketch	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
      -----------    ----------     ----------
        |             |                  |
        |        Positional or keyword   |
        |                                - Keyword only
         -- Positional only	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> def standard_arg(arg):
...     print(arg)
...
>>> def pos_only_arg(arg, /):
...     print(arg)
...
>>> def kwd_only_arg(*, arg):
...     print(arg)
...
>>> def combined_example(pos_only, /, standard, *, kwd_only):
...     print(pos_only, standard, kwd_only)	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> standard_arg(2)
2

>>> standard_arg(arg=2)
2	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> pos_only_arg(1)
1

>>> pos_only_arg(arg=1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: pos_only_arg() got an unexpected keyword argument 'arg'	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> kwd_only_arg(3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: kwd_only_arg() takes 0 positional arguments but 1 was given

>>> kwd_only_arg(arg=3)
3	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> combined_example(1, 2, 3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: combined_example() takes 2 positional arguments but 3 were given

>>> combined_example(1, 2, kwd_only=3)
1 2 3

>>> combined_example(1, standard=2, kwd_only=3)
1 2 3

>>> combined_example(pos_only=1, standard=2, kwd_only=3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: combined_example() got an unexpected keyword argument 'pos_only'	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def foo(name, **kwds):
    return 'name' in kwds	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> foo(1, **{'name': 2})
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: foo() got multiple values for argument 'name'
>>>	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def foo(name, /, **kwds):
    return 'name' in kwds
>>> foo(1, **{'name': 2})
True	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">def write_multiple_items(file, separator, *args):
    file.write(separator.join(args))	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> list(range(3, 6))            # normal call with separate arguments
[3, 4, 5]
>>> args = [3, 6]
>>> list(range(*args))            # call with arguments unpacked from a list
[3, 4, 5]	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> def parrot(voltage, state='a stiff', action='voom'):
...     print("-- This parrot wouldn't", action, end=' ')
...     print("if you put", voltage, "volts through it.", end=' ')
...     print("E's", state, "!")
...
>>> d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
>>> parrot(**d)
-- This parrot wouldn't VOOM if you put four million volts through it. E's bleedin' demised !	
</code></pre>

![CassidyMedia Logo](./assets/wallpaper_without_slogan2.png)

Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)