
![Python Logo](https://i.imgur.com/yOGqfxX.png)


---

Besides numbers, Python can also manipulate strings, which can be expressed in several ways. They can be enclosed in single quotes (`'...'`) or double quotes (`"..."`) with the same result `\` can be used to escape quotes:

<pre><code class="python">&gt;&gt;&gt; 'spam eggs'  # single quotes
'spam eggs'
>>> 'doesn\'t'  # use \' to escape the single quote...
"doesn't"
>>> "doesn't"  # ...or use double quotes instead
"doesn't"
>>> '"Yes," they said.'
'"Yes," they said.'
>>> "\"Yes,\" they said."
'"Yes," they said.'
>>> '"Isn\'t," they said.'
'"Isn\'t," they said.'
</code></pre>

In the interactive interpreter, the output string is enclosed in quotes and special characters are escaped with backslashes. While this might sometimes look different from the input (the enclosing quotes could change), the two strings are equivalent. The string is enclosed in double quotes if the string contains a single quote and no double quotes, otherwise it is enclosed in single quotes. The [print()](https://docs.python.org/3.8/library/functions.html#print) function produces a more readable output, by omitting the enclosing quotes and by printing escaped and special characters:

<pre><code class="python">>>> '"Isn\'t," they said.'
'"Isn\'t," they said.'
>>> print('"Isn\'t," they said.')
"Isn't," they said.
>>> s = 'First line.\nSecond line.'  # \n means newline
>>> s  # without print(), \n is included in the output
'First line.\nSecond line.'
>>> print(s)  # with print(), \n produces a new line
First line.
Second line.
</code></pre>

If you don’t want characters prefaced by `\` to be interpreted as special characters, you can use raw strings by adding an `r` before the first quote:

<pre><code class="python">>>> print('C:\some\name')  # here \n means newline!
C:\some
ame
>>> print(r'C:\some\name')  # note the r before the quote
C:\some\name
</code></pre>

String literals can span multiple lines. One way is using triple-quotes: `"""..."""` or `'''...'''`. End of lines are automatically included in the string, but it’s possible to prevent this by adding a `\` at the end of the line. The following example:

<pre><code class="python">print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
</code></pre>

produces the following output (note that the initial newline is not included):

<pre><code class="python">Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
</code></pre>

Strings can be concatenated (glued together) with the `+` operator, and repeated with `*`:

<pre><code class="python">>>> # 3 times 'un', followed by 'ium'
>>> 3 * 'un' + 'ium'
'unununium'
</code></pre>

Two or more string literals (i.e. the ones enclosed between quotes) next to each other are automatically concatenated.

<pre><code class="python">>>> 'Py' 'thon'
'Python'
</code></pre>

This feature is particularly useful when you want to break long strings:

<pre><code class="Python">>>> text = ('Put several strings within parentheses '
...         'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'
</code></pre>

This only works with two literals though, not with variables or expressions:

<pre><code class="python">>>> prefix = 'Py'
>>> prefix 'thon'  # can't concatenate a variable and a string literal
  File "<stdin>", line 1
    prefix 'thon'
                ^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  File "<stdin>", line 1
    ('un' * 3) 'ium'
                   ^
SyntaxError: invalid syntax
</code></pre>

If you want to concatenate variables or a variable and a literal, use `+`:

<pre><code class="python">>>> prefix + 'thon'
'Python'
</code></pre>

Strings can be indexed (subscripted), with the first character having index 0. There is no separate character type; a character is simply a string of size one:

<pre><code class="python">>>> word = 'Python'
>>> word[0]  # character in position 0
'P'
>>> word[5]  # character in position 5
'n'
</code></pre>

Indices may also be negative numbers, to start counting from the right:

<pre><code class="python">>>> word[-1]  # last character
'n'
>>> word[-2]  # second-last character
'o'
>>> word[-6]
'P'
</code></pre>

Note that since -0 is the same as 0, negative indices start from -1.

In addition to indexing, slicing is also supported. While indexing is used to obtain individual characters, slicing allows you to obtain substring:

<pre><code class="python">
>>> word[0:2]  # characters from position 0 (included) to 2 (excluded)
'Py'
>>> word[2:5]  # characters from position 2 (included) to 5 (excluded)
'tho'
</code></pre>

Note how the start is always included, and the end always excluded. This makes sure that `s[:i] + s[i:]` is always equal to `s`:

<pre><code class="python">>>> word[:2] + word[2:]
'Python'
>>> word[:4] + word[4:]
'Python'
</code></pre>

Slice indices have useful defaults; an omitted first index defaults to zero, an omitted second index defaults to the size of the string being sliced.

<pre><code class="python">>>> word[:2]   # character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]   # characters from position 4 (included) to the end
'on'
>>> word[-2:]  # characters from the second-last (included) to the end
'on'
</code></pre>

One way to remember how slices work is to think of the indices as pointing between characters, with the left edge of the first character numbered 0. Then the right edge of the last character of a string of n characters has index n, for example:

<pre><code class="python"> +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
</code></pre>

The first row of numbers gives the position of the indices 0…6 in the string; the second row gives the corresponding negative indices. The slice from i to j consists of all characters between the edges labeled i and j, respectively.

For non-negative indices, the length of a slice is the difference of the indices, if both are within bounds. For example, the length of `word[1:3]` is 2.

Attempting to use an index that is too large will result in an error:

<pre><code class="python">>>> word[42]  # the word only has 6 characters
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
</code></pre>

However, out of range slice indexes are handled gracefully when used for slicing:

<pre><code class="python">>>> word[4:42]
'on'
>>> word[42:]
''
</code></pre>

Python strings cannot be changed — they are immutable. Therefore, assigning to an indexed position in the string results in an error:

<pre><code class="python">>>> word[0] = 'J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
</code></pre>

If you need a different string, you should create a new one:

<pre><code class="python">>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
</code></pre>

The built-in function [len()](https://docs.python.org/3.8/library/functions.html#len) returns the length of a string:

<pre><code class="python">>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
34
</code></pre>



__See also__
<dl style="background: #2787E7; color: white; padding: 15px">

<dt>
<a href="https://docs.python.org/3.8/library/stdtypes.html#textseq" style="color: yellow;">Text Sequence Type — str</a>
</dt>
<dd>Strings are examples of sequence types, and support the common operations supported by such types.</dd>

<dt>
<a href="https://docs.python.org/3.8/library/stdtypes.html#string-methods" style="color: yellow;">String Methods</a>
</dt>
<dd>Strings support a large number of methods for basic transformations and searching.</dd>
    
<dt>
<a href="https://docs.python.org/3.8/reference/lexical_analysis.html#f-strings" style="color: yellow;">Formatted string literals</a>
</dt>
<dd>String literals that have embedded expressions.</dd>

<dt>
<a href="https://docs.python.org/3.8/library/string.html#formatstrings" style="color: yellow;">Format String Syntax</a>
</dt>
<dd>Information about string formatting with <code>str.format().</code></dd>

<dt>
<a href="https://docs.python.org/3.8/library/stdtypes.html#old-string-formatting" style="color: yellow;">printf-style String Formatting</a> 
</dt>
<dd>The old formatting operations invoked when strings are the left operand of the % operator are described in more detail here.</dd>
</dl>



Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)