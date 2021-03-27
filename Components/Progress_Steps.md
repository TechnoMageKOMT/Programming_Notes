# Progress Steps

## Coulour Scheme

--back-color: #f6f7fb; (Body Background)
--circle-back: #fff; (Circle background)
--circle-text: #999;
--line-inactive: #e0e0e0;
--line-active: #3498db;

## HTML

Start again with an outer div container with class **container**.

Within that another container with class **progress-container**. This will be the container for the "animated section of the project (I.e., the circles, progress bar/line etc).

Within that a div with _class and id_ of **progress** (no content this is just for styling and for creating the progress bar/line that will connect the different steps).

On the same level the circle div's will follow with a class of **circle** (the first one will also have the active class). These will all have the numbers 1 through 4 as content.

Outside of this but on the same level as the progress-container div, the button's will be placed. The first button will have a _class_ of **btn** and _id_ of **prev**. It will also have the **disabled attribute** set (this is because it should not be selectable at the very beginning of the process.). The second button will be identical but have a **next**. _id_ and the disabled attribute removed. Both will also have the inner text corresponding to their ids.

## CSS

The normal baseline CSS was started with:

```CSS

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  font-family: 'Roboto', sans-serif;

}
```

Changes made to the `body{}` section: `flex-direction: column;` was removed because the project does not require columnar orientation. `background: #f6f7fb;` was added.

The rest of the elements were styled as follow:

```CSS
.container {
  text-align: center;               /*To center align the numberning / steps*/
}

.progress-container {
  display: flex;                    /*To space the steps out horizontally*/
  justify-content: space-between;   /*To place the available space between the steps*/
  position: relative;               /*To allow the absolute positioning of elements inside of it*/
  margin-bottom: 30px;              /*To create some space between the steps and buttons*/
  max-width: 100%;                  /*If content is larger than the parent container the height will be adjusted.*/
  width: 350px;                     /*To create some more space between the steps*/
}
```

The progress line has to be grey in it's inactive state and transition into blue when the steps are activated. This will be done by use of the `progress` class and the `::before` pseudoclass.

```CSS
.progress-container::before {         /*styling of the horizontal grey "passive" progress line/bar*/
  content: '';
  background-color: #e0e0e0;
  position: absolute;
  top: 50%;                          /*Leaves top in the middel of the container*/
  transform: translateY(-50%);       /*Moves half the width of the line upwards so that it is truly centered behind the steps */
  left: 0;
  height: 4px;
  width: 100%;
  z-index: -1;
}

.progress {                             /*styling of the horizontal progress line/bar*/
  background-color: #3498db;
  position: absolute;
  top: 50%;                             /*To space vertically centered in container*/
  transform: translateY(-50%);          /*To space verticallt centered in container*/
  left: 0;
  height: 4px;
  width: 50%;                           /*This will change dynamically as the line moves between steps*/
  z-index: -1;                          /*To place behind the steps elements*/
  transition: 0.4s ease;                /*To animate line as it moves between steps*/
}

.circle {
  background-color: var(--circle-back);
  color: var(--circle-text);
  border-radius: 50%;
  height: 30px;
  width: 30px;
  display: flex;    /*To center numbers*/
  align-items: center;  /*To center numbers*/
  justify-content: center;  /*To center numbers*/
  border: 3px solid var(--line-inactive);
  transition: 400ms ease.
}


.circle.active {
  border-color: var(--line-active);
}

.btn {
  background-color: var(--line-active);
  color: var(--circle-back);
  border: 0;  /*Removes the button border*/
  border-radius: 6px;
  cursor: pointer;
  font-family: inherit;
  padding: 8px 30px;
  margin: 5px;
  font-size: 14px;
}

.btn:active {  /*Pseudoclass for click*/
  transform: scale(0.98);
}

.btn:focus {
  outline: 0; /*? Removes outline*/
}

.btn:disabled {
  background-color: var(--line-inactive);
  cursor: not-allowed;
}
```

## JavaScript

JavaScript tasks:

1. Aquire assets from the DOM
2. Set counter
3. Set up event listeners to increment counters and call update function
4. Create update function to
   i) Handle active class add and remove
   ii) Progress line percentages
   iii) Disable/enable of prev and next buttons

```JavaScript
const progress = document.getElementById('progress');
const prev = document.getElementById('prev');
const next = document.getElementById('next');
const circles = document.querySelectorAll('.circle');

let currentActive = 1;

next.addEventListener('click', function(){
  currentActive++;

  if(currentActive > circles.length){
    currentActive = circles.length
  }

  update();
})

prev.addEventListener('click', function(){
  currentActive--;

  if(currentActive < 1){
    currentActive = 1
  }

  update();
})

function update(){
  for (let i = 0; i < circles.length; i++) {
    if (i < currentActive){
      circles[i].classList.add('active');
    } else {
      circles[i].classList.remove('active');
    }
  }
  const actives = document.querySelectorAll('.active');
  progress.style.width = (actives.length - 1) / (circles.length -  1) * 100 + '%';

  if (currentActive === 1){
    prev.disabled = true;
  } else if (currentActive === circles.length) {
    next.disabled = true;
  } else {
    prev.disabled = false;
    next.disabled = false;
  }

}
```
