# Working notes

## Functions

## Shadowed variables

When a variable is declared globally as well as inside a function. I.e., The same variable name. The variable inside of the function is handled independant of the global one. This behaviour is called shadowing:

```JavaScript
let userName = 'Max'
function greetUser (name) {
  let userName = name
  alert(userName)
}
userName = 'John'
greetUser('Max')
```

This code will show an alert that says 'Max' not 'John'

## Return statement

Any statement after the return statement in a function will not excecute. I.e., The return statement ends the function excecution. The `return` keyword can actually be used on its own in a function to exit the function excecution. This would usually be linked to some conditional statement.

## Executing functions "indirectly"

An example of this would be a callback function that is used during DOM manipulation.

```JavaScript
const defaultResult = 0
let currentResult = defaultResult

function add() {
  currentResult = currentResult + userInput.value
  outputResult(currentResult, '')
}

addbtn.addEventListeners('click', add);
```

Note the "callback" defined by the function name `add` without the arguments parenthesis.

This is done when a function should only be excecuted at some future point when, in this case, a click event occurs.
