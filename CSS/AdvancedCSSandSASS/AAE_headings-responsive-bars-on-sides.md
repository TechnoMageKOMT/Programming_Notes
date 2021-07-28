# Heading: Responsive coloured bars on sides

This is a way of placing responsive coloured bars inline with and besides headings. The bars fills the white space that would otherwise have been to the sides of centered headings.

```HTML
<h1 class="intro">Here is a generic heading</h1>
```

```SCSS
.intro {
  position: relative;
  display: inline-block;

  &::before,
  &::after {
    content: '';
    display: block;
    position: absolute;
  }

  &::before {
    background-color: white;
    height: 101%;
    left: -20px;
    right: -20px;
    z-index: -1;
  }

  &::after {
    background-color: red;
    width: 100vw;
    height: 100%;
    left: 50%;
    top: 0;
    transform: translateX(-50%);
    z-index: -2;
  }
}
```
