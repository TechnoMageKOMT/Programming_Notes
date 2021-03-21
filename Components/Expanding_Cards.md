h
# Expanding Cards

## HTML code

Basically a parent div with 5 children div's which will form the interactive cards.

The first child div will have a class of `panel` and `active`. This `active` class is going to be toggled based on the active card. The rest start out with classes 'panel' only. This feature will be controlled with JavaScript.

Each card also has Some 'h3' text with a background image. Brad used inline styling for the background images, but I do not like inline CSS and therefore added `image1-5` classes and declared them in the stylesheet.

## Global Reset and Initialisation

```CSS
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --body-color: rgb(217, 237, 245);
  --panel-color: rgb(105, 105, 105);
  --wrapper-color: rgb(166, 166, 230);
}

body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  font-family: 'Merienda', cursive;
  overflow: hidden;
}
```

## CSS code

```CSS
.container {
  display: flex;
  width: 90vw;  /*To set width slightly smaller than the viewport*/
}

.panel {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 80vh;
  border-radius: 50px;
  color: white;
  cursor: pointer;
  flex: 0.5;    /*To make all panels equal in width*/
  margin: 10px;   /*To seperate images from each other*/
  position: relative; /*Needed for positioning of h3 text below*/
  transition: flex 0.7s ease-in;  /*Smooth transitions when panels expand*/
}

.panel h3 {
  font-size: 24px;
  position: absolute;
  bottom: 20px;
  left: 20px;
  margin: 0;
  opacity: 0;
}

.panel.active {
  flex: 5;    /*To expand the active panel relative to the others*/
}

.panel.active h3 {
  opacity: 1;   /*To make text visible only on active panels*/
}

/*This media query is to limit display on small screens to only three of the panels and to use the full width of the viewport*/

@media(max-width: 480px){
  .container {
    width: 100vw;
  }

  .panel:nth-of-type(4), .panel:nth-of-type(5) {
    display: none;
  }
}
```

## JavaScript

A normal event listener loop was added to the `.panel` class, but a second function had to be written to remove the `.active` class from all `.panel` elements when a click is registered but before the .add('active') statement.

```JavaScript
const panels = document.querySelectorAll('.panel');
for (let i = 0; i < panels.length; i++) {
  panels[i].addEventListener('click', function(){
    removeActiveClasses();
    panels[i].classList.add('active')
  })
}

function removeActiveClasses(){
  for (j = 0; j < panels.length; j++) {
    panels[j].classList.remove('active')
  }
}
```


## Conclusion

This is a nice "widget" or gimmic that can be used for various purposes like pricing options, or services offered etc sections of a web page.
