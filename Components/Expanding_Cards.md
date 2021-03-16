
# Expanding Cards

## HTML code

Basically a parent div with 5 children div's which will form the interactive cards.

The first child div will have a class of `panel` and `active`. This `active` class is going to be toggled based on the active card. The rest start out with classes 'panel' only. This feature will be controlled with JavaScript.

Each card also has Some 'h3' text with a background image. Brad used inline styling for the background images, but I do not like inline CSS and therefore added `image1-5` classes and declared them in the stylesheet.

## CSS code

The following CSS styling was applied for the reasons listed below:

`.panel`

_background-size: auto 100%;_ Two-value syntax: I.e., width, height (?background: cover; a better option). The auto option scales the background image in the corresponding direction such that its intrinsic proportions are maintained. The height remains constant during the expansion of the individual cards, so I presume that is why width was set as auto and height as 100% to fit parent container.
_background-position: center;_ This sets the initial position for each background image relative to its parent. In this case the choice is self explanatory.
_background-repeat: no-repeat;_ Self explanatory.
_height: 80vh;_ Giving dimension to the div's. Slighly less than parent container in this case.
_border-radius: 50px;_ Rounding the edges.
_color: white;_ Text colour.
_cursor: pointer;_ To change cursor appearance to indicate to user that the images are clickable.
_flex: 0.5;_ This initial setting will allow the items to take up equal size, but it will be part of the JavaScript manipulation.
_margin: 10px;_ To seperate images from each other.
_position: relative;_ So that `h3` elements can be positioned which are contained in the panels.
_transition: flex 0.7s ease-in;_ This is for smooth transitions when the cards are expanded.

`.panel h3`

_font-size: 24px;_ SX
_position: absolute;_ SX
_bottom: 20px;_ Positioning relative to parent `.panel` container.
_left: 20px;_ SX
_margin: 0;_
_opacity: 0;_ Set to 0 so that text is only visible when a panel is selected. I.e., Not visible by default

`.panel.active`

_flex: 5;_ So that active panel grows relative to other panels

`panel.active h3`

_opacity: 1:_ To make text visible when panel is active.
_transition: opacity 0.3s ease-in 0.4s_ To smooth out the transition

`@media(max-width: 480px)`

The `.container` width changed to 100vw so full screen is used on small devices.  
The last two panels were also hidden for small screens by targeting the `.panel:nth-of-type(4), .panel:nth-of-type(5)` pseudo elements and setting `display: none;`

## JavaScript

A normal event listener loop was added to the `.panel` class, but a second function had to be written to remove the `.active` class from all `.panel` elements when a click is registered but before the .add('active') statement.

## Conclusion

This is a nice "widget" or gimmic that can be used for various purposes like pricing options, or services offered etc sections of a web page.
