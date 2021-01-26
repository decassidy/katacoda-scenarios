
The Python interpreter is usually installed as `/usr/local/bin/python3.8` on those machines where it is available; putting `/usr/local/bin` in your Unix shell’s search path makes it possible to start it by typing the command:

```BASH
python3.8
```

to the shell. Since the choice of the directory where the interpreter lives is an installation option, other places are possible; check with your local Python guru or system administrator.  (E.g., `/usr/local/python` is a popular alternative location.)

Typing an end-of-file character (*`Control-D`* on Unix, *`Control-Z`* on Windows)  at the primary prompt causes the interpreter to exit with a zero exit status. If that doesn’t work, you can exit the interpreter by typing the following command: *`quit()`*.

The interpreter’s line-editing features include interactive editing, history substitution and code completion on systems that support the [GNU Readline library](https://tiswww.case.edu/php/chet/readline/rltop.html). Perhaps the quickest check to see whether command line editing is supported is typing *`Control-P`* to the first Python prompt you get. If it beeps, you have command line editing; see Appendix [Interactive Input Editing and History Substitution](https://docs.python.org/3.8/tutorial/interactive.html#tut-interacting) for an introduction to the keys. If nothing appears to happen, or if *`^P`* is echoed, command line editing isn’t available; you’ll only be able to use backspace to remove characters from the current line.