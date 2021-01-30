
![Python Logo](./assets/python-logo.png)

___
Python knows a number of compound data types, used to group together other values. The most versatile is the list, which can be written as a list of comma-separated values (items) between square brackets. Lists might contain items of different types, but usually the items all have the same type.
<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> squares = [1, 4, 9, 16, 25]
>>> squares
[1, 4, 9, 16, 25]</code></pre>

Like strings (and all other built-in sequence types), lists can be indexed and sliced:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> squares[0]  # indexing returns the item
1
>>> squares[-1]
25
>>> squares[-3:]  # slicing returns a new list
[9, 16, 25]</code></pre>

All slice operations return a new list containing the requested elements. This means that the following slice returns a [shallow copy](https://docs.python.org/3.8/library/copy.html#shallow-vs-deep-copy) of the list:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> squares[:]
[1, 4, 9, 16, 25]</code></pre>

Lists also support operations like concatenation:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]</code></pre>

Unlike strings, which are [immutable](https://docs.python.org/3.8/glossary.html#term-immutable), lists are a [mutable](https://docs.python.org/3.8/glossary.html#term-mutable) type, i.e. it is possible to change their content:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> cubes = [1, 8, 27, 65, 125]  # something's wrong here
>>> 4 ** 3  # the cube of 4 is 64, not 65!
64
>>> cubes[3] = 64  # replace the wrong value
>>> cubes
[1, 8, 27, 64, 125]</code></pre>

You can also add new items at the end of the list, by using the `append()` method (we will see more about methods later):

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> cubes.append(216)  # add the cube of 6
>>> cubes.append(7 ** 3)  # and the cube of 7
>>> cubes
[1, 8, 27, 64, 125, 216, 343]</code></pre>

Assignment to slices is also possible, and this can even change the size of the list or clear it entirely:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # replace some values
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # now remove them
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> # clear the list by replacing all the elements with an empty list
>>> letters[:] = []
>>> letters
[]</code></pre>

The built-in function [len()](https://docs.python.org/3.8/library/functions.html#len) also applies to lists:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4</code></pre>

It is possible to nest lists (create lists containing other lists), for example:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'</code></pre>

![CassidyMedia Logo](./assets/wallpaper_without_slogan2.png)

Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)