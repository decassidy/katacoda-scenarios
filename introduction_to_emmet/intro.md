# Fundamentals of Emmet

Emmet is a web-developer’s toolkit that can greatly improve your HTML & CSS workflow:

Basically, most text editors out there allow you to store and re-use commonly used code chunks, called “snippets”. While snippets are a good way to boost your productivity, all implementations have common pitfalls: you have to define the snippet first and you can’t extend them in runtime.

Emmet takes the snippets idea to a whole new level: you can type CSS-like expressions that can be dynamically parsed, and produce output depending on what you type in the abbreviation. Emmet is developed and optimised for web-developers whose workflow depends on HTML/XML and CSS, but can be used with programming languages too. 

Start learning Emmet with the [abbreviation syntax](https://docs.emmet.io/abbreviations/) and available [actions](https://docs.emmet.io/actions/).

### Elements
You can use elements’ names like div or p to generate HTML tags. Emmet doesn’t have a predefined set of available tag names, you can write any word and transform it into a tag: **`div → <div></div>, foo → <foo></foo>`** and so on.

### Nesting Operators
Nesting operators are used to position abbreviation elements inside generated tree: whether it should be placed inside or near the context element.

#### Child: `>`
You can use `>` operator to nest elements inside each other:

### **`div>ul>li`**

... will produce

```HTML
<div>
    <ul>
        <li></li>
    </ul>
</div>
```

### Sibling: `+`
Use **`+`** operator to place elements near each other, on the same level:

### **`div+p+bq`**

... will produce

```HTML
<div></div>
<p></p>
<blockquote></blockquote>
```

### Climb-up: `^`
With `>` operator you’re descending down the generated tree and positions of all sibling elements will be resolved against the most deepest element:

### **`div+div>p>span+em`**

... will be expanded to

```HTML
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
```

With `^` operator, you can climb one level up the tree and change context where following elements should appear:

### **`div+div>p>span+em^bq`**

... outputs to

```HTML
<div></div>
<div>
    <p><span></span><em></em></p>
    <blockquote></blockquote>
</div>
```

You can use as many **`^`** operators as you like, each operator will move one level up:

### **`div+div>p>span+em^^^bq`**

...will output to

```HTML
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
<blockquote></blockquote>
```

### Multiplication: `*`
With **`*`** operator you can define how many times element should be outputted:

### **`ul>li*5`**

... outputs to

```HTML
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```