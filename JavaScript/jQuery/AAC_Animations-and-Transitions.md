# Animations and Transitions

## hide()

`$('target').hide()` - Just hides the element.
`$('target').hide(1000)` - Hide over 1 second. The keywords `slow` and `fast` can also be used as an argument. Their durations are 600ms and 400ms respectively.
`$('target').hide(1000, function(){})` - The second optional argument is a call back function

Hide takes place from bottom to top and right to left by default.

NB! The hiding of elements places the display property of hide onto elements. This also applies to the similar methods below.

A work around to this is to use the fadeTo() method and to set the opacity to 0. This will make sure the display property is not changed.

## show()

The opposite of `hide()`, but everything else is the same.

## toggle()

Toggles between `show()` and `hide()`.

## fadeIn()

Similar to `show()` but eased.

## fadeOut()

Similar to `hide()` but eased.

## fadeTo()

Takes an additional argument of opacity that the element should fade out to or in to. `$('target').fadeTo(1000, 0.3, function(){})`

## toggleFade

Example:

```HTML
    <div
      class="element"
      style="width: 100px; height: 100px; background: red"
    ></div>
 
    <br />

    <div class="fadeIn">Fade In</div>
    <br />
    <div class="fadeOut">Fade Out</div>
```

```JavaScript
$('.fadeIn, .fadeOut').click(function(){
    $('.element').fadeToggle(2000, function() {
      console.log("Transition Complete");
    })
})
```

## slideUp()

Same rules applies as above

## slideDown()

Same rules applies as above

## slideToggle()

Same syntax and rules as toggleFade().

## Custom animations

These animations takes four arguments.

1. The properties to change (only numeric properties apply with units included. Color for instance is not supported)
2. The duration of the animation
3. Easing function (dealt with in jQuery UI)(default = swing)
4. Callback function

Example:

```JavaScript
$(document).click(function() {

    $('.element').animate({
      left: "200px",
      top: "50px",
      width: "50px",
      height: "50px",
      fontSize: "7px",
      opacity: "0.2"
    }, 2000, 'swing', function() {
      console.log('Animate done');
    })
})
```

## Stop it all

The `stop()` prevents animations from repeating more than once in response to repeated events. It stops any animations that are currently running on element so that the next one can start.

Example:

```JavaScript
$('.element').hover(function() {
    $(this).stop().animate({left: "50px"}, "slow")
  }, function(){
    $(this).stop().animate({left: "0px"}, "slow")
})
```

If the mouse is moved repeatedly over the element, the animation will keep on repeating for the same amount of times and this is usually not what is intended. The stop() method prevents this, so the animation will only take place once when the mouse enters over the element and once when it leaves.

For a better explanation run the above code. The `element` is a block div with a background color.

## Timing Animations

Two methods:

- Callback method
- Delay method

### Callback method

This method is basically using embedded code to sequentially animate.

```HTML
    <div class="square one"></div>
    <div class="square two"></div>
    <div class="square three"></div>

    <style>
      .square {
        width: 50px;
        height: 50px;
        background-color: blue;
        margin-bottom: 20px;
      }
    </style>
```

```JavaScript
$('.square.one').animate({marginLeft: "+=100"}, 1000, function() {
    $('.square.two').animate({marginLeft: "+=100"}, 1000, function(){
      $('.square.three').animate({marginLeft: "+=100"}, 1000)
    })
})
```

### Delay Method

```JavaScript
$('.square.one').animate({marginLeft: "+=100"}, 1000)
$('.square.two').delay(200).animate({marginLeft: "+=100"}, 1000)
$('.square.three').delay(1000).animate({marginLeft: "+=100"}, 1000)
```

This is a better method than the callback method because one has very fine control over the animation timing.

The two methods could also be combined if need be:

```JavaScript
$('.square.one').animate({marginLeft: "+=100"}, 1000, function() {
    $('.square.two').delay(200).animate({marginLeft: "+=100"}, 1000)
    $('.square.three').delay(1000).animate({marginLeft: "+=100"}, 1000)
})
```
## Chaining 

The delay method is an example of chaining in jQuery where functions are chained one after the other to achieve the desired effect.

