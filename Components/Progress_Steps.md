# Progress Steps

## HTML

Start again with an outer div container with class **container**.

Within that another container with class **progress-container**. This will be the container for the "animated section of the project (I.e., the circles, progress bar/line etc).

Within that a div with *class and id* of **progress** (no content this is just for styling and for creating the progress bar/line that will connect the different steps).

On the same level the circle div's will follow with a class of **circle** (the first one will also have the active class). These will all have the numbers 1 through 4 as content.

Outside of this but on the same level as the progress-container div, the button's will be placed. The first button will have a *class* of **btn** and *id* of **prev**. It will also have the **disabled attribute** set (this is because it should not be selectable at the very beginning of the process.). The second button will be identical but have a **next**. *id* and the disabled attribute removed. Both will also have the inner text corresponding to their ids.

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
  top: 50%;                             
  transform: translateY(-50%);          
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