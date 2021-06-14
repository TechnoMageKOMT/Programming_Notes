# Traversing the DOM

Using the traversal properties (methods) is faster and more efficient when a specific element is already selected and should serve as the anchor for moving within the DOM. These methods are also faster for the browser than using querySelector because querySelector has to parse the document to find the target nodes. NB! Deeply nested DOM traversal methods will not perform any better and could potentially make performance worse.

## element.children

Will produce an array like object of all child **element** nodes of the parent. I.e., This will exclude any text nodes.

## element.childNodes

This will produce a nodelist type object that will include **element and text** nodes. These text node includes any white space and line breaks in the HTML document. Aside: White space by default is not rendered by browsers, but there is a CSS property `white-space: pre` that will overide the default setting and render any white space in the HTML document. This selection method is very rarely used since one normally wants only the elements to work with which is covered by `element.children`.

## element.firstChild and element.firstElementChild

The first selects the first node regardless of whether it is a text or element node and the latter selects the first element node.

## element.lastChild and element.lastElementChild

Similar but last nodes.

## element.parentNode and element.parentElement

The first selects the nearest parent node and the second to the nearest parent element. In almost all cases these are equivalent because the way that the DOM is structured only allows for one parent and that is almost always an element. Text nodes for instance cannot have child nodes. The one exception is document.documentElement.parentElement which is null with document.documentElement.parentNode targeting the document. There is however no use case for this since it is easier to just target the document object directly.

## element.closest('') method

Allows the selection of the nearest ancestor that satisfies the CSS selector entered as an argument between ''.

## element.perviousSibling and previousElementSibling

The first would give the previous sibling node (text or element) and the latter will only give element nodes.

## element.nextSibling and element.nextElementSibling

Same but for the next sibling.

