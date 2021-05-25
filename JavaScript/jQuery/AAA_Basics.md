# jQuery Introduction and Basics

## What is jQuery

jQuery is a JavaScript library designed to simplify HTML DOM tree traversal and manipulation, as well as event handling, CSS animation, and Ajax. It is free, open-source software using the permissive MIT License. As of May 2019, jQuery is used by 73% of the 10 million most popular websites. Web analysis indicates that it is the most widely deployed JavaScript library by a large margin, having at least 3 to 4 times more usage than any other JavaScript library. - Wikipedia

## Other JavaScript libraries

- jQuery UI
- MooTools
- Underscore.js
- Dojo Toolkit

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

### Accessing next and previous elements

`$('target').prev().` This will target the previous element regardless of what the element is.
`$('target').next().`  

### Using eq()

When working with objects with multiple items. NB! The index number n is 0 based like arrays.  

`$('parent child:eq(n)').`  
`$('child').parents().eq(0).` Will select the first parent of child. 

### First, last, filter and Not

When the first or last appearance of an element needs to be selected:  
`$('target').first().`  
`$('target').last().`  

When all similar elements needs to be accessed with the exception of one
`$('targets').not('target').`  

Filter does the opposite. It will look at all the targets and select only the specified single target.
`$('targets').filter('target')`  

## Modifying the DOM

### Appending an element or content

`$('parent').append('content or html code')` Appends the specified content as the last child of the targetted parent.  

Can also be coded as:

`$(content or html code).appendTo('parent')`  

Similar concept:

`$('target').html('HTML code')`  

### Prepend an element or content

`$('parent').prepend('content or html code')` Appends the specified content as the first child of the targeted parent.

Also:

`$(content or html code).prependTo('parent')`  

### .before()

`$('target').before('content or HTML code')` Adds the specified content before the target element.

### .after()

`$('target').after('content or HTML code')` Adds the specified content after the target element.

### Replacing elements

`$('target').replaceWith('content or HTML code')`  

Replacing several targets:

`$('content or HTML code').replaceAll('target1, target2')`

Alternatively a selector that selects multiple targets can also be used. Eg:

`$('content or HTML code').replaceAll('li')`  

### Removing elements

`$('target').remove()`  

Also,

`$('target').empty()` Will remove everything inside the target. I.e., children or content. `$('target').html('')` will do the same

### Access Element Data

`$('target').text()` - No argument just returns the innerText of the element. If a string argument is passed then the innerText is updated with the new string.  
`$('target').attr('attributeName')` Value of an attribute. If a second argument is passed then the value will be updated.
`$('target').val()` Used with forms to get the value of an input field.  
`$('target').prop('checked')` To get the value of a radio or checkbox.  

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

### Manipulating Styles

To return the value of a style:  
`$('target').css('property')`  
`$('target').width()` Returns the width of the element without the px units.  
`$('target').height()` Same but for height.  

To change or add CSS styles:  
`$('target').css('property', 'value')`  

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

NB! This data won't appear on the HTML element when doing a inspector lookup, but will be there. Console.log will confirm that it is there.
NB! This data won't appear on the HTML element when doing a inspector lookup, but will be there. Console.log will confirm that it is there.