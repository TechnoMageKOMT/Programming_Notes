# Functions

## Definitions

Functions are code on demand.

Variables and constants created in functions "belong" to that function.

Functions MAY take parameters (arguments) and MAY return a value.

Functions can be called multiple times (with different arguments).

Functions can be called "directly" or "indirectly". Directly when using () and indirectly, for example, when binding a function to an event listener.

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

If an arrow function has only one expression in it, the 'return' and {} can be left out and the expression can be stored directly in a variable:

```JavaScript
const getWinner = (cChoice, pChoice) =>
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
const loadPerson = pName => ({name: pName}) //Extra parenthesis if object is returned. To distinguish object{} from function block{}
```

## Default Arguments

Default arguments are simply set by setting the parameters in the function definition equal to the required default values:

```JavaScript
const someFunction = function (par1 = a, par2 = b, par = 3) {
  //code block
}
```

NB: It does not matter in what order the parameters with defaults are listed. They can be before, after or between parameters that do not have default values.

NB: When passing arguments to a function with default parameters. If the "missing" variable is before or in between actual arguments, then the keyword `undefined` must be passed.

```JavaScript
someFunction(undefined, someValue, anotherValue)
```

## Rest parameter

The rest parameter takes in the applicable arguments and places them (or packs them) into an array. For example:

```JavaScript
const someFunction = function (...numbers) {
  let sum = 0
  for (const num of numbers) {
    sum +=num
  }
  return sum
}

someFunction(1, 5, 10, -3, 6, 10)
```

`numbers` Will be an array within the function; with the elements passed as arguments. If the rest parameter appear together with "normal" arguments then it should ALWAYS be at the end of the list since the rest parameter will 'consume' all remaining arguments in the list. For the same reasons there can only be one rest parameter per function.

## Legacy code: arguments parameter

There is a keyword in pre-ES6 JavaScript that serves a similar function as the rest parameter. The keyword is `arguments`. For example:

```JavaScript
const subtract = function () {
  let sum = 0
  for (const num of arguments) {
    sum -= num
  }
  return sum
}
```

`arguments` Is an array-like object that also contains all the arguments passed to the function. It is ONLY available to functions declared with the `function` keyword. I.e., Arrow function do not have their own `arguments` keyword.

From ES6 onwards this is replaced by the rest operator and `arguments` should no longer be used. It is only included here because it may appear in older code.

## Creating Functions Inside of Functions

Functions created inside other functions are only available inside the parent function. Example:

```JavaScript
const sumUp = (a, b, ...numbers) => {
  const validateNumber = (number) => {
    return isNaN(number) ? 0 : number
  }

  let sum = 0
  for (const num of numbers) {
    sum += validateNumber(num)
  }
  return sum
}
```

In most cases it is, however, better for functions to have global scope so even thought there are use cases for functions inside of functions, it is relatively rare. This will be discussed in greater length when dealing with code performance.

## Callback Functions

This is effectively passing a pointer to a function to another function. Many of the built in JavaScript functions require a callback function.

The following is an example of a manually written callback function (I.e., not a built in function):

Add a new function: "checkInput" which takes an unlimited amount of arguments (unlimited amount of strings) and executes a callback function if NO argument/ string is an empty string.

```JavaScript
function checkInput(cb,...strings) {
  let hasEmptyStrings = false
  for (const item of strings) {
    if (!item) {
      hasEmptyStrings = true
      break
    }
  }
  if (!hasEmptyStrings) {
    cb()
  }
}

function noEmptyStringHandler () {
  console.log(`Has no empty or null strings`);
}

checkInput(noEmptyStringHandler, 'Hello', 'World', 'Tester', 'Strings')

```

## Working with bind()
