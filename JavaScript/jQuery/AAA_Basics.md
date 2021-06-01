# jQuery Introduction and Basics

## What is jQuery

jQuery is a JavaScript library designed to simplify HTML DOM tree traversal and manipulation, as well as event handling, CSS animation, and Ajax. It is free, open-source software using the permissive MIT License. As of May 2019, jQuery is used by 73% of the 10 million most popular websites. Web analysis indicates that it is the most widely deployed JavaScript library by a large margin, having at least 3 to 4 times more usage than any other JavaScript library. - Wikipedia

## Other JavaScript libraries

- jQuery UI
- MooTools
- Underscore.js
- Dojo Toolkit (more suitable for advanced developers)

There are many more and each library usually focusses on specialised aspects of web development.

## Where to get the latest version of jQuery

[https://jquery.com]

Main options:

- Download the files locally (uncompressed recommended during development and compressed during production)
- Use with a CDN (recommended for speed when deploying website)

## Checking if the jQuery script is linked and working

```JavaScript
console.log($)
Output: function S(e, t)
```

## Document ready event

This code is always used to wrap the jQuery code to ensure that the code is only excecuted after HTML page is fully loaded with all relevant scripts and stylesheets.  

```JavaScript
$(document).ready(function() {

})
```

## Selecting

### Selecting elements by tag

`$('tag name').`  

or if more than one tag is needed:

`$('tag1, tag2').`  

### Selecting elements by class and id

`$('.class').`  
`$('#id').`  
`$('.class, #id').`  

### Selecting elements by type attribute

`$('tag[type="value"]').`  

or a simpler version:  

`$('tag:value').`  

### Selecting first, last, even or odd children

`$('child:first').`  
`$('child:last').`  
`$('child:even').`  
`$('child:odd').`  

### Selecting child of a parent

`$('parent child')`  
`$('parent child:first-child')`  
`$('parent child:first-of-type')`  
`$('parent child:last-child')`  
`$('parent child:last-of-type')`  
`$('parent child:nth-child(n)')`  
`$('parent child:nth-last-child(n)')` Going in reverse  

### Finding elements with jQuery

`$('parent').find('target').`  The target can be a tag, class or id or any other selector.  
`$('parent').children('target')` Searches through all the children of the parent for the target.  
`$('child').parent().` Accesses the child's parent  
`$('child').parents('target').` This is better than the parent() method. 
`$('child).siblings('target')` The target is optional.
`$(':header)` Will target all h1 - h6 elements 

### Accessing next and previous elements

`$('target').prev().` This will target the previous element regardless of what the element is.
`$('target').next().`  

### Using eq()

When working with objects with multiple items. NB! The index number n is 0 based like arrays.  

`$('parent child:eq(n)').`  
`$('child').parents().eq(0).` Will select the first parent of child. 

When negative numbers are used, the list will be traversed in reverse.

### First, last, and Not

When the first or last appearance of an element needs to be selected:  
`$('target').first().`  
`$('target').last().`  

When all similar elements needs to be accessed with the exception of one
`$('targets').not('target').` Not can also take a callback function as described for filter() below. 

### Filter()

Filter does the opposite of not. It will look at all the targets and select only the specified single target.
`$('targets').filter('target')`  

Some special keywords to use with filter:

- ':even'
- ':first'

Filter() can also take a callback function to search more specifically:

```JavaScript
$(`li`).filter(function(index) {
  return index % 3 === 0
})
```

Will return only elements whose index number is divisible by 3. The argument of the callback function is always the index number of the list of elements. If the statement is true, the element will be retained and if false, discarded. The retained elements will then be returned as an object.

## Modifying the DOM

All of the methods below can take callback functions as arguments and the html code can be determined within these functions based on the desired logic.

Instead of new content, existing elements can also be passed as arguments , but it is important to keep in mind that the elements will be moved and NOT cloned. If tgis is done on a target that returns a list of elements then the element will also be moved, but then cloned to subsequent members of the list.

### Appending an element or content

`$('parent').append('content or html code')` Appends the specified content as the last child of the targetted parent. Id multiple elements are targetted then the new content will be added to each member of the list of elements. 

Can also be coded as:

`$(content or html code).appendTo('parent')`  

Similar concept:

`$('target').html('HTML code')`  

### Prepend an element or content

`$('parent').prepend('content or html code')` Appends the specified content as the first child of the targeted parent.

Also:

`$(content or html code).prependTo('parent')`  

### .before()

`$('target').before('content or HTML code')` Adds the specified content before the target element as a sibling.

See also:

`$(content or html).insertBefore('target')`

### .after()

`$('target').after('content or HTML code')` Adds the specified content after the target element as a sibling.

See also:

`$(content or html).insertAfter('target')`

### Replacing elements

`$('target').replaceWith('content or HTML code')`  

Replacing several targets:

`$('content or HTML code').replaceAll('target1, target2')`

Alternatively a selector that selects multiple targets can also be used. Eg:

`$('content or HTML code').replaceAll('li')`  

A callback function can again be used to implement more complex replacements that depend on logic.

### Removing elements

`$('target').remove()`  

Also,

`$('target').empty()` Will remove everything inside the target. I.e., children or content. It will remove anything inside the element, but not the element itself.`$('target').html('')` will do the same

`$('target).detach()` All data and event handlers that are associated with the target is available. So this method is usually done by saving the result into a variable for later use: `const var1 = $('target').detach()`. With remove() on the other hand all associated data is lost. 

### Access Element Data

`$('target').text()` - No argument just returns the innerText of the element. If a string argument is passed then the innerText is updated with the new string. 
`$('target').html()` - Same as text, but full html is retrieved. Ignores parent HTML tags, so it only returns the text and internal HTML tags.  
`$('target').attr('attributeName')` Value of an attribute. If a second argument is passed then the value will be updated.
`$('target').val()` Used with forms to get the value of an input field.  
`$('target').prop('checked')` To get the value of a selected, radio or checkbox value on input fields.

NB! If these are called on targets that produce list objects then the first item in the list will be targetted for the value.

A callback function can also be used here as long as the function returns a value that is expected by the respective functions.

### Manipulating classes

To get a elements classses:  
`$('target').attr('class')`  

To check if an element has a class:  
`$('target').hasClass('className')` A boolean value is returned.  

To add a class:
`$('target').addClass('className')`  

To remove a class:
`$('target').removeClass('className')`  

To replace a class use the toggleClass() method:  
`$('target').toggleClass('currentClass newClass')`  

Callback functions can also be used here:

```JavaScript
$(`li`).addClass(function (index) {
  $(this).addClass(`item-${index}`)
})
```

```JavaScript
$(`div`).addClass(function (index ,currentClass){
  if (currentClass === `someClass`) {
    return `someOtherClass`
  }
})
```

The addClass() and removeClass() methods can also be chained together:

```JavaScript
$(`.red-box`).removeClass(`red-box`).addClass(`blue-box`)
```

### Manipulating Styles

To return the value of a style:  
`$('target').css('property')`  
`$('target').width()` Returns the width of the element without the px units.  
`$('target').height()` Same but for height.  

```JavaScript
const properties = $(`p`).css([`font-size`, `line-height`, `color`])
console.log(properties);
//Output: Object with property:value pairs
```

To change or add CSS styles:  
`$('target').css('property', 'value')`  

Instead of f passing in a new value, a callback function can also be used where some logic determines the return value of the function which will then be used as the new value.

To add to values:  
`$('target').css('property', '+=50px')` This can be done with anything that has a numeric value. -= Is also valid.  

To change several properties, pass in an object literal with property value pairs in it:

```JavaScript
$('target').css({
  'property1: 'value1',
  'property2: 'value2,
})
```

### Data Attributes

When the `data-` fields are in use in the HTML code, the data-items can be accessed as follow:

```HTML
    <div class="element" data-name="Johann" data-hobbies="['Music', 'Reading','Coding']">User</div>
```

```JavaScript
    const data = $('.element').data('name')
    console.log(data);
```

All data values can also be retrieved at once:  
`$('target').data()`  

To add data:

```JavaScript
  const cars = ['ford', 'Renault', 'Fiat']
  $('.element').data('cars', cars)
    
  console.log(data);
```
To remove data:

`$('target').removeData('key')`  

NB! This data won't appear on the HTML element when doing a inspector lookup, but will be there. Console.log will confirm that it is there.