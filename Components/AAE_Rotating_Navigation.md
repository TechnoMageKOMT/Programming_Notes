# Rotating Navigation Animation

## HTML

Starts with div `container` that wraps around everything. Within that a div `circle-container` then `circle` with two buttons one with id `close` and the other `open`. The content of the close button will be the fontawesome icon 'fa fa-times' and the open button 'fa fa-bars'

Outside the `circle-container` but still inside `container` an `<h1>`, `<small>` for the author and the lorem100. Followed by `<h3>My Dog</h3>` an `<img>` and lorem75.

Finally outside the `container` div a nav with 1 ul and three li inside (Home, About, Contact) (font awesome icons fa-home, fa-user, fa-envelope)

## CSS

```JavaScript
:root {
  --body-color: #333;
  --text-color: #222;
  --main-container-back-color: #fafafa;
  --circle-back-color: #ff7979;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  overflow-x: hidden; /*Hides scroll on x-axis only*/
  font-family: Lato, sans-serif;
  background-color: var(--body-color);
  color: var(--text-color);
}

/*The body color will only show during the "tilting* navigation so the similar text and background colours in the body are not as conflicting as they appear here. The container background (below) is actually light*/

.container {
  background-color: var(--main-container-back-color);
  transform-origin: top left;
  transition: transform 500ms linear;
  width: 100vw;
  min-height: 100vh;
  padding: 50px;
}

.container.show-nav {
  transform: rotate(-20deg);
}

.circle-container {
  position: fixed;
  top: -100px;
  left: -100px;
}

.circle {
  background-color: var(--circle-back-color);
  height: 200px;
  width: 200px;
  border-radius: 50%;
  position: relative; /*For absolute pos of buttons*/
  transition: transform 500ms linear;
}

.circle button {
  cursor: pointer;
  position: absolute;
  top: 50%;
  left: 50%;
  height: 100px;
  background: transparent;
  border: 0;
  font-size: 26px;
  color: var(--main-container-back-color);
}

.circle button:focus {
  outline: none;
}

.circle button#open {
  left: 60%;
}
.circle button#close {
  top: 60%;
  transform: rotate(90deg);
  transform-origin: top left;
}

.content img {
  max-width: 100%;
}
```
