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
