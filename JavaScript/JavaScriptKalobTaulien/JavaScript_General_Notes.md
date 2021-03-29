# General JavaScript Notes 

## Hoisting

This is JavaScripts general behaviour of moving a variable to the top of its scope while still undefined. (? Jonas Schmedtmann for deeper discussion.  

## Getting Input Values from DOM Events

Example. Note dot notation for future reference.

```JavaScript
const input = document.querySelector('.js-name');
const nameEvent = document.querySelector('.js-change-name');

input.addEventListener('keyup', function(e){
  nameEvent.textContent = e.target.value;
} )
```

Also note that the function here is a technically called a callback function. It is therefore only called (back) once the specified event is detected. The following code would have been equivalent for clarification.

```JavaScript
input.addEventListener('keyup', keyPress);

function keyPress(e){
  nameEvent.textContent = e.target.value;
}
```

