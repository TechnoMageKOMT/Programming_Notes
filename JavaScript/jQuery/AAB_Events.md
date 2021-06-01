# jQuery Event Handling

## Basic Syntax

```JavaScript
$('target').click(function() {
    console.log('click!!');
  })
```

or

```JavaScript
$('target').on('click mouseleave mouseover', function() {
    console.log('click!!');
  })
```

The second method allows for multiple events to be responded to.

## Mouse events

### mouseenter and mouseleave

Same syntax as above, but with these two keywords. 

### hover

The same syntax is used as above, but additional functionality is possible. Two events fire when the mouse is hovered over an element. The first is when the mouse enters the element and the second when the mouse leaves it.

Two functions can therefore be passed as arguments. The first is for mouseenter and the second for mouseleave.

```JavaScript
$('target').hover(function(){
    console.log('Mouse enter');
  }, function(){
    console.log('Mouse leave');
  })
```

### mousedown and mouseup

This refers to the clicking action. I.e., The click and then release of the LHS mouse button.

### mousemove

This will trigger whenever the mouse moves over the target element.

A way to get the XY coordinates of the movement is:

```JavaScript
$('.element').mousemove(function(e){
    let pagecoords = "(" + e.pageX + " , " + e.pageY + ")"
    console.log("coords:" + pagecoords);
})
```

## Keyboard events

- keydown
- keyup

```JavaScript
$(document).keydown(function(e){
    console.log(e.which);
  })
`Output: Value associated with the key pressed`
```

### Example of a moving square

```JavaScript
$(document).keydown(function(e){
    
    const DOWN = 40
    const RIGHT = 39

    if (e.which === DOWN)
      $('.element').css({top: '+=10px'})
    if(e.which === RIGHT)
      $('.element').css({left: '+=10px'})
      
})
```

## Window events

### scroll

```JavaScript
$(document).scroll(function(){
    console.log('Scrolling');
  })
```

### resize

This is on the window object:

```JavaScript
$(window).resize(function(){
    console.log('Resize');
  })
```

## Adding the same handler for multiple events

```JavaScript
$(`html`).on(`click keydown`, function () {
    console.log(`Mouse was click or key was pressed`);
})
```

## on method

When adding event handlers on dynamically created content, the on method should be used as follows:

```JavaScript
$(document).on('click', 'target', function() {
  console.log('Clicked');
})
```

This method is therefore a better way of handling events especially when content is being generated dynamically (on the fly).

## forms

When working with forms a lot of information can be gained from events.

To capture when a user goes into a form field and out again.

- focusin
- focusout
- blur (a focus out behaviour)

```JavaScript
$('target').focusin(function() {
    console.log('Focus in');
  })
```

Example of using blur on a form field:

```JavaScript
$('input').blur(function(e) {

    const value = $(this).val()

    if (value.length < 5) {
      $(this).addClass('error')
    } else {
      $(this).removeClass('error')
    }
})
```

```HTML
    <input type="text" name="" id="" placeholder="Enter name">
    <input type="text" name="" id="" placeholder="Enter car model">
    
    <style>
      .error {
        background: red;
      }
    </style>
```

Side note: `const value = $(this).val()` is equivalent to the statement `const value = e.target.value`. Refer to "Basics.md". val() is used to retrieve the value of input fields. In this case `$(this)` refers to the input field that was blurred away from.

### Form events: submit

The default behaviour for form submits is to reload the page to send the data. If this refresh page behaviour needs to be stopped, jQuery has a solution.

The solution is the submit() and preventDefault() methods:

```JavaScript
$('form').submit(function(e) {
    e.preventDefault()
    console.log('Not reloading');
})
```

### Form events: change

Change events can be listened for on forms. This is usually used for select, checkboxes and radio buttons. The problem is that it only gives information on whether a change occurred. No information about the actual data. The following code is the jQuery way around this limitation:

```HTML
      <input type="checkbox" name="vehicle" value="Bike" id="">I have a bike
      <br>
      <input type="checkbox" name="vehicle" value="Car" id="">I have a car
      <br>
```

```JavaScript
$('input[type=checkbox]').change(function() {
    
    const checked = $(this).is(":checked")
    if (checked) {
      console.log($(this).val() + ' is checked');
    } else {
      console.log($(this).val() + ' is not checked');
    }
})
```

Note: The :checked CSS pseudo-class selector represents any radio `<input type="radio">`, checkbox `<input type="checkbox">`, or option `<option>` in a `<select>` element that is checked or toggled to an on state.

## Triggering events automatically

If an event should be triggered within the application just call the event afterwards without passing any arguments. Eg.,

```JavaScript
$(`.red-box`).click(function() {
    $(this).fadeTo(1000, 0.5)
  })

$(`.red-box`).click()
//This code will automatically trigger the click event when the page is loaded.
```

## Delegated Events

The solution to event hanlders on dynamically created content. The code below places the event handler or the parent of the dynamically created code and then "delegate" it to elements of the same type as the dynamically created content.

```JavaScript
$(`#content`).append(`<p>This is a dynamically added paragraph</p>`)  

$(`#content`).on(`click`, `p`, function() {
    $(this).slideUp()
})
```

## Passing additional data to events

Refer: [https://api.jquery.com/event.data/]

```JavaScript
const greetUser = function (userdata) {
    const username = userdata.user || `Anonymous`
    const domain = userdata.domain || `Example.com`
    alert(`Welcome back ${username} from ${domain}!`)
  }

  $(`#btn-click`).click({
    user: `Peter`,
    domain: `petersommerhof.com`,
  }, function(e) {
    greetUser(e.data)
})
```
