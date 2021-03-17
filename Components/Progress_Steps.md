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
