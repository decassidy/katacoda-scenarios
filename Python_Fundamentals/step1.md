
The Python interpreter is usually installed as  `/usr/local/bin/python3.8` on those machines where it is available; putting  `/usr/local/bin` in your Unix shell’s search path makes it possible to start it by typing the command:

```BASH
python3.8
```

to the shell. Since the choice of the directory where the interpreter lives is an installation option, other places are possible; check with your local Python guru or system administrator.  (E.g., `/usr/local/python` is a popular alternative location.)

Typing an end-of-file character ( *`Control-D`* on Unix,  *`Control-Z`* on Windows)  at the primary prompt causes the interpreter to exit with a zero exit status. If that doesn’t work, you can exit the interpreter by typing the following command:  *`quit()`*.

The interpreter’s line-editing features include interactive editing, history substitution and code completion on systems that support the [GNU Readline library](https://tiswww.case.edu/php/chet/readline/rltop.html). Perhaps the quickest check to see whether command line editing is supported is typing  *`Control-P`* to the first Python prompt you get. If it beeps, you have command line editing; see Appendix [Interactive Input Editing and History Substitution](https://docs.python.org/3.8/tutorial/interactive.html#tut-interacting) for an introduction to the keys. If nothing appears to happen, or if *`^P`* is echoed, command line editing isn’t available; you’ll only be able to use backspace to remove characters from the current line.

The interpreter operates somewhat like the Unix shell: when called with standard input connected to a tty device, it reads and executes commands interactively; when called with a file name argument or with a file as standard input, it reads and executes a script from that file.

A second way of starting the interpreter is :point_right: *`python -c command [arg] ...`*, which executes the statement(s) in command, analogous to the shell’s :point_right: *`-c`* option. Since Python statements often contain spaces or other characters that are special to the shell, it is usually advised to quote command in its entirety with single quotes.

Some Python modules are also useful as scripts. These can be invoked using :point_right: *`python -m module [arg] ...`*, which executes the source file for module as if you had spelled out its full name on the command line.

When a script file is used, it is sometimes useful to be able to run the script and enter interactive mode afterwards. This can be done by passing [-i](https://docs.python.org/3.8/using/cmdline.html#cmdoption-i) before the script.

All command line options are described in [Command line and environment](https://docs.python.org/3.8/using/cmdline.html#using-on-general).

## :smiley_cat: Argument Passing

When known to the interpreter, the script name and additional arguments thereafter are turned into a list of strings and assigned to the  *`argv`* variable in the  *`sys`* module. You can access this list by executing  *`import sys`*. The length of the list is at least one; when no script and no arguments are given,  *`sys.argv[0]`* is an empty string. When the script name is given as  *`'-'`* (meaning standard input),  *`sys.argv[0]`* is set to  *`'-'`*. When  *`-c`* command is used,  *`sys.argv[0]`* is set to  *`'-c'`*. When  *`-m`* module is used,  *`sys.argv[0]`* is set to the full name of the located module. Options found after  *`-c`* command or  *`-m`* module are not consumed by the Python interpreter’s option processing but left in  *`sys.argv`* for the command or module to handle.

## :smiley_cat: Interactive Mode

When commands are read from a tty, the interpreter is said to be in interactive mode. In this mode it prompts for the next command with the primary prompt, usually three greater-than signs (*`>>>`*); for continuation lines it prompts with the secondary prompt, by default three dots (*`...`*). The interpreter prints a welcome message stating its version number and a copyright notice before printing the first prompt:


<pre><code class="vscode-dark">
$ python3.8
Python 3.8 (default, Sep 16 2015, 09:25:04)
[GCC 4.8.2] on linux
Type "help", "copyright", "credits" or "license" for more information.
&gt;&gt;&gt;
</code></pre>
1. Open the Python Interactive session:<br>
:smiley_cat: `python3.8`{{execute}}

2. Run the command:<br> 
:smiley_cat: `15 * 20`{{execute}}
<br>
3. Exit Python Interactive Mode:<br>
:smiley_cat: `quit()`{{execute}}