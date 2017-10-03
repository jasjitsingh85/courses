# Build a Webapp with jQuery and Javascript

## Introduction

Today we’re going to get an introduction to JavaScript by building a [simple shopping list application](https://unique-heart.glitch.me/). 

[Thinkful](https://www.thinkful.com/) is hosting this event. Thinkful is a bootcamp that helps people become developers and data scientists through 1-on-1 mentorship and project-based learning.

Today you’ll be working with junior Thinkful mentors to learn the key concepts and build the project. The lessons you see below are taken and abridged from Thinkful's full-stack developer program. As you read this, make sure to ask for help from your TA's when you're confused about a concept. If you're still stuck on a concept, just skip to the next section and come back to it once you start working on your project. 

Lets get started!

# HTML Review

Of all the computer languages we'll look at in this course, HTML (hypertext markup language) is the simplest. That's because it's not a full fledged *programming language*. You can't write logical statements using HTML like you can with a programming language like Javascript (where, for instance, you can have code that behaves one way if some condition is true, and another if that condition is false). Instead, HTML is used to *mark up* content so web browsers know what kinds of content they're dealing with.

For the most part, that's all there is to HTML: you take content and wrap it in the appropriate tags.

### Elements vs. tags vs. attributes

There are three key HTML-related terms you need to be able to use correctly in order to come across as competent in interviews: *element*, *tag*, and *attribute*. Let's distinguish these with an example:

```html
<div class="foo-class">
  <p>This is a paragraph with <a href="https://somewhere.com">a link</a> in it.</p>
  <p id="second-paragraph">This is the second paragraph</p>
</div>
```

This snippet has four elements: 1 div, 2 paragraphs, and one anchor. If we look at the `<div>` element, it consists of an *opening tag* (`<div>`) some inner content (the two paragraphs), and a *closing tag* (`</div>`).

To generalize, an HTML element *usually* consists of some content (could be plain text or additional HTML elements) wrapped by *opening* and *closing* tags.

*Tags*, then, are used to mark off the beginning and end of an element. Both opening and closing tags consist of angle brackets and the tag name (`< ... >`), with closing tags  distinguished by a forward slash (`</ ...>`).

Note that the reason we said that HTML elements *usually* consist of content wrapped by an opening and closing tag is because some elements are *self closing* and don't have inner content. For example, the `<img>` element, which is used to embed images in an HTML document, has no inner content, and doesn't require a closing tag. So this image element is well-formed: `<p>This paragraph has an image: <img src="./images/foo.jpg"></p>`.

Finally, *attributes* are for setting properties on an HTML element. In the example above, there are three attributes: `class="foo-class"`, `href="https://www.somewhere.com"`, and `id="second-paragraph"`. HTML attributes consist of a name (e.g., `href`) and a value enclosed in quotes (e.g., "https://www.somewhere.com").

Some attributes, like *class* and *id* are valid on almost any HTML element. We'll learn more about using classes and ids as hooks for CSS styles and JavaScript code later in this course. We present them now because they are core HTML attributes that can be used on all but a handful of elements (specifically, they can’t be used on: `<base>`, `<head>`, `<meta>`, `<param>`, or `<title>`).

Other attributes are specific to a particular element. The `href` attribute on our anchor element above is specific to anchor elements.


### Structuring content with HTML

In the programming world, it's commonly said that HTML is about *structuring* content while CSS, which we'll cover in depth in the next lesson, is about *styling* content. HTML tells the browser *what* content to represent, while CSS tells the browser *how* that content should appear.

When we say that HTML is about *structuring* content, we mean two things. First, we mean that an HTML document specifies each and every one of its elements. These can be visible elements (paragraphs and images) or ones that human users never see (for instance, `<meta>` elements appearing in the head of the document).

Second, HTML specifies the *hierarchical relationship* between elements in a document. Below, we have a snippet of HTML, followed by a chart depicting the hierarchical structure of that HTML:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Sally Student | About me</title>
  <link rel="stylesheet" type="text/css" href="./main.css">
  <script type="text/javascript" src='./main.js'></script>
  <meta charset="utf-8">
</head>
<body>

  <nav>
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/about_me">About me</a></li>
      <li><a href="/blog">Blog</a></li>
    </ul>
  </nav>

  <header>
    <h1>About me</h1>
  </header>

  <main>
    <h2>My work</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
    quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
    consequat.</p>
  </main>
</body>
</html>
```

![html_document.png](html_document.png)

Each element from the HTML snippet appears in this diagram, which reveals the *tree structure* of our HTML code. This tree consists of a series of *nodes* (each represented by a box) which lie in hierarchical relation to one another. We call the `<html>` element the *root element* because it is the parent (or grandparent, or great grandparent, etc.) of all other elements in the document. The root element has children (`<head>` and `<body>`).

Looking at the `<li>` elements in the `<nav>`, we find our most nested elements. We have list items inside an unordered list inside a nav inside the body inside the root HTML element.

Nodes existing at the same level of the hierarchy (for instance, the `<nav>`, `<header>`, and `<main>` elements above) are called siblings.

Finally, notice how we use a level one heading (`<h1>`) in the `<header>` and then a level two heading (`<h2>`) in the `<main>`. [Heading elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements) (`h1`, `h2`, `h3`, `h4`, `h5`, `h6`) are used to establish information hierarchy. Although these elements are often styled so that `h1`s are bigger than `h2`s are bigger than `h3`s etc., their main role is to indicate the relative importance of different content in the page. There should only ever be one `h1` for the page, and it's used to indicate what the page is about. It's fine to have more than one `h2` to `h6`, but don't skip headings or pick headings just for their sizes, which can be changed with CSS. For instance, don't have an `h1`, then two `h2`s, and jump to four `h5`s.


## CSS Review

## Programming in JavaScript

Programming is the process of translating a problem stated in plain language into a set of instructions for solving that problem (this is what is meant by the term *algorithm*), and then expressing your algorithm in terms that your computer can understand (that is, expressing it in a programming language).

A *program*, in simplest terms, is a set of instructions for a computer to carry out. In the context of frontend web development, you might write a program for validating form inputs when the user submits their username and password to a form, or checking to make sure they’ve typed a valid phone number before passing the data to a server. Or you might have a program that retrieves data from the Twitter API and displays an interesting visualization of your user's friend and follower network. There's literally an infinite number of programs you could write.

## Variable Basics

A variable is a name that is attached to a value. Variables open up two possibilities.

First, they give us a shorthand way to refer to values created elsewhere in a program. We can declare and define a variable once, and pass that value around in our code without having to rewrite it each time.

Second, variables give us a way to manage *state* in a program. *State* has to do with persisting values over time in a program. That probably sounds abstract, so let's look at a concrete example. Consider the following interface, which displays to the user how many times they've clicked a button (super useful, right!?):

<iframe height="500px" width="100%" src="https://repl.it/IgSp/2"></iframe>

Take a minute to read through the code comments in the JavaScript code in this Repl.it to get a sense of what it's doing. Click the "index.js" tab to see the JavaScript code, then click the "run" button at the top of the Repl.it to run the code. Remember, the goal at this moment is not to master the syntax; instead, we want you to start get a feel for this idea of *state*.

In this simple program, the application state is maintained in a single `clickCount` variable. When the user clicks the button, we add 1 to the value currently stored in `clickCount`, display the updated click count to the user, then wait for any additional clicks, and when they happen, run the same instructions again. We say that in between successive calls to the function (that is, the `function(event) {....}` part of the code), the application's state is maintained in the `clickCount` variable. At any point when this program is running, the `clickCount` variable tells everyone else how many clicks have happened. Variables give us a way of persisting this information for the life of the program.

## Defining variables with `let`

`let` is used to define variables whose values can (but need not) be reassigned.

```javascript
let pi = 3.14159;
console.log(pi); // => 3.14159
// on second thought, let's round to the nearest tenth place...
pi = 3.1;
console.log(pi); // 3.1
```

In this example, we initially create a variable `pi` whose value is 3.14159. We print out that value, then change the value of `pi` to 3.1, and then print that value. Because we've defined this variable using `let`, the browser allows us to assign a new value to `pi`.

We can initially *declare* a variable without yet assigning a value. When you *declare* a variable, you create a link between a variable name, and a place in the computer's memory that stores the value of that variable. The syntax for declaring a variable looks like this:

```javascript
let myVar;
```

When you declare a variable, it doesn't have a value yet. By default, JavaScript gives declared (but unassigned) variables the special value `undefined` (which we’ll discuss below).

To assign a value to a declared variable, we use the same assignment operator we saw above:

```javascript
let myVar;
myVar = 6;
```

Here we've said that the value of the variable `myVar` is 6, and that information is stored in memory.

## Naming variables

The names you choose for variables are important.

On the one hand, there are some rules about how variable names *must* look in order for the JavaScript interpreter to recognize that our code is talking about a variable. On the other hand, there are stylistic conventions about how we *should* name our variables.

You can find a full account of the rules governing variable names in JavaScript [here](https://mathiasbynens.be/notes/javascript-identifiers). Here, we mention the following:

* **Reserved words**: Reserved words are a special category of words that you're not allowed to use as variable names in a given programming language. For instance, in JavaScript, you can't reassign the name `var` to a new value (that is, you can't  do `var var = 'some value';`). If you try to use a reserved word as a variable name, you'll get an error. Note that reserved words *can* be used within a variable name (so `var varFoo;` is okay).
* **Character restrictions**: A variable name must begin with an upper or lower case letter, `$` or `_`.  It cannot begin with a number. Numbers can be used elsewhere in the variable name (`var myFoo2;` is okay). Spaces cannot appear anywhere in the variable name (`var my Foo = 'bar';`, not okay). Comparison and logical operators cannot be used in variable names (`var my+Foo;` is  not okay).

There are also best practices that you *should* follow. If you don't it won't cause your code to break, but it will make your code look strange to other JavaScript developers and make it harder to maintain. Here are the most important stylistic guidelines:

* **camelCasing**: JavaScript developers have an unwritten agreement to use *camel-casing* for variable names. Camel-casing looks like this: `thisIsCamelCasing`. A camel-cased variable name starts with a lowercase letter, and then uses lowercase letters throughout, except for the first letter of any new words in the variable name after the first -- for these first letters, use uppercase. There are agreed upon cases where we use TitleCasing in JavaScript (for instance, when creating [object constructors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor#Examples), which is an advanced topic that you don't need to understand at the moment), but the general rule is use camel-casing.
* **Choose meaningful variable names*: When we learned about HTML, we learned about the idea of *semantic HTML*, which says that the type of element we choose should reflect the type of content that element provides. In a similar way, when we choose variable names in JavaScript, we should choose names that reflect how the variable gets used in the program. A well chosen variable name can help other people reading the code to understand how the variable is intended to be used. In the click counter app at the top of this reading, we had the variable name `clickCount`. When you read that name, you already have a sense of what it does. If we had named that same variable `y`, the code would have worked exactly the same, but its meaning becomes less clear.

## Javascript Data Types

A *data type* is a kind of value that variables can have in a given programming language. JavaScript has six data types: `String`, `Number`, `Boolean`, `Null`, `Undefined`, and `Object`. We'll give you a brief introduction to all 6 data types. The goal here is to give you a lay of the land, not for you to memorize all the information in this reading.

### Strings

Strings are delineated by opening and closing quotes (either single or double, but both must be same kind, you can't open with a single, and close with a double): `let foo = 'bar';` and `let bar = "foo";` are both valid.

Strings are used to represent text. It's [*basically* the case](http://stackoverflow.com/a/11141331) that any character from the [Unicode](https://en.wikipedia.org/wiki/Unicode) character encoding scheme can be represented in a JavaScript string.

<img src="string-variables.gif" class="no-expand">

### Numbers

The number type in JavaScript is used to represent numbers — both integer values (that is to say, whole numbers like 1, 2, 3, 10000000...) and floating point decimal numbers (that is, numbers like 1.234999).

<img src="number-variables.gif" class="no-expand">

### `null`

`null` is a special value used to indicate that a variable has no value. It's not uncommon to see code that defaults to assigning `null` when other data is not available.

### booleans

```javascript

let loggedIn = false;

if (!loggedIn) {
  redirectToLoginScreen();
}
```

Booleans signify truth and falsity. A boolean has two possible values: `true` and `false`. In the example above, we set `loggedIn` to false, and we then have a block of code that runs if and only if the user is not logged in. The `!` in `!loggedIn` inverts the Boolean value of the item to the right of it, so `!false` evaluates to `true` and `!true` evaluates to false.

### `undefined`

We encountered `undefined` in the previous assignment when we discussed *declaring* variables before assigning values to them. `undefined` is a special value that the browser assigns to variables when it first creates them in memory.

You should never directly set a value to `undefined`. It's fine to check if a variable is `undefined`, but you shouldn't do `let foo = undefined;`. If you want to represent the absence of a value, use `null`.

### functions

A function is a mini program that you define once in your code and invoke or call elsewhere.

```javascript
function sayHello(personName) {
 const greeting =  "Hi there, " + personName;
 console.log(greeting);
}

```

Functions are values, but not in quite the same way as the preceding data types. Whereas numbers, strings, Booleans, null, and undefined all represent a discrete, specific value, a *function* describes a thing that's a bit hard to pin down: a set of instructions that can be run elsewhere. These instructions can create, manipulate and reference the simple data types described above.

### objects

Objects are considered to be a *complex data type* because they combine the *primitive data types* we've just explored (numbers, strings, Boolean, null, undefined).

Objects allow us to have variables that don't point to a single value (say for instance, a single string), but instead to a collection of values. Here's an example of a JavaScript object:

```javascript
const person = {
  name: 'Jane Doe',
  greet: function() {
    console.log('Hello world');
  }
}

console.log(person.name); // => Jane Doe
person.greet(); // => Hello world
```

## Function Basics
Functions are one of the most important concepts in programming. A function describes a repeatable process or behavior. You define that behavior once, and you can call it whenever you need to run your set of instructions.

Let's look at an example: JavaScript's built in `alert` function. Open the JavaScript console in Developer Tools, enter the following command, and hit enter: `alert('Hello from JavaScript land')`. You should see a pop up window displaying 'Hello from JavaScript land'.


![js-dev-tools-alert.gif](js-dev-tools-alert.gif)


`alert` takes one *argument*, the text you want to display in the alert. In the context of functions, an *argument* (or *parameter*) is a variable that gets passed to the function when it's called.

The name `alert` is well chosen. Just knowing the name of the function gives us a good sense of what it does. A well chosen function name can make clear what might otherwise require multiple lines of comments to explain.

Well crafted functions like alert have a *single responsibility*. This means that they are designed to do one thing and do it well. `alert`'s sole responsibility is to display a pop-up window to the user with a message in it.

Well crafted functions are also *determinate*. Given the same inputs on separate invocations, the result should be exactly the same. No matter what else is happening in your program, when you run `alert('foo bar!')`, it will always cause an alert pop up to be displayed to the user with the text 'foo bar!'.

## Defining and invoking functions

Let's define a function `alertHelloWorld` that displays a pop up alert saying "Hello world" to the user.

```javascript

function alertHelloWorld() {
  alert('Hello world');
}

alertHelloWorld();
```

The `function` keyword signifies that a function is about to be defined. Next comes the function name (in this case, "alertHelloWorld"), followed by its *call signature* `()`. *Call signature* refers to the arguments or parameters — if any — that get passed to a function. `alertHelloWorld` doesn't get any parameters (aka, arguments) passed to it, but we'll see an example of that in a moment. Between the `{ .. }` brackets comes the main block of the function. This is the behavior that will be carried out each time the function is run.

Note that we *call* or *invoke* the function by entering a line with the function name followed by the call signature (empty, in the case of `alertHelloWorld` above: `alertHelloWorld()`).

Also, note that *defining* a function and *calling*/*invoking* it are separate things, and when you define a function, the code isn't automatically run. You only run it by calling it as described above.

Here's an example of a function that takes one argument (`name`) in its call signature:

```javascript
function hello(name) {
  return 'Hello ' + name + '!';
}

console.log(hello('Thomas')); // => "Hello Thomas!"
```

This function abstracts out the name. We now can call it and pass in any value for `name`, and it will output a string that says "Hello " + the value of `name`.

This function has a *return statement*, as do many functions. A return statement causes a function to return the value to the right of the `return` keyword. We can assign values returned by a function to a variable (`const hiTom = hello("Thomas")`) or pass them as inputs to other function calls (`console.log(hello("Thomas"))`).

Note that functions that do not set an explicit return value via `return` still return something, namely, `undefined`:


```javascript
function noReturn() {
  // don't do anything
}

const foo = noReturn();

console.log(foo); // => undefined
```

Here's a function that takes two numbers and computes their average.

```javascript
function averageOfTwo(num1, num2) {
  return (num1 + num2) / 2;
}
```

Just like in `hello` above, inside the function body (that is, any code between the {...} brackets) we can access the variables passed in as num1 and num2 when the function is called. `averageOfTwo` expects to be called with two numbers but it can handle any combination of real numbers sent in when it's called. It first adds together the two numbers, then divides that value by 2 to get the average, which it returns.

If you're feeling a bit overwhelmed with all this new syntax, don't worry. For the moment, focus first on understanding the mental model for functions:

* a function is a block of instructions that you can call in your code
* some functions take arguments (or parameters), which are variables that the body of the function has access to
* some functions can *return* a value, which means that they output a value that can be assigned to a variable

## Working with Strings

```javascript
const myVar = 'this is a string';
```

A string is a collection of characters. In JavaScript, we can assign string values to variables by using either single or double quotes.

```javascript
const foo = "foo";
const bar = 'bar';
console.log(foo); // => foo
console.log(bar); // => bar
```

Either single or double quotes are fine. The key is that the outermost quote delimiters must both be either single or double.

Strings are used to represent text. It's [*basically* the case](http://stackoverflow.com/a/11141331) that any character from the [UTF-16](https://en.wikipedia.org/wiki/UTF-16) character encoding scheme can be represented in a JavaScript string.


## Concatenating Strings

JavaScript lets us use the `+` operator to *concatenate* — which just means "connect" — two strings into a bigger one.

```javascript
const innerText = 'The quick brown fox jumps over the lazy dog.'
const paragraph = '<p>' + innerText + '</p>';
console.log(paragraph) ;// => '<p>The quick brown fox jumps over the lazy dog.</p>'
```
## String methods

All strings in JavaScript share a number of built-in methods. Here are just a few:

```javascript
const fooBar = 'foo bar foo bar';
fooBar.length; // => 15
fooBar.charAt(0); // => "f"
fooBar.slice(4); // => "bar foo bar"
fooBar.slice(4, 7); // => "bar"
fooBar.split(" "); // => ["foo", "bar", "foo", "bar"]
fooBar.toUpperCase(); // => "FOO BAR FOO BAR"
fooBar.replace('foo', 'bar'); // => 'bar bar foo bar'
```

You can find the full list at [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#String_instances).

## Working with Numbers

In JavaScript, there's a single data type for representing integers (that is, whole numbers like -4, 0, 3, 1000, etc.) and floating point decimal numbers (like 3.234): `number`.

JavaScript can comfortably represent numbers ranging from (-2\*\*53, 2\*\*53), which is an acceptable level of precision for many applications.

Open the JavaScript console, and try inputting the following commands to get a feel of how numbers work in JavaScript:

```javascript
typeof 7 === "number"; // => true
let total = 1 + 2 + 3 + 4;
console.log(total); // => 10
total = total + 1;
console.log(total); // => 11
total += 3;
console.log(total); // => 14
total ++;
console.log(total); // => 15
console.log(3/10); // => 0.3
```

### Arithmetic operators

Numbers can be manipulated using the following *arithmetic* operators:

* `+` addition
* `-` subtraction
* `*` multiplication
* `/` division
* `**` exponentiation
* `%` remainder (also known as the "modulo" or "modulus" operator)

```javascript
5 + 5; // => 10

let foo = 2 + 2;
foo - 1; // => 3

let bar = foo * 2;
bar; // => 8

bar ** 2; // => 64
bar/3 // => 2.6666666666666665
bar/4; // => 2;

```

JavaScript also gives us a couple of shortcut functions for incrementing numbers:

```javascript
let counter = 0;
console.log(counter) // => 0
counter += 1;
console.log(counter) // => 1
counter += 9;
console.log(counter) // => 10
counter -= 1;
console.log(counter) // => 9
```

These compound operators allow us to change the value of a number variable in place — that is, we don't have to say `counter = counter + 1;`. Calling `counter ++` also increases the value of `counter` by 1.

### Comparing numbers

Numbers can be compared using the following operators:

* `<` less than
* `<=` less than or equal to
* `>` greater than
* `>=` greater than or equal to
* `===` equal
* `!==` not equal

Here are some examples of comparing numbers:

```javascript

let foo = 1;
let bar = 2;

foo < bar // => true
foo === 1 // => true
foo >= foo + bar // false
```

## Making Logical Assertions

An assertion is a statement that evaluates to either true or false — for example: `true === true` or `1 <= 5`.

Used in combination with `if` and `else`, logical assertions allow us to write conditional logic into our programs. We can tell our code to carry out one set of instructions if our assertion is true, and another if it is false.

## Logical Operators

Logical operators are used to make assertions about two or more statements or values. Let's start with `&&` (logical and), which is used to assert whether or not two statements are true. If you run `true && false` in a JavaScript console, you'll see that you get `false`. JavaScript checks to see if *both* expressions evaluate to true, and if so, it returns true. (Technically it returns the second value if the first one is true; this is sometimes useful, since other things count as false than just the boolean value.)

In the case of `true && false`, both values being compared are already Booleans, so no conversion takes place. Since one side of the `&&` is false, the whole assertion evaluates to false.

Logical operators can also be used with non-Boolean values like strings and numbers. For instance `true && "foo bar"` evaluates to `true` because JavaScript treats non empty string values as `true`.

In JavaScript we have three logical operators: `&&` (and), `||` (or), and `!` (not). `&&` evaluates to true if the values on both sides of the operator evaluate to true. `||` evaluates to true if one of the values evaluate to true. `!` negates a boolean value, so `!true` evaluates to `false` and `!false` evaluates to `true`.

```javascript
const foo = true;
const bar = false;
foo === bar; // => false
foo || bar; // => true
foo && bar; // => false
!foo; // => false
!bar; // => true
```

## Control Folow and Conditionals

Control flow dictates how programs execute different sets of instructions based on differing conditions. You might have one branch that executes if a condition is true, and another that executes if it's false. That's control flow, and it's a powerful tool.

## Conditionals `if`, `else`, `else if`

JavaScript gives us three keywords for working with conditionality: `if`, `else`, and `else if`. Let's start with an example of `if`:

```javascript

function sanityCheck() {
  if (true === true) {
    console.log("true is still true. that's reassuring");
  }
}

sanityCheck() // => "true is still true. that's reassuring"
```

To use a conditional, you begin with the command (`if` in this case), followed by an expression wrapped in parentheses `(true === true)`. Between the curly brackets (`{...}`) comes the statement(s) to be executed if the expression evaluates to true.

The same syntax is used for `else` and `else if`, but these both have the additional requirement that they must come after an adjacent `if` block.

```javascript
function analyzeNumber(num) {
  if (typeof num !== 'number') {
    console.log('not a number');
  }
  else if (num % 2 === 0) {
    console.log('even number');
  }
  else {
    console.log('odd number');
  }
}
```

## Object Basics

Objects are a *complex* data type that allow you to bring together common properties and behaviors into a single entity.  Objects provide an excellent way of organizing code that belongs together, help you avoid global variables, and let us represent individual instances of some model.

For instance, you can take the idea of a person and come up with a generalized model of that person’s attributes. A person has a name, and can say hello. Then we can have individual instances of that `person` model. We might have an individual person named "Sue" who greets others by saying "Howdy y'all", and another individual person named "Greta" who greets others by saying "Hi there".  All instances of a person share these traits (they have a name and can greet others).

Objects give us a way of representing instances of an idea or model, and because of that they're used all the time in programming. At the end of this course, in your capstone project, you'll create an app that retrieves data from a third party API and displays it to your user. In your JavaScript code, the results from the API will be represented as an array of objects.

In this lesson you'll learn the syntax for interacting with objects in JavaScript.

Objects are a data structure used to hold *key/value pairs*. If you've ever used a dictionary, you already have an intuitive sense of what a key/value pair is: you look up a word (aka, *key*), and you find its definition (aka, its *value*).

Here's an example of an object representing the classic rock band Led Zeppelin:

```javascript
const ledZeppelin = {
  singer: 'Robert Plant',
  guitar: 'Jimmy Page',
  bass: 'John Paul Jones',
  drums: 'Jon Bonham'
}
```


The curly bracket syntax above (`{}`) is one way we can create a new object. When you create an object like this, it's called an *object literal*. The keys in our `ledZeppelin` object are `singer`, `guitar`, `bass`, and `drums`. The values for these keys are 'Robert Plant', 'Jimmy Page', 'John Paul Jones', and 'Jon Bonham'. Each key is followed by a colon (`:`). Each key/value pair is separated by a comma (`,`).

Notice that the keys in the example above are not enclosed in quotation marks. This is the default way of indicating keys in an object literal, but there are times where you need to use quotation marks. For instance if you need a space or period in a key, you'd need to use quotation marks around the key:

```javascript
const ledZeppelin2 = {
  'lead singer': 'Robert Plant',
  'lead guitar': 'Jimmy Page',
}
```

Also, know that the keys in an object must all be *unique* -- that is, each key can be used only once in the object.

The values in an object can be any valid JavaScript data type. In the example above, all the values are strings, but values can also be numbers, booleans, other objects, `null`, or functions.

When an object has a value that is a function, we refer to that key/value pair as a `method`. Here's an example of an object representing a mammal, that features an `evolve` method.

<iframe src="https://repl.it/G9LN/3" width="100%" height="600px">

```javascript
const mammal = {
  numEyes: 2,
  warmBlooded: true,
  evolve: function() {
    console.log("I'm not mutating, I'm evolving.");
    mammal.numEyes ++;
  }
}

console.log(`mammal has ${mammal.numEyes} eyes`);
mammal.evolve();
console.log(`mammal has ${mammal.numEyes} eyes`);
```
</iframe>


### Getting values and running methods

Once the object is created, you can *get* values and run object methods in one of two ways: *dot notation* ( `ledZeppelin.singer`) or with *bracket notation* (`ledZeppelin2['lead singer']`). Using the example objects from above, both `ledZeppelin.singer` and `ledZeppelin2['lead singer']` would return the value 'Robert Plant'. Usually we use dot notation to get values from an object, but if you need to get a key with spaces or periods, you *must* use bracket notation.

The same syntax is used to run methods on an object. In the `mammal` example above, we use dot notation to call the `evolve` method.

Note that just like functions outside of objects, an object method can take arguments. Here's an example:

```javascript
const simpleCalculator = {
  add: function(a, b) {
    return a+b;
  }
};

simpleCalculator.add(1, 1); // => 2
```


### Adding key/value pairs to an object

Once an object is defined, you can add new key/value pairs to it using either dot or bracket notation. Here's an example:

```javascript
const myFamily = {
  lastName: 'Doe',
  mom: 'Cynthia',
  dad: 'Paul',
};

myFamily.sister = 'Lucinda';
myFamily['brother'] = 'Merle';
myFamily.sayHi = function() {
  console.log(`Hello from the ${myFamily.lastName}s`);
}
myFamily.sayHi() // => Hello from the Does
```


### Updating values

Updating values in objects is just like adding them.

```javascript
const foo = {
  bar: 'bizz'
};

foo.bar = 'bang';
```


### Deleting key/value pairs

To delete a key/value pair from an object, use the `delete` command:

```javascript
const foo = {
  bar: true
};
delete foo.bar;
console.log(foo.bar); // => undefined
```

# A Final (but very important) Note

The first, most important part of being a programmer, is thinking like one. There are two important steps to that. 
The first step is understanding the problem at hand. In order to solve a problem, you need to break it down. You will see in the next lessons that a webpage is built with pieces of code. All these pieces work together to solve a problem. When you first encounter a project, it's important to break it down into smaller problems. In doing this, you will be able to use the second important skill of a programmer: research.

A programmer is good at researching. Why? Because the tech world is ever changing, and you have to be able to keep up with it, including finding solutions to oddities that arise from those changes. Instead of memorizing everything, you will learn to research those things. If you follow step one, and break everything down into a small problem, then you can research that small problem. You will find as you continue along with this course, that you will have points that you encounter a large problem. If you break it down into small steps, you will be able to overcome each small hurdle with the knowledge you have.

If you have a question or can't solve a problem once you've broken it down, you're likely not the first person to have that question. When you get stuck, start Googling (or DuckDuckGo-ing, though that's a lot harder to say). Far from 'cheating,' any experienced programmer will tell you they do this regularly. There are a few tricks that will help you optimize your Google searches. [This infographic](https://d3rgj9au57pk8c.cloudfront.net/uploaded/attachments/11080.gif?v=21fa9b) has some great tips, and your mentor is sure to have more. Before asking your mentor or Slack, try searching on your own for about 30 minutes. 

Make sure you use these tactics in particular:
- If you get an error message, copy and paste the exact message into Google. Try it with quotes for an exact match, and if that doesn't yield results, try it without quotes. 
- Make sure your search is precise. Searching "webpage background colors" won't get you what you want, but "HTML CSS background color" will return something useful. Include the language and/or framework you're working with and the end goal, the thing you're trying to accomplish by the end of this search. Also use as few "keywords" as possible.
- Don't just follow the first set of answers you find. Evaluate the website. Is it reputable? Are other people up-voting or agreeing with the solution? If you're not sure that you've found a good resource ask the student community what they think.

Most searches will take you to an answer on [Stack Overflow](http://stackoverflow.com/), a powerful community for learners, and a place you'll soon know well. If you'd like to ask questions on Stack Overflow, [use their guide](http://stackoverflow.com/help/how-to-ask) to make sure you phrase your questions well. You may have heard that Stack Overflow has a reputation of being harsh on new members. The biggest reason for that is asking a duplicate question, and not asking a "good" question. You can avoid this harsh reaction by making sure that your question is indeed a new one, and following the guidelines for a good question.

# Building the Virtual Pet Project

You'll be building your projects in Glitch. Glitch allows you to write code in your browser and instantly see (and keep) the live version of your site. [Here's the link](https://glitch.com/edit/#!/spotless-chemistry?path=README.md:1:0) to start building your virtual pet projects. 

When you run into issues, make sure to raise your hand and ask your junior mentor for assistance.
