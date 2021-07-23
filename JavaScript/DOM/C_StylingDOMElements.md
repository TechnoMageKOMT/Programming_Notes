# Styling DOM Elements

## .style Property

This is the main way of targetting individual CSS styles on an element. Controls styles as inline styles on the element. I.e., Has the highest specificity/priority in CSS. It will therefore override any other styles in the style.css file. Style names are same as in CSS but where there are hyphenated words, these are turned into the camel case equivalent forms.

## .className Property

Another way of using JavaScript to style individual elements is to dynamically set /control classes on an element. The property takes a space seperated string where the string is all the classes of the element. This is an easy way of removing all classes on an element. `element.className = ''`

## .classList property

A JavaSCript object with a set of built in methods. `.add`, `.remove`, `.toggle` etc. This gives fine grained control over classes that are added. It can also be used in conjunction with `.className`.

## Good practice

Keep all styling in the style.css(s) file and use JavaScript to dynamically add or remove the styles as needed.
