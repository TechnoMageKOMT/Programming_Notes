# JavaScript In The Browser

## DOM Manipulation

```JavaScript
const p = document.querySelector('p');
p.remove()
```

The remove() method with no specified arguments removes the entire targeted 'p' element from the DOM.

The rest of the material was revision of already covered material in other courses.

## Adding Elements Via The Dom

Three steps

- Create the new element
- Update it's content
- Insert the element

Example:

```JavaScript
const newParagraph = document.createElement('p');
newParagraph.textContent = `This is a new element from JavaScript`;
document.querySelector('body').appendChild(newParagraph);
```

This code would insert the new paragraph element at the end of the body section of the DOM (I.e., as last child).

## User interaction

Additional option for selecting a specific target when there is more than one that fits the selector. Using querySelectorAll together with bracket notation for the array that is returned.

```JavaScript
document.querySelector('button')[1].addEventListener('click', function(){
  //some code 
})
```

This method is not recommended because it lacks specificity. 

Ways of targeting elements

--Single--  
`p` - By HTML tag  
`#id` - By id  
`.class` - By class  
--Multiple--  
`p#id` - Element that has both  
`button.inventory` - Element that has both  
`h1#title.application`- Element that has all three  

