# Abbreviations

Abbreviations are the heart of the Emmet toolkit: these special expressions are parsed in runtime and transformed into structured code block, HTML for example. The abbreviation’s syntax looks like CSS selectors with a few extensions specific to code generation. So every web-developer already knows how to use it. 

Here’s an example: this abbreviation:

```#page>div.logo+ul#navigation>li*5>a{Item $}```

```HTML
<div id="page">
    <div class="logo"></div>
    <ul id="navigation">
        <li><a href="">Item 1</a></li>
        <li><a href="">Item 2</a></li>
        <li><a href="">Item 3</a></li>
        <li><a href="">Item 4</a></li>
        <li><a href="">Item 5</a></li>
    </ul>
</div>
```

...with just a single key stroke. In many editors (such as Eclipse, Sublime Text 2, Espresso etc.) plugins will also generate proper tabstop marks so you can quickly traverse between important places of generated code with the Tab key.

Abbreviations are optimised for, but not limited to, HTML and XML generation, and make writing tedious markup code a breeze. You can start learning [syntax](https://docs.emmet.io/abbreviations/syntax/) to unleash the full power of Emmet abbreviations.

1. Click on the command link below to initialize this lesson.

##### ```mkdir emmet-lessons && cd emmet-lessons && touch emmet-syntax.html```{{execute}}

2. Open the 'emmet-syntax.html" file in VS Code using the link below to get started.

##### ```./emmet-lessons/emmet-syntax.html```{{open}}

3. Click the link below to add the Emmet syntax line then tap the <kbd>Tab</kbd> to expand the syntax to HTML:
   
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Emmet Abbreviations</title>
</head>
<body>
    <!-- Type the following Emmet Syntax and hit the TAB key to expand it.-->
    
</body>
</html>
```{{copy}}

4. Copy the following HTML code below the comment in the *`./emmet-lessons/emmet-syntax.html`*

`.page>div.logo+ul#navigation>li*5>a{Item $`{{copy}}

5. Add *`}`* closing bracket to the emmet abbreviation and press the <kbd>tab</kbd> Key.

You should see the above abbreviation output like this:

```HTML
<div id="page">
    <div class="logo"></div>
    <ul id="navigation">
        <li><a href="">Item 1</a></li>
        <li><a href="">Item 2</a></li>
        <li><a href="">Item 3</a></li>
        <li><a href="">Item 4</a></li>
        <li><a href="">Item 5</a></li>
    </ul>
</div>
```

