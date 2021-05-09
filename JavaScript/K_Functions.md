# Functions

## Definitions

Functions are code on demand.  

Variables and constants created in functions "belong" to that function.  

Functions MAY take parameters (arguments) and MAY return a value.  

Functions can be called multiple times (with different arguments).  

Functions can be called "directly" or "indirectly". Directly when using () and indirectly when binding a function to an event listener.  

## Objects

Functions are objects themselves and everything that applies to objects apply to them. They are stored in the 'Heap" for example just like any other objects.

## Function Declaration vs Expression

- Declaration: Hoisted to top and initialised. It can therefore be declared anywhere in the file.
- Expressions: Hoisted to top of file but NOT initialised/defined. Must be defined before it is used.

## Naming of anonymous functions

This may be useful for trouble-shooting because the function name will appear in the browser error code. So event handlers for instance can be declared as follow:

```JavaScript
someButton.addEventListener('click', function functionName () {
  //code block
})
```

## Arrow functions

If an arrow function has only one expression in it, the 'return' {} can be left out and the expression can be stored directly in a variable:

```JavaScript
const getWinner = (cChoice, pChoice) => {
  cChoice === pChoice
    ? RESULT_DRAW
    : (cChoice === ROCK && pChoice === PAPER) ||
      (cChoice === PAPER && pChoice === SCISSORS) ||
      (cChoice === SCISSORS && pChoice === ROCK)
    ? RESULT_PLAYER_WINS
    : RESULT_COMPUTER_WINS

or

const add = (a, b) => a + b
```

The general syntax:

```JavaScript
(parameter1, parameter2) => {...}
() => {...} //If no parameters
parameter => {...} //If only one parameter
(a, b) => a + b //If only one expression in the body
const loadPerson = pName => ({name: pName}) //Extra parenthesis if object is returned
```

## Default Arguments

Default arguments are simply set by setting the parameters in the function definition equal to the required default values:

```JavaScript
const someFunction = function (par1=a, par2=b, par3) {
  //code block
}
```

NB: It does not matter in what order the parameters with defaults are listed. They can be before, after or between paramters that do not have default values.

## Rest parameter

The rest parameter takes in the applicable arguments and places them into an array.

```JavaScript
const someFunction = function (...numbers) {
  //code block
}

someFunction(a,b,c,d,e,f)
```

`numbers` Will be an array within the function with the elements passed as arguments. If the rest parameter appear together with "normal" arguments then it should ALWAYS be at the end of the list since it will 'consume' all remaining arguments in the list. For the same reasons there can only be one rest parameter per function.