# Creating and Inserting Elements

Two methods:

- HTML string
- createElement() method

## HTML string

### innerHTML property

This is done via the innerHTML property. This then adds or render a new HTML string. **NB** Any and all html content of the parent will be replaced.

### insertAdjacentHTML() method

This will render HTML content next to existing content in a specific position. Ref MDN for all options. E.g.,

```JavaScript
div.insertAdjecentHTML('beforeend', '<p>Some text here</p>')
```

The `div` here would be any target element where the new content needs to be entered (seeMDN for all options). The downside of this method is that there is no direct way to access the content via JavaScript once it has been added/created.

## createElement()

This is then added with appendChild() or append(). This appends new DOM elements or nodes. The difference between append() and appendChild() is that append() can be used to insert a text node in addition to an element node. Append can also be used to add multiple nodes (comma seperated) at the same time. Refer MDN documnetation. Internet explorer does not support append().

There is also prepend(), before(), after() and insertBefore(), insertAdjacentElement() methods to use here. Also ref replaceChild() and replaceWith(). prepend() inserts the node at the beginning of the child nodes of the targeted element.

Refer DOM-manipulationBasics document for more information.

**NB** If an element is inserted after creation and then inserted again later in the code, the node will be moved from the first position to the new one. Remember that objects are referenced.

**NB** Always check browser support when using any of these options apart from appendChild().

## Cloning DOM elements

cloneNode() is a method available on every DOM node. This methods takes one boolean argument. true = deep clone and false is a superficial clone. I.e., no nested elements will be cloned.

## Live node lists vs static node lists

All getElementsBy.. methods yield live node lists whereas the querySelectorAll() method yields a non-live static node list.

This however does not really have any significant advantage or disadvantages.
