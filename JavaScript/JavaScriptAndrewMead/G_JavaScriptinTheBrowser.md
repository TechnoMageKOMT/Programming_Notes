# JavaScript In The Browser

## DOM Manipulation

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

## User interaction

Additional option for selecting a specific target when there is more than one that fits the selector. Using querySelectorAll together with bracket notation for the array that is returned.

```JavaScript
document.querySelector('button')[1].addEventListener('click', function(){
  //some code 
})
```

This method is not recommended because it lacks specificity. 

Ways of targeting elements

--Single--  
`p` - By HTML tag  
`#id` - By id  
`.class` - By class  
--Multiple--  
`p#id` - Element that has both  
`button.inventory` - Element that has both  
`h1#title.application`- Element that has all three  

## Text Input Fields

### change Event type

```JavaScript
document.querySelector('#search-text').addEventListener('change', function(e){
  console.log(e.target.value)
})
```

This code will produce the text that the user entered into a text input field, but only when focus on the input field is left. I.e., when clicking outside the field.

### input Event type

The alternative to `change` is `input`. The syntax is the same, but the input values are received in real time, character by character as the user types in the field.

## Rendering Filtered Data 

**VERY NB For real world applications**
**This will be used a lot in real life***

This is to filtered arrays of data. The data would normally be individual objects in the array.

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

## Working with forms. 

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

