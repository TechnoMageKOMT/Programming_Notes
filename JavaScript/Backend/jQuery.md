# jQuery

## What is jQuery

The most popular JavaScript Library.

Library of code written externally that can be incorporated into own code to improve one's own efficiency or even the efficiency of one's own code.  

```jQuery
document.querySelector('h1');
```

```jQuery
jQuery('h1);
```

or even better:

```jQuery
$('h1')
```

## How to make use of it (CDN)

The most popular Content Delivery Network (CDN) for jQuery is Google's (there is a link to the snippets on the jquery.com download section). Use the `<script>` tag with the latest version of jQuery (3.6.0 at the writing of this document March 2021).

Reminder: Great thing about a CDN is that if a user has visit a particular CDN for some other website, it is likely to already be cached in their browser's memory.

The position of the `<scrip>` tag is **very NB**. It must be above the local js scripts. This is so that the library is available for the excecution of the code written in jQuery in the local js scripts. If this is not done, the browser will simply give "not defined" errors on all jQuery commands encountered.  

It is also not recommended to load the script in the head section of the HTML document. There is a way around this (by loading the .ready()callback function), but it is not recommended since JS scripts should ideally be loaded just before the closing body tag once the entire DOM has been loaded.

## Selecting Elements 

jQuery works very much like querySelector and querySelectorAll in normal JavaScript. See above for syntax.

## Manipulating CSS style

### General syntax:

```jQuery
$('target').css('property','new value')
```

### The value of a property can also be accessed simply by:

```jQuery
$('target').css('property')
E.g., 
console.log($('h1').css('color'));
Output: rgb(0, 128, 0)
```

### Add and remove a class is:

```jQuery
$('h1').addClass('someClass')
$('h1').removeClass('big-title')
Multiple classes
$('h1').addClass('big-title margin-50')
```

### To check if an element has a specific class:

```jQuery
console.log($('h1').hasClass('margin-50'))
Output: true
```

### Change text or HTML

```jQuery
$('h1').text('newvalue') //Similar to innerText and textContent 

$('h1').html('newHTML') //Similar to innerHTML in vanilla JS
```

### Change attributes

To access the value of an attribute:

```jQuery
console.log($('img').attr('src'))
Output: #
```

To change the attributes value:

```jQuery
$('a').attr('href', 'https://www.google.com')
```

### Print out all classes using the .attr() method

```jQuery
console.log($('h1').attr("class"))
Output: big-title margin-50
```

### Add event listeners with jQuery

```jQuery
$('h1').click(function(){
  $('h1').css('color', 'red')
})
```

To add listeners to multiple items under selection

```jQuery
$('button').click(function(){
  $('h1').css('color', 'pink')
})
```

No need for a for loop. In this case there were 5 buttons that would have all been selected.

### Keyboard events

```jQuery
$('input').keypress(function(e){
  console.log(e.key);
})
```

or if the listener needs to be tied to the whole document

```jQuery
$('body').keypress(function(e){
  console.log(e.key);
})

or 

$(document).keypress(function(e){
  console.log(e.key);
})
```

### Advanced event listener .on() 

Takes two parameters. The first is the type of event and the second is the callback function linked to the event.

```jQuery
$('h1').on('mouseover', function(){
  $('h1').css('color', 'purple')
})
```

This can be done for any of the MDN listed DOM events.

### Adding and removing elements

To add an element before the targeted one:

```jQuery
$('h1').before('<button>New</button>')
```

also 

```jQuery
$('h1').after()
$('h1').prepend() //inserts into / inside the selected element, Beginning
$('h1').append()  //Opposite of prepend()
```

Removing element:

```jQuery
$('h1').remove() 
```

This will remove the selected h1 element.

### Animation

.hide()
.show()

```jQuery
$('button').on('click', function(){
  $('h1').hide();
})
```

Will hide the h1 element when any button is clicked.

```jQuery
$('button').on('click', function(){
  $('h1').show();
})
```

Will show the same element when a button is clicked.

```jQuery
$('button').on('click', function(){
  $('h1').toggle();
})
```

Will toggle between .hide() and .show().

`.fadeOut()` Will hide the h1 but in a smoother movement (ease). It first reduces the opacity and then hides the element.
`.fadeIn()` Opposite.
`fadeToggle()` Fade version of .toggle()
`slideUp()` 
`slideDown()`
`slideToggle`

### .animate({})

Within the {} a normal CSS property: value pair is entered and jQuery will automatically animate from the original value to the new value.

```jQuery
$('button').on('click', function(){
  $('h1').animate({opacity: 0.5})
})
```

**NB Caveat** Only properties with numeric values can be used in this method. Color for instance cannot be used. If a number with a unit is used such as % or px then it should be enclosed in quotation marks.

Any of the animation methods listed above can be changed together.

```jQuery
$('button').on('click', function(){
  $('h1').slideUp().slideDown().animate({opacity: 0.5})
})
```

### Reference of available methods

Google "jQuery methods". The w3schools link has extensive information on available methods, but there is a full list available on the jQuery website at [https://api.jquery.com/].


