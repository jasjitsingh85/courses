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


# CSS Review
CSS (Cascading Style Sheets) is the language used to control the *presentation layer*. Whereas HTML is about structure and content (aka, the "content layer"), CSS is about style and appearance. We use it to control the visual aspects of the content on a page: from fonts to color to size to animations and more.

The key vocabulary words for CSS are: *ruleset*, *selector*, *declaration block*, *declarations*, *property*, and *value*.

```css
input {
  display: block;
  font-family: 'Proxima Nova W01', sans-serif;
  font-weight: 400;
  font-style: normal;
  height: 45px;
  width: 420px;
  min-width: 210px;
  max-width: 100%;
  padding: 6px 1em 5px;
  border: 1px solid #d0d2d5;
  border-radius: 3px;
  font-size: 15px;
  line-height: 30px;
  color: #404853;
  box-shadow: inset 0 3px 7px #f6f7f7;
}
```

This snippet is from a page on Thinkful's website. It is a *ruleset* that describes how input elements should look. It consists of a *selector* (`input`, in this case), which is the element or elements that will be targeted by the declarations that follow.

The *declaration block* follows the selector. A declaration block is a set of *declarations* contained in curly brackets (`{`, `}`). Within the block, each line is a separate declaration.

A *declaration* consists of a *property* and the value it is to be set to (for instance, `box-shadow: inset 0 3px 7px #f6f7f7;`, above). 

Each property has a range of valid values (for instance, width could be set in terms of pixels or percentage, among other options, but setting width to "foo" would not be valid).

```css
/*invalid*/
.foo {
  width: 'foo';
}

/* valid */
.foo {
  width: 100px;
}

.bar {
  width: 50%;
}
```

The property name is followed by a colon, and the value is followed by a semicolon.

In the first line of the snippet above (`/*invalid*/`), notice that we've used a code comment. As with HTML, you can use comments in CSS to document your code or temporarily disable (*comment out*) a block of code.

With real web pages, the final presentation of a given element will usually be the result of several rulesets interacting. We'll learn more about this in a moment when we discuss *CSS specificity*, but for the moment, know that this:

```css
p {
 font-family: Arial;
}

p {
  font-size: 20px;
}
```

is valid (though not the most concise) CSS. In practice though, the computed CSS that gets applied to an element by the browser is often the result of a set of rulesets, possibly spanning more than one stylesheet.


### CSS Selectors

CSS provides a rich set of selectors that give you precise control over the elements targeted by a declaration block. Later in this lesson, you'll complete drills on CSS selectors to build up your working knowledge of the most commonly used selectors.

The following examples will give you a sense of some of the ways you can target elements for style rules:

```css
/* universal selector (applies to everything) */
* {
  /* set stuff */
}

/* targeting a single element type */
p {
  /* set stuff */
}

/* targeting two different elements */
p, input {
  /* set stuff */
}

/* targeting a class */
.foo {
  /* set stuff */
}

/* targeting an id */
/* avoid these, but know how to recognize
  them in the wild. It's usually better to
  use a class selector instead.
*/
#bar {
  /* set stuff */
}

/* targeting an element with a class */
/* try to avoid this, in favor of simple class declaration */
p.foo {
  /* set stuff */
}

/* targeting descendants */
ul.foo li {
  /* any `li` within `ul.foo` will get targeted */
}

/* targeting direct children */
ul > li  {
  /*  only `li`s that are direct children of ul targeted */
}

/* targeting submit buttons */
button[type="submit"] {
  /* any button with a type of "submit" */
}
```

# jQuery Basics

To create an interactive web app, we need a way to programatically alter the HTML that's displayed to users when certain events occur. For instance, we might want to display validation errors in a form or load additional articles to display as a user scrolls down in a result list.

### The DOM

The [DOM, or document object model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction), is the browser's representation of the current state of the HTML content of a page. The DOM is not to be confused with the HTML file for a page. When the browser first loads an HTML page, the DOM will look a lot like the HTML source code, but as JavaScript scripts begin to take over, HTML elements can be added and removed, regardless of whether or not they appeared in the HTML file.

You might not have realized it, but you worked with the DOM earlier in this curriculum. When you view HTML in the elements panel of Chrome Developer Tools, you are looking at a representation of the DOM.


### DOM Traversal and Manipulation

We'll be using jQuery to find particular elements in the DOM (which is called *traversing*) and update them (which is called *manipulating*). DOM traversal and manipulation can be done using plain JavaScript, but because of cross-browser compatibility issues, many developers prefer to use jQuery's API for DOM traversal and manipulation.

In jQuery, to select elements in the DOM, you use the same CSS selectors you learned about in *Introduction to Web Development. For instance, `var paragraphElements = $('p')` would give you access to all paragraph elements in the DOM. The `$` in that snippet is the jQuery object, which has methods for DOM manipulation and traversal, as well as AJAX requests (which we'll cover later), and JavaScript animations (which we will not cover).

Let's look at a simple hello world app to see the idea of traversal and manipulation in action. In the JavaScript code below, we traverse the DOM to find all elements with the `.js-hello-world` class, and we then manipulate those elements so their inner text says "Hello js world".

<iframe frameborder="0" height='500px' width="100%" src='https://repl.it/GhE1/9'></iframe>

Although the end user never sees it, when the HTML first loads the page initially loads with an h1 element that says "Hello from original HTML". Looking at the HTML file, we can see that initially the unordered list has a single empty list item in it.

Looking at the output panel, in the end result we see the text "hello world from js" in two places.

Looking at the JavaScript code, in `doHelloWorld`, we first find all elements in the DOM that have the '.js-hide-it' class on them, and using jQuery's [addClass method](https://api.jquery.com/addclass/), we add the '.hidden' class to all matching elements. In that line, we have both *traversal* and *manipulation*. We traverse the DOM to find elements with the '.js-hide-it' class and we manipulate them by adding the '.hidden' class to them.

In the next line, we find elements with the '.js-hello-world' class, and using jQuery's [text method](http://api.jquery.com/text/), we change the inner text of matching elements to be "hello world from js". Again, we have two steps, traversing and manipulating.

Note the deliberate prefixing of 'js-' on the class names our JavaScript code targets. Any time you add class names that are there not for styling purposes but as a target for DOM manipulation, it's best practice to let the class name reflect this. You don't want your JavaScript layer to be dependent on the same class names being used for styling purposes, because those might change, and your JavaScript code should continue to work even when styles change.

Finally, note the order of our `<script>` tags in `index.html`. First we include the jQuery library, and then we link to `index.js`. Recall that the browser reads our HTML file top to bottom, so if you have an `index.js` file that depends on jQuery, that `index.js` file needs to come after jQuery.


### Traversal and Manipulation Methods

When you use the `$()` jQuery method to target a set of elements, the object you get back is a jQuery object, and it has [numerous traversal methods](https://api.jquery.com/category/traversing/) that you can use to traverse the selected element(s).

The following example demonstrates two commonly used jQuery traversal methods: [.find()](https://api.jquery.com/find/) and [.parent()](https://api.jquery.com/parent/). `.find()` is used to traverse the elements contained in a jQuery selection, using a filter condition. `.parent()` is used to target the first parent element of a jQuery object that passes a filter condition.

<iframe frameborder="0" height='500px' width="100%" src='https://repl.it/GhE9/12'></iframe>

In the initial HTML for this example, we've applied a hidden class to the div element containing a to do list, making it invisible. Note that one of the list items has the class `.js-complete`.

When our JavaScript code runs, it targets elements with the `.js-to-dos` class. We call `.parent()` on the resulting jQuery object to find the first parent with the class `.js-parent-demo`, and we remove the `.hidden` class from that element. We use the `.find()` traversal method to target children of the `.js-to-dos` jQuery object that have the class `.js-complete`, and add the `.complete` CSS class to those elements in order to get the strikethrough text effect.

There are several other useful jQuery [traversal](https://api.jquery.com/category/traversing/) and [manipulation methods](https://api.jquery.com/category/manipulation/). We will not cover these methods here, but you should spend a half hour or so reviewing what's available.

# jQuery Events

In the previous assignment, you learned how to traverse and manipulate the DOM, but that ability alone is not very valuable. In order to take advantage of DOM manipulation, you need to be able to alter the DOM when [events](https://developer.mozilla.org/en-US/docs/Web/Events
) happen.

jQuery provides a streamlined, cross-browser compatible [interface for setting up event listeners](https://learn.jquery.com/events/event-basics/), and this assignment will teach you what you need to know to use it.

An event listener consists of two parts. First you have to specify which event to listen for. Second, you have to provide a *callback function* that runs whenever the event occurs. Let's look at some examples.

### Basic event handling

This app listens for when users click the "Click me" button, and responds by updating the DOM with the number of times the button has been clicked:

<iframe frameborder="0" height='500px' width="100%" src='https://repl.it/GlVR/5'></iframe>

To implement this behavior, we use two event listeners. The first event we need to know about is when the page is fully loaded. At the bottom of the JavaScript file, we call jQuery (`$()`), passing in a callback function that we want to run when the page loads:

```javascript
$(handleClicks);
```

When the browser finishes loading the DOM for a page, it emits a "ready" event. This event happens once per page load. jQuery will run the callback function we pass to `$()` after this ready event happens. You should start using the `$(callbackFn)` function to activate your application.

Be aware that in addition to the `$(callbackFn)` syntax for document ready events, earlier versions of (jQuery < 3.0) used the built-in [`.ready()` method](https://api.jquery.com/ready/). `.ready` has been deprecated (programmer talk for 'no longer preferred, but still allowed'), and you shouldn't use it in your own code, but you should understand that it does the same thing as `$(callbackFn)`, as you're likely to encounter legacy code with the older syntax.

We pass `handleClicks` as our callback function to run when the DOM has loaded. At the top of `handleClicks`, we create a variable to track the number of times the user has clicked the button.

Next we traverse the DOM to find any elements with the `.js-click-counter` class, and set the text on those elements to the current value of click count.

After that we have our second event listener. Any time an element with the `.js-clicker` class on it gets clicked, we increment our `clickCount` variable, then update the `.js-click-counter` elements with the new value.

### Event objects

Let's imagine that you are using jQuery to make a puzzle game. When the player presses the "w" key, you want their character to move forwards. When they press "a" and "d" you want them to move left and right. And when the player right-clicks on an item you want to open up a menu letting them interact with the item. So far you have learned how to call a function when the user presses a key, or clicks on a DOM element. But how would you work out whether the "a" or "d" key was pressed, or whether the left or right button was clicked?

The solution is to use the DOM event objects. The callback functions in your event listeners always get access to an object representing the instance of the event. This contains information about where you typed in the text, what keys you pressed or which buttons were clicked. In fact, just about every piece of information you could ever want to know about *how* you performed an action is contained within the event object.

<iframe frameborder="0" height='500px' width="100%" src='https://repl.it/GhEp/6'></iframe>

In the repl.it above, try typing in the text box and left and right-clicking the button. You should see the output `<div>` being filled with information about the action you performed. If you left-click it will tell you that button 1 was clicked, and if you right-click it will tell you that button 3 was clicked. And if you type some text it will tell you which keys were pressed.

Let's look at the JavaScript for the repl.it:

```js
$(function() {
  $('button').mousedown(event =>
    $('.output').text(`Button clicked: ${event.which}`)
  );

  $('input').keydown(event =>
    $('.output').text(`Key pressed: ${event.key}`)
  );
});
```

This code tells the browser to wait until the page loads, then listen for when a user clicks on any `button` element or presses a key in any `input` element. When one of those happens, you run a callback function (i.e., the blocks of behaviors we define below). When the user clicks or types a key, the browser generates some data about the click event. The object representing that data is the `event` you see in `function(event)`.

### `event.currentTarget`

One of the most powerful properties of an `event` object is the `currentTarget`. This contains information about which DOM element the user has interacted with.

<iframe frameborder="0" height='500px' width="100%" src='https://repl.it/GiO6/15'></iframe>

In the repl.it above, try clicking on the green section, then each of the red-bordered rectangles. The text inside of the clicked element gets displayed in the top section. In non-technical language, when you click on one of these sections, it's as though the blue section at the top says "Hey which section was it that got clicked? And what's the text in that section?" and the clicked section responds "My internal text is 'fee'" (or whatever its internal text happens to be).

Here's the JavaScript for the repl.it:

```javascript
$(function() {
  $(".foo, p, ul, li").click(function(event) {
    event.stopPropagation();
    $("h2").text(`event.currentTarget's text is: ${$(event.currentTarget).text()}`);
  });
});
```

This code tells the browser to wait until the page loads, then listen for the user clicking any element matched by the selectors `.foo, p, ul, li`. When one of those is clicked, a function is run (with an event object provided).

We'll circle back to `event.stopPropagation()` in a moment. First let's see how `event.currentTarget` works. In the line `$("h2").text(...`, we're telling the browser to find an h2 element and set its text content to be "event.currentTarget's text is:" plus whatever `$(event.currentTarget).text()` computes to. From observing the behavior of the repl.it, you already have a sense of what's going on here: `event.currentTarget` refers to the element being clicked, and we retrieve the text of the currently clicked element.

Why then do we need to do `$(event.currentTarget).text()` and not just `event.currentTarget.text()`? What's the jQuery dollar sign doing? Recall that jQuery is a JavaScript library that makes it much easier to make our pages interactive. `.text()` is a method from the jQuery library. In order to use the methods from jQuery, you first need to select something to act upon, using the selector (`$(event.currentTarget)`). The browser will find that element, and then pass it to the method you want to use. In JavaScript, `event.currentTarget` refers to the element, as discussed above, but jQuery selectors actually have different methods and data than a non-jQuery selected element. Because of that, we need to turn `event.currentTarget` into a jQuery object, so the library code can add the extra methods (including `.text()`).

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
