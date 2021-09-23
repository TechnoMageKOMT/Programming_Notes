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

```CSS
@mixin someName {
  selector {
    /*code*/
  }
}
```

Inclusion in sass stylesheet:

```CSS
@include someName
```

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

## :is Selector

```CSS
:is(ul, ol) {
  /*code block*/
}
```

This selector would select anything that is an `ul` or `ol`.

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

## Forms

Font-family and color is not inherited, so always specify the value to fit in with the rest of the page. Simply set the value to `inherit`.

:focus states. Set the outline to none, but always specify a box shadow and border-bottom for users that acess the site without a mouse. I.e., with a keyboard only. This is done for accessibility reasons.

`autocomplete="off"` This is an HTML attribute on input fields that will disable annoying autocomplete popup/dropdown lists.

### Validation

With :valid and :invalid pseudoclasses. The example will for example underline the code with an orange color while incorrect.

```SCSS
&:focus:invalid {
  border-bottom: 3px solid $color-secondary-dark;
}
```

## Responsive padding and margins

The following code will set a padding top and bottom to the second smaller value if the viewport shrinks below the first.

```SCSS
selector {
  padding-block: min(10vh, 10rem)
}
```

## :target pseudoclass

As soon as the element becomes the target when the matching anchor is clicked, the pseudoclass `:target` becomes available.

## Media query breakpoints

EM's and REM's in media queries do not reference the root font-size but rather that of the user's browser. REM's additionally cause problems with some browsers, so EM's are the unit of choice with media queries.

- 0 - 600px (37.5em) Phones
- 600 - 900px (56.25em) Tablets portrait
- 900 - 1200px (75em) Tablets landscape
- 1200 - 1800px Desktop - normal code. No media queries
- 1800 - (112.5em) Big desktops

## Media Query Manager with SASS mixins

```SCSS
//The following type of code is used in the mixin file. See further down below how this will be used.

//Media Query Manager
/*
0   - 600px     Phone
600 - 900px     Tablet portrait
900 - 1200px    Tablet landscape
1200 - 1800px   Normal desktop styles
1800 -          Big desktop

Breakpoint argument choices
- phone
- tab-port
- tab-land
- big-desktop
*/
@mixin respond($breakpoint) {
  @if $breakpoint == phone {
    @media (max-width: 37.5em) {
      //600px
      @content;
    }
  }
  @if $breakpoint == tab-port {
    @media (max-width: 56.25em) {
      //900px
      @content;
    }
  }
  @if $breakpoint == tab-land {
    @media (max-width: 75em) {
      //1200px
      @content;
    }
  }
  @if $breakpoint == big-desktop {
    @media (min-width: 112.5em) {
      //1800px
      @content;
    }
  }
}
```

```SCSS
//Usage of mixin media query manager

html {
  font-size: 62.5%;

  @include respond(tab-land) {
    font-size: 56.25%; //1rem = 9px, 9/16 = 56.25%
  }

  @include respond(tab-port) {
    font-size: 50%; //1rem = 8px, 8/16 = 50%
  }

  @include respond(phone) {
    font-size: 30%; //1rem = 4.8px 4.8/16 = 30%
  }

  @include respond(big-desktop) {
    font-size: 75%; //1rem = 12px, 12/16 = 75%
  }
}
```

## Outline offset

This property can be used to frame an image or div. A negative value will actually create an inset that looks great with images.

## General order of tackling responsiveness changes once a site has been coded

1. Base and typography
2. General layout
3. Grid
4. Page layout
5. Components

## Smooth scrolling

```CSS
html {
  scroll-behaviour: smooth;
}
```
