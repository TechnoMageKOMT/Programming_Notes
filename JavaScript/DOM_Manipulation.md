# The Complete 2021 Web Development Bootcamp - Dr Angela Yu

## JavaScript Notes

## Manipulating the DOM - General Introduction

```JavaScript
document.firstElementChild; => html
```

```JavaScript
document.firstElementChild.firstEelement.Child; => head
```

```JavaScript
document.firstElemenetChild.lastElemenetChild; => body
```

```JavaScript
document.firstElementChild.lastElemenetChild.firstElemenetChild; => h1
```

Use case example:

```JavaScript
  let heading = document.firstElementChild.lastElemenetChild.firstElemenetChild;
  heading.innerHTML = "Good Bye:;
  heading.style.color = "red";
```

`document.querySelector()` is another way of selecting elements:

```JavaScript
  document.querySelector('input').click();
```

This statement will mark the corresponding checkbox as "clicked". I.e.,simulating a user click.

Also note the use of dot notation when manipulating the DOM.

`object.property;` is called a "getter" (Get property).
`object.property = x;` is called a "setter (Setting a property)
`object.method();` is called "calling a method

Example of properties:

- innerHTML
- style
- firstChild

Examples of methods

- click()
- appendChild()
- setAttribute()

```JavaScript
  let example = document.querySelectorAll('li')
  example[2].innerText = "Johann";
  example[2].style.color = "blue";
```

`document.getElementsByTagName('');` Would return an array if there are multiple items with the same tag.

```JavaScript
document.getElementsByTagName('li')[2].style.color = "purple";
document.getElementsByTagName('li').length //Length of the array
```

`document.getElementByClassName('');` Also returns an array even if there is only one item in the array (I.e., when there is only one element with that class name)
so,

```JavaScript
document.getElementByClassName('btn')[0].innerText;
```

`document.getElementById('');` Much more specific

`document.querySelector('');` # and . to be included for classes and ids. NB if multiple items with same class or id, only the first will be selected. Call also use hierarchical selector just as is done in CSS

```JavaScript
document.querySelector('li a'); or
document.querySelector('li.item') i.e., tag.class
```

`document.querySelectorAll('');` produces a node list which is for all itents and purposes an array.

**querySelector and querySelectorAll allows for more complex selections.**

The other methods are more broad in scope and it is very difficult to target a specific element without going in and changing the HTML. Predominant is querySelector options followed by getElement options (Ref: Jonas getElement method is faster for very big applications).

## Manipulating and changing styles of HTML Elements and JavaScript

Refer to MDN "HTML DOM Style Object" documentation for CSS property name equivalents in JavaScript. Property name written with dash connectors is just written in camelCase in JavaScript. E.g., background-color becomes backgroundColor.

When setting new values for styling properties, the values are always set as strings. I.e., in quotation marks. This is the case even when the value is a number.

**Take careful note of the selectors in the previous section where arrays or objects are returned**
Using these selectors does not work unless the index number is included using bracket notation:

```JavaScript
document.getElementsByTagName("h1")[0].style.color = "red";
```

The selector returned an array even though there is only one `<h1>` element.

Refer: To wriiten notes from Jonas Schmedtmann's course where this was already covered.

## The seperation of concerns: Structure vs Style vs Behaviour

This basically means that a seperation is maintained between the three to keep code tidy and easy to debug.

- HTML: Content
- CSS: Style
- JavaScript: Behaviour  

The **classlist** is a property of every DOM object which keeps track of the list of classes that an object has. This can be manimpulated by methods such as
add(): To add a class
remove(): to remove a class
contains(): to check if a class is present
toggle():to add if class is absent and to remove if present.

```JavaScript
document.querySelector('.btn').classList.add('invisible');
```

This line of code will add the class 'invinsible' to the object wuth the class .btn. Using this together with styling for the new class in CSS means that the button in this case can be manipulated to appear and disappear by JavaScript

```CSS
.invinsible {
  visibility: hidden
}
```

**NB** Because we are dealing with the classList, the dot precursors for classes is not needed. Just the name of the class is entered.

## Text manipulation and the text content Property

innerHTML: Returns the content between the element's tags including children within that tag, but as the 'raw' html code.
innerText: **Do not use: Refer to MDN documentation**
textContent: Returns the text content between the specified elements tags including text within child elements.

innerHTML and textContent can be used to change their values 'on the fly'

```JavaScript
document.querySelector('h1').textContent = "Some new content.";
document.querySelector('h1').innerHTML = "<em>Some new text</em>";
```

## Mnaipulating HTML attributes

Any elements attributes can be accessed as follow:  

```JavaScript
document.querySelector('.item a').attributes;
```

This will produce a list of all the attributes of the selected element.

To access the value of a specific attribute

```JavaScript
document.querySelector('.item a').getAttribute('href');
```

To change an attribute:

```JavaScript
document.querySelector('.item a').setAttribute('href','https://www.bing.com');
```

Note that this method has two parameters so two arguments are needed. The first is the attribute name and the second is the new value.

## Drumkit Project

## Adding event listeners

Functions within the addEventListener method does not have () because they are only called by the method if the event takes place.

Generic syntax:

```JavaScript
target.AddEventListener(type, event-handler-function);
```

Two ways:
Anonymous function:

```JavaScript
target.addEventListener('click', function(){
  //some action;
})
```

Named function:

```JavaScript
target.addEventListener('click', respondToClick);

function respondToClick(){
  //some action;
}
```

Higher order functions = Functions that can takes as input another function. This is very common to the way that JS manipulates the DOM.

### Constructor Functions

These function are used to create objects:

```JavaScript
function SomeName(var1, var2, var3, var4){
  this.var1 = var1;
  this.var2 = var2;
  this.var3 = var3;
  this.var4 = var4;
  this.someFunction = function(){
    //statement / expression
  }
}

const objectName = new SomeName(value1, value2, value3, value4);
```

Take note of the `new` keyword that must precede the name of the constructor when invoked. Another difference is that the function name starts with a capital, unlike normal functions.

To call the method in this object:

```JavaScript
SomeName.someFunction();
```

Constructor functions are what is behind JS's methods. Refer to drumkit project:

```JavaScript
let crash = new Audio("sounds/crash.mp3");
crash.play();
```

This is clearly a new object that is being created by the Audio constructor function that has a function called play within it which is invoked in the second line.