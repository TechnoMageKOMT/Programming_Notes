# Advanced CSS and SASS - General Notes

Asign a class to every single element in the HTML.

Set general font properties, including line height, color in the body{} section of the CSS because font properties are usually inherited.

To set a white border around the entire website add padding to the body{}.

## clip-path property

Clips an element to a basic shape or to a SVG source. Ref: [https://bennettfeely.com/clippy/] for a tool to create various different shapes. A link for this tool is also available on Jonas' resources page [http://codingheroes.io/resources/]

## Special character selectors

`[class^="col-"]` - All elements with a class starting with col-
`[class*="col-"]` - All elements with a class containing the string col-
`[class$="col-"]` - All elements with a class ending in col-

## background-clip property

Use together with -webkit-background-clip. If the value is set to `text` and there is a background colour gradient or image then the letters will be filled with the image. Make sure `color` is set to transparent.

## Usage of mixins

Code in mixin.scss file:

````CSS
@mixin someName {
  selector {
    /*code*/
  }
}

Inclusion in sass stylesheet:

```CSS
@include someName
````

## BEM

Block - Standalone component. Meaningful on its own
Element - Part of a block. No meaning on its own
Modifier - Different version of a block or element

`block`
`block__element`
`block__element--modifier`

## Direct child selector

`primarySelector > *` - This would select all direct children of the primary selector regardless of which types of elements they are.

## Perspective property

The perspective property is used to give a 3D-positioned element some perspective. The perspective property defines how far the object is away from the user. So, a lower value will result in a more intensive 3D effect than a higher value.

When defining the perspective property for an element, it is the CHILD elements that get the perspective view, NOT the element itself.

Tip: Also look at the perspective-origin property, which defines at which position the user is looking at the 3D object.

When using this property include -moz-perspective to make sure Firefox browsers also supports the property.

The lower the value the more dramatic the effect, so generally higher values (~ 1500px) gives the effect of a rotation towards the user (rotation around Y axis). It is really a matter of experimenting with different values until the desired effect is obtained.

## Tooltip

```HTML
<body>
  <button data-tooltip="TooltipText">Hover Me</button>
<body>
```

```CSS
[data-tooltip] {
  position: relative;
}

[data-tooltip]:hover::before {
  content: attr(data-tooltip);
  position: absolute;
  width: 100%;
  background-color: black;
  color: white;
  padding: .25rem;
  top: -0.5rem;
  left: 50%
  transform: translate(-50%, -100%);
}
```

## :is Selector

```CSS
:is(ul, ol) {
  ...
}
```

This selector would select anything that is an `ul` or `ol`.

## Counter

```HTML
<body>
  <h2>Intro</h2>
  <h2>Body</h2>
  <h2>Conclusion</h2>
  <ol>
    <li></li>
    ...
  </ol>
</body>
```

```CSS
body {
  counter-reset: heading;
}

h2::before {
  content: 'Part ' counter(heading, upper-roman) ': ';
  counter-increment: heading;
}

ol {
  counter-reset: outline;
}

li {
  list-style: none;
}

li::before {
  content: counters(outline, '.)
  counter-increment: outline;
}
```

## Conical gradients

```HTML
<body>
  <div></div>
</body>
```

```CSS
div {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: conix-gradient (red .25turn, blue .25turn .5turn, green .5turn)
}
```

## Background video

Nice website with free videos: [https://coverr.co/]

```HTML
<div class="bg-video">
  <video class="bg-video__content" autoplay muted loop>
    <source src="img/video.mp4" type="video/mp4" />
    <source src="img/video.webm" type="video/webm" />
    Your browser is not supported!
  </video>
</div>
```

```SCSS
.bg-video {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%; //Same as parent
  width: 100%; //Same as parent
  z-index: -1;
  opacity: 0.15;
  overflow: hidden;

  &__content {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
}
```
