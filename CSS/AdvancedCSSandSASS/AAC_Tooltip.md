# Tooltip

## Example 1

```HTML
<button data-tooltip="TooltipText">Hover Me</button>
```

```CSS
button {
  margin: 10rem;
}

[data-tooltip] {
  position: relative;
}

[data-tooltip]:hover::before {
  content: attr(data-tooltip);
  position: absolute;
  width: 100%;
  background-color: black;
  color: white;
  padding: 0.25rem;
  top: -0.5rem;
  left: 50%;
  transform: translate(-50%, -100%);
}
```

## Example 2

Give the `<a>` tag a data-tooltip attribute. Then set the attr value to the content property.

```HTML
<p>Some sentence<a href="#" data-tooltip="a cool tool tip">and a link</a>in this paragraph</p>
```

```CSS
a[data-tooltip] {
position: relative;
}

a[data-tooltip]::after {
  content: attr(data-tooltip);
  display: block;
  position: absolute;
  background-color: gray;
  padding: 1em 3em;
  color: #fff;
  border-radius: 5px;
  font-size: 0.8em;
  bottom: 0;
  left: 0;
  white-space: nowrap;
  transform: scale(0); /*This will make it dissappear unless hovered over*/
  transition:
    transform 150ms ease-out,
    bottom 150ms ease-out;
}

a[data-tooltip]:hover::after {
  transform: scale(1);
  bottom: 100%;
}
```
