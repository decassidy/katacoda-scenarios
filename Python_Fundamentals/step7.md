
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
<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
...
cat 3
window 6
defenestrate 12	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>



<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="py">	
</code></pre>

![CassidyMedia Logo](./assets/wallpaper_without_slogan2.png)

Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)