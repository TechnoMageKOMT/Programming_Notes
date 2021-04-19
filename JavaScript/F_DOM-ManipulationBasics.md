# Manipulating the DOM - General Introduction

## DOM - Document Object Model

Document Object Model (DOM) is a platform and language-neutral interface that allows programs and scripts to dynamically access and update the content, structure, and style of an HTML document. It can simply be understood as a tree of nodes created by the browser.

Each HTML element and unit of content is a DOM object or a **node** in the DOM tree that JavaScript interact with. Each of these nodes has its own properties and methods which can be accessed by JavaScript. At the top of the structure is the `document` object which is the entry point for JavaScript into the DOM. Everything in the DOM is a node object.

**NB** The DOM is not JavaScript. The DOM and DOM methods are parts of web APIs which JavaScript can interact with. These APIs (Application Programming Interfaces) are libraries that are written in JavaScript that is used during the DOM manipulation.

**Aside** Curiously the "href" aatribute and text content of an `<a></a>` tag are children of the tag! This is an example of the statement above "Everything in the DOM is a node object".

## Selecting Elements and accessing properties

Selecting the entire HTML document:

```JavaScript
document.firstElementChild;

```

Then the head section:

```JavaScript
document.firstElementChild.firstEelement.Child; => head
```

or the body section:

```JavaScript
document.firstElemenetChild.lastElemenetChild; => body
```

An h1 element if that was the first child of the body section: 

```JavaScript
document.firstElementChild.lastElemenetChild.firstElemenetChild; => h1
```

Use case example:

```JavaScript
  let heading = document.firstElementChild.lastElemenetChild.firstElemenetChild;
  heading.innerHTML = "Good Bye:;
  heading.style.color = "red";
```

The full list of these relationship-to-node selectors are:

- .parentNode
- .childrenNodes
- .firstElementChild
- .lastElementChild
- .nextElementSibling
- .previousElementSibling

`document.querySelector('*')` is another way of selecting elements. * is the selector as it is used in CSS. I.e., if it is a class or id, then a . or # precedes it.

```JavaScript
  document.querySelector('input').click();
```

This statement will mark the corresponding checkbox as "clicked". I.e.,simulating a user click.

Also note the use of dot notation when manipulating the DOM. **DOT assosciativity** Left to right, so the element is first "retrieved" and then the property is extracted by the dot operator.

`object.property;` is called a "getter" (Get property).
`object.property = x;` is called a "setter (Setting a property)
`object.method();` is called "calling a method

Example of properties:

- innerHTML
- textContent
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

`document.getElementById('');` Much more specific and faster when working on very large and complex projects.

`document.querySelector('');` # and . to be included for classes and ids. NB if multiple items with same class or id, only the first will be selected. Call also use hierarchical selector just as is done in CSS

```JavaScript
document.querySelector('li a'); or
document.querySelector('li.item') i.e., tag.class
```

`document.querySelectorAll('');` produces a node list which is for all intents and purposes an array which can and is iterated through.

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

## Manipulating CSS style directly with JavaScript and the DOM

```JavaScript
const someVariable = document.querySelector('someSelector')
someVariable.style.someProperty = 'newValue'
```

Hyphenated CSS property names are substituted with camelCase names. **NB** The newValue must be passed in as a string with the unit included. I.e., between ' '.

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

## Changes in the DOM

**Good practive**: If variables are manipulated and changed in the DOM by a JavaScript application, the variables should be stored in the JavaSCript code. These are called state variables. In practice, "fetch" the required elements and assign them to variables in the JavaScript code. From there onwards the JavaSCript variables are referenced not the selection string.

It is a good idea to "fetch" these elements at the beginning of the JavaScript file.

## Adding event listeners

For code to react to something that happens in the DOM an event listener is needed.

The addEventListener() method has two parameters and takes in a "type" argument (eg., 'click', 'keydown' etc.) and a "listener" which is usually a JavaScript function. This function will determine what dynamic action is taken when the "type" of event is detected. When calling a function here there is no set of () unless an anonymous function is used. The reason for this is that the function is not called until the event type is detected. Until then it "lies dormant". If the () were present and there is an explicit named function, the function will be called everytime the line of code is read by the browser and the action will be carried out irrespective of the presence of the event. Without (), the function will only be called when the event is detected. This does not apply to aunonymous functions.

An anonymous function is simply the RHS of a function expression (i.e., without the assignment and name).

This is a central feature of JS programming. The idea that a function is passed as an input into another function so that it can be called at a later time.  

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

### Higher order functions

Functions that can take as input another function. This is very common to the way that JS manipulates the DOM.

```JavaScript
element.addEventListener('click', function(){
  console.log('I got clicked!');
} )
```

Could also be coded as:

```JavaScript
element.addEventListener('click', respondToClick);

function respondToClick(){
  console.log('I got clicked!);
}
```

The addEventListener() method(function) is in this second case a higher order function and representative of all higher order function. The only variation to this is the level of complication. 

### `this`

`this` in an object context belongs and points to the object that called it. In this case during the iteration through the buttons in the initial for loop, this points to each html button element as the loop iterates. `this` Can therefore be used interchangeably with that element in the code.

```JavaScript
for (let i = 0; i < numberOfDrumButtons; i++){
  document.querySelectorAll('.drum')[i].addEventListener('click', function(){

    console.log(this);

  })
}
```

The output for each iteration here will be the html element. E.g.,:

`<button class="s drum">`

As each button is clicked `this` will point to that HTML object / element. Any of the properties of `this` object can be utilised and referenced in this way. E.g., `this.innerHTML` or `this.style.color = "white"`.





### Understanding Callbacks and How To Respond To Events

```JavaScript
document.addEventListener('keydown', respondToKey(event));

function respondtoKey(event){
  console.log('Key pressed.');
```

In this example the function that is passed into the addEventListener() method is referred to as a callback function, because it alows a waiting period for something else to finish happening ( a key press in this case). When the keypress event has taken place, the callback function will be called and it can in this case supply us with information only known after the event. During this process the callback function also passes through information about the event that actually triggered the callback function to be called.

The callback function is called by the object that experienced the event that was needed for the function to be called.

When an event occurs an object is created within the addEventListener() method and information about that event is stored in the object.

## Removing Elements 

```JavaScript
const p = document.querySelector('p');
p.remove()
```

The remove() method with no specified arguments removes the entire targeted 'p' element from the DOM.

The rest of the material was revision of already covered material in other courses.

## Adding Elements Via The Dom

Three steps

- Create the new element
- Update it's content
- Insert the element

Example:

```JavaScript
const newParagraph = document.createElement('p');
newParagraph.textContent = `This is a new element from JavaScript`;
document.querySelector('body').appendChild(newParagraph);
```

This code would insert the new paragraph element at the end of the body section of the DOM (I.e., as last child).

## Advanced Selectors

Additional option for selecting a specific target when there is more than one that fits the selector. Using querySelectorAll together with bracket notation for the array that is returned.

Ways of targeting elements

--Single--  
`p` - By HTML tag  
`#id` - By id  
`.class` - By class  
--Multiple--  
`p#id` - Element that has both  
`button.inventory` - Element that has both  
`h1#title.application`- Element that has all three  

## Keyboard / Keypress Events

Requires the addEventListener() method just like mouse clicks.

Keyboard events are global events because they're not usually associated with specific elements (exception text input fields).

Three types: 

- keydown **Most commonly used**
- keypress
- keyup

Generic syntax:

```JavaScript
document.addEventListener('keydown', function(e){
  //code block
})
```
`e` Is used by convention and stands for event. When a key is pressed an object is generated which contains all the information about that event. By passing this object as an argument to the event handler function, it can access specific key:value pairs within the object. One of the properties or keys of this object is `key` where the actual key's identity that was pressed is stored.

```JavaScript
document.addEventListener('keydown', function(e){
  console.log(e)
})
```

Will output the object to the console. This output can be used to verify that the identity of the actual key that was pressed, is stored under the property `key`.

```JavaScript
document.addEventListener('keydown', function(e){
  console.log(e.key)
})
```

Will output the identity of the key to the console. 

The `e.key` value can be used anywhere that expressions are accepted. For instance, conditional statements.


```JavaScript
document.addEventListener('keydown', function(e){
  if (e.key === 'Escape') {
    //code block
  }
})
```

## Text Input Fields

### change Event type

```JavaScript
document.querySelector('#search-text').addEventListener('change', function(e){
  console.log(e.target.value)
})
```

This code will produce the text that the user entered into a text input field, but only when focus on the input field is left. I.e., when clicking outside the field.

### input Event type

The alternative to `change` is `input`. The syntax is the same, but the input values are received in real time, character by character as the user types in the field. This method is preferred when filetering data on the fly.

### Rendering Filtered Data 

**VERY NB For real world applications**
**This will be used a lot in real life***

This is to filter arrays of data. The data would normally be individual objects in the array.

Let `notes` be the array with properties `title` and `body`. We want to filter the data based on text values entered into a input field with the id of `search-text` 

Step 1  

Set up a filters object to store the latest filters. The initial object only has one property with an empty value.

```JavaScript
const filters = {
  searchText: '',
}
```
Step 2.1  

Setup first half of a rendering function. This part is to filter the list by `title` and the `searchText` value in the `filters` object.

```JavaScript
const renderNotes = function (notes, filters) {
  const filteredNotes = notes.filter(function(){
    return note.title.toLowerCase().includes(filters.searcText,toLowerCase());
  });
};
```

Step 2.2  

Remove all previously rendered notes by targeting a div with id `notes` that was created for all rendered notes.

```JavaScript
const renderNotes = function (notes, filters) {
  const filteredNotes = notes.filter(function(){
    return note.title.toLowerCase().includes(filters.searcText,toLowerCase());
  });

  document.querySelector('#notes').innerHTML = '';
};
```

Step 2.3  

The third part of the function is to render the filtered notes

```JavaScript
const renderNotes = function (notes, filters) {
  const filteredNotes = notes.filter(function(){
    return note.title.toLowerCase().includes(filters.searcText,toLowerCase());
  });

  document.querySelector('#notes').innerHTML = '';

  filteredNotes.forEach(function(note){
    const noteElement = document.createElement('p');
    noreElement.textContent = note.title;
    document.querySelector('#notes').appendChild(noteElement)
  });
};
```

Step 2.4  

Respond to input from the user and calling the renderNotes function  

```JavaScript
documnet.querySelector('#search-text').addEventListener('input', function(e){
  filters.searchText = e.target.value;
  renderNotes(notes, filters);
});
```

### Working with forms. 

The 'submit' type event listener is used for form elements. This will trigger on clicking a button or pressing enter after entering the input.

Within the callback function of the event listener the method `e.preventDefault` will be invoked to prevent the browser's default handling of forms. (This is analogous to telling the browser that the request will be handled by ourselves).

To access the values within the event handler function:

```JavaScript
e.target.elements.variableName.value
```

`variableName` is the name that was entered as the value of the name attribute of the input element in HTML.

Once a field has been entered the value on the HTML page can be wiped away by

```JavaScript
e.target.elements.variableName.value = '';
```

Exampes: `newTodo` is the value attributed to the name attribute of the input element. `todos` Is an array of todo objects each composed of a `text` and `completed` property.

```JavaScript
document.querySelector('#todo-form).addEventListener('submit', function(e){
  e.preventDefault();
  const newTodo = e.target.elements.newTodo.value;
  todos.push({
    text: newTodo,
    completed: false
    });
  renderTodos(todos, filters);  //Similar to the renderNotes example above
  e.target.elements.newTodod.value = '';
})
```

### Checkboxes

The event listerner type to use with checkboxes is `'change'`. The event will fire as soon as the checkbox is checked or unchecked.

To access the **boolean** value:

```JavaScript
e.target.checked
```

### Select Dropdowns

In HTML these are added with the `<select></select>` element and options are added within it via the `<option>` tag. An id is allocated to the `<select>` element which is targeted. **Do not** enter a name attribute, not even a blank one. This will result in a value that is an empty string. Simply enter the options between the `<option></option>` tags. If it is necessary to use more user friendly value when manipulating in JavaScript the `value` attribute can be set with camel case variable type name to be used in JS.

The `'change'` type event listener is used just as in checkboxes.

The value is accessed by 

```JavaScript
e.target.value
```
