# Grid Partners Block

This component is for the list of partners that often appear on webpages. It is constructed here with CSS Grid.

## HTML

The HTML is a simple container with class`wrapper` and inside of that the image container `partners`. The latter is the grid container. Within the grid container there are simply 9 `<img>` elements.

## Global reset and initialisation

```CSS
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --back-color: #f6f6f6;
  --heading-color: rgb(130, 129, 129);
}

body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  font-family: 'Source Sans Pro', sans-serif;
  background-color: var(--back-color);
}
```

## Project CSS

```CSS
h1 {
  text-align: center;
  color: var(--heading-color);
  font-weight: 600;
}

img {
  display: block;  
  width: 100%;          /*To force images to fill the grid cells further down*/
}

.wrapper {
  width: 100%;          /*Fill viewport width*/
  max-width: 1280px;    /*Limit to screen size*/
  margin: auto;         /*To center container*/
}

.partners {
  display: grid;
  grid-template-columns: repeat(3, 200px);
  grid-auto-rows: 80px;
  gap: 60px 80px;
  margin-top: 100px;
  justify-content: center;  /*To center on page*/
  place-items: center center; /*Center images within cells*/
}  
```  

