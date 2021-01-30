
![Python logo](./assets/python-logo.png)
___
In the following examples, input and output are distinguished by the presence or absence of prompts ([>>>](https://docs.python.org/3.8/glossary.html#term-0) and […](https://docs.python.org/3.8/glossary.html#term-1)): to repeat the example, you must type everything after the prompt, when the prompt appears; lines that do not begin with a prompt are output from the interpreter. Note that a secondary prompt on a line by itself in an example means you must type a blank line; this is used to end a multi-line command.

Many of the examples in this manual, even those entered at the interactive prompt, include comments. Comments in Python start with the hash character, #, and extend to the end of the physical line. A comment may appear at the start of a line or following whitespace or code, but not within a string literal. A hash character within a string literal is just a hash character. Since comments are to clarify code and are not interpreted by Python, they may be omitted when typing in examples.

Some examples:
<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python"># this is the first comment
spam = 1  # and this is the second comment
          # ... and now a third!
text = "# This is not a comment because it's inside quotes."</code></pre>

## Using Python as a Calculator

Let’s try some simple Python commands. Start the interpreter and wait for the primary prompt, `>>>`. (It shouldn’t take long.)

### Numbers

The interpreter acts as a simple calculator: you can type an expression at it and it will write the value. Expression syntax is straightforward: the operators `+`, `-`, `*` and `/` work just like in most other languages (for example, Pascal or C); parentheses (`()`) can be used for grouping. For example:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python">>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # division always returns a floating point number
1.6</code></pre>

Now do the following exercise:
1. Open python interactive session: `python3`{{execute}}

2. Run this addition: `2 + 2`{{execute}}

3. Run this calculation: `(50 - 5*6) / 4`{{execute}}

4. Run this calculation: `8 / 5`{{execute}}

5. close the interactive session: `quit()`{{execute}}

The integer numbers (e.g. `2`, `4`, `20`) have type [int](https://docs.python.org/3.8/library/functions.html#int), the ones with a fractional part (e.g. `5.0`, `1.6`) have type float. We will see more about numeric types later in the tutorial.

Division (`/`) always returns a float. To do [floor division](https://docs.python.org/3.8/glossary.html#term-floor-division) and get an integer result (discarding any fractional result) you can use the `//` operator; to calculate the remainder you can use `%`:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python">>>> 17 / 3  # classic division returns a float
5.666666666666667
>>>
>>> 17 // 3  # floor division discards the fractional part
5
>>> 17 % 3  # the % operator returns the remainder of the division
2
>>> 5 * 3 + 2  # result * divisor + remainder
17</code></pre>

Now do the following exercise:
1. Open python interactive session: `python3`{{execute}}

2. Run this division: `17 / 3 # classic division returns a float`{{execute}}

3. Run this division: `17 // 3 # floor division discards the fractional part`{{execute}}

4. Run this calculation: `5 * 3 + 2  # result * divisor + remainder`{{execute}}

5. Terminal python session: `quit()`{{execute}}

With Python, it is possible to use the `**` operator to calculate powers:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python">>>> 5 ** 2  # 5 squared
25
>>> 2 ** 7  # 2 to the power of 7
128</code></pre>

Since `**` has higher precedence than `-`, `-3**2` will be interpreted as `-(3**2)` and thus result in `-9`. To avoid this and get `9`, you can use `(-3)**2`.

The equal sign (`=`) is used to assign a value to a variable. Afterwards, no result is displayed before the next interactive prompt:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python">&gt;&gt;&gt; width = 20
>>> height = 5 * 9
>>> width * height
900</code></pre>

If a variable is not “defined” (assigned a value), trying to use it will give you an error:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python">&gt;&gt;&gt; n  # try to access an undefined variable
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'n' is not defined</code></pre>

There is full support for floating point; operators with mixed type operands convert the integer operand to floating point:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python">&gt;&gt;&gt; 4 * 3.75 - 1
14.0</code></pre>

In interactive mode, the last printed expression is assigned to the variable `_`. This means that when you are using Python as a desk calculator, it is somewhat easier to continue calculations, for example:

<pre style="background-color: #FFE37F; border: 1px solid #C4C4C4;"><code class="python">&gt;&gt;&gt; tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06</code></pre>

This variable should be treated as read-only by the user. Don’t explicitly assign a value to it — you would create an independent local variable with the same name masking the built-in variable with its magic behavior.

In addition to [int](https://docs.python.org/3.8/library/functions.html#int) and [float](https://docs.python.org/3.8/library/functions.html#float), Python supports other types of numbers, such as [Decimal](https://docs.python.org/3.8/library/decimal.html#decimal.Decimal) and [Fraction](https://docs.python.org/3.8/library/fractions.html#fractions.Fraction). Python also has built-in support for complex numbers, and uses the j or J suffix to indicate the imaginary part (e.g. 3+5j).
This variable should be treated as read-only by the user. Don’t explicitly assign a value to it — you would create an independent local variable with the same name masking the built-in variable with its magic behavior.

In addition to int and float, Python supports other types of numbers, such as Decimal and Fraction. Python also has built-in support for complex numbers, and uses the j or J suffix to indicate the imaginary part (e.g. 3+5j).

![CassidyMedia Logo](./assets/cover_photo_without_slogan2.png)
Cassidy Media 2021 - All Content from [Python Tutorials](https://docs.python.org/3/tutorial/index.html)