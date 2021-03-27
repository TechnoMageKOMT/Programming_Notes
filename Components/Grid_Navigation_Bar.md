# Grid - Navigation

## HTML

Create a header element with class `header`. Inside it a div with class `header-container` which will house the header content. Next an img element is added in the inner div. This image is linked to the logo.png image file. The nav element with the class of `nav` is added next on the same level. Within the nav element a unordered list with class `nav--list` is added. To the ul is added 5 list items with link elements. The first item is given a class of `active`. The links are given the following text content: Home, Articles, Video, Support, Contact.

```HTML
<header class="header">
      <div class="header-container">
        <img src="images/logo.png" alt="Website logo" />
        <nav class="nav">
          <ul class="nav--list">
            <li class="active"><a href="">Home</a></li>
            <li><a href="">Articles</a></li>
            <li><a href="">Video</a></li>
            <li><a href="">Support</a></li>
            <li><a href="">Contact</a></li>
          </ul>
        </nav>
      </div>
</header>
```

## CSS

```CSS
:root {
    --body-color: #333;
    --border-bottom-color: rgb(153, 13, 181);
    --header-background: #eee
}

*,
*::before,
*::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    background-color: var(--body-color);
    font-family: 'Source Sans Pro', sans-serif;
}

img {
    max-width: 100%;
}

ul {
    paddng: 0;
    list-style: none;
}

a {
    text-decoration: none;
}

.header {
    width: 100%;
    background-color: var(--header-background);
}

.header-container {
    display: grid;
    grid-template-columns: 200px 1fr; /*Size of logo and 1fr to take up the rest (i.e., nav) of the width*/
    align-items: center;
    width: 100%;
    max-width: 1280px;
    margin: auto;
    min-height: 80px;
    padding: 20px;
}

.nav {
    justify-self: right; /*To get nav elements to stick to right side of viewport*/
}

.nav--list {
    display: grid;
    grid-auto-flow: column; /*To get each item in its own column and in a single row*/
    column-gap: 40px;
}

.nav--list a {
    display: inline-block;
    font-size: 24px;
    color: #333;
    padding-bottom: 2px;
    border-bottom: 3px solid transparent;
    transition: border-color 0.2s ease;
}

.nav--list .active a,
.nav--list a:hover {
    border-bottom-color: var(--border-bottom-color);
}
```
