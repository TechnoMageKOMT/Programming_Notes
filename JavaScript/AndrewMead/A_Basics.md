# Basics: Variables, Data Types, Operators & Functions

## Linking JavaSCript to a HTML file

### Embedded

Enter code between `<script></script>` tags either in the head section of the HTML document or within the body. Only JavaScript code must appear between the tags. **NB This method is not recommended for various reason**

### Linked as an external Script

Link a script file to the HTML file by way of the script source tag:  

`<script src="script.js"></script>`

## Variable Naming

- camelCase
- Only alphanumeric digits
- No special characters except $ and _
- No JavaSCript reserved words
- May not start with a number

## Variable Declarations

- let = Mutable variable
- const = Immutable or constant variable
- var = Deprecated. Mutable. Function scoped but rest of the time global.

## Escape Character

\n = Line break character in normal strings (i.e., non-template literals)
\t = Tab
\ = In general is the escape character in strings. The character immediately after this will be escaped

## Commenting

// For inline comments
/*...*/ Block comments (`ctrl+/ in VS Code while on a line or highlighted selection)

## Operators

(=) Assingment  
(*) Multiplication  
(/) Division
(+) Addition
(-) Subtraction
(**) Exponentiation

## Conditional Operators

===  Equal to (Strict)
(>= ) Greater than or equal to
(<= ) Less than or equal to
(>  ) Greater than
(<  ) Less than
(!==) Not equal to (Strict)

There is also == and !=. These operator converts variables to the same type before doing the comparison. This is called coersion and may cause unforseseen bugs. It should therefore be avoided in favour of === and !==.

## Primitive Data Types

- Strings
- Numbers
- Booleans
- null
- undefined
- Symbol
- BigInt

## undefined versus null

undefined = A value has never been assigned to a variable.
null = The value of a vairiable was reset by the developer and/or some code.

## Data Structures

- Function
- Arrays
- Objects
- Sets
- Maps
- Classes

## Variables

Variables are "data containers" in which data is "stored" for re-use during the excecution of a program. The data may change if declared as `let` or `var` variables, but not if declared as `const`.

Variables can be declared and initialised at the same time or in the case of `let` and `var` variables can be declared without initialisation.

## Scope

JS uses lexical scope. Sometimes also referred to as static scope. The idea is that variables are only available within the context that they have been assigned. The keyword here is code blocks.  

There are two scopes. Global and Local. Global scope is defined outside of all code blocks. Local scopes are defined inside code blocks.

There is also function and blocked scoped. A block being any code between a set of {}. The difference between the two only becomes apparent when using `var` variables, which are function scoped, but not block scoped.

## Leaked Scope

Variables should **always** be declared and/or initialised before they are used.

```JavaScript
if (true){
  if (true) {
    name = `Jen`;
    console.log(name);
  }
}

if (true) {
  console.log(name);
}
```

In this case when a variable assignment is encountered. JS will go up the scoping chain and if not found will automatically declare a global scope for the variable in question.

This can cause some unforseen and difficult to detect bugs and should be avoided at all cost.


## Function scopes

All same rules applies but it is important to remember that the arguments are also part of the function's local scope and does therefore not form part of the global scope.

There can also be local scopes nested within a function if there are for instance if statements within the function.

## String Concatenation vs Template Literals

Strings can be concatenated together with the +, concatenation operator, and variables can be inserted in strings using the same. The result of such a concatenation is called a **string literal**.

```JavaScript
const temp = 37
'The current tmeparature is ' + temp + 'degrees celcius.';
```

A better and more modern way of achieving the same task is to use **template literals**:

```JavaScript
const temp = 37
`The current temperature is ${temp} degrees celcius`
```

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

Note the "callback" function, defined by the function name `add` without the arguments parenthesis.

This is done when a function should only be excecuted at some future point when, in this case, a click event occurs.

## Strings

### Access individual characters

Individual characters can be accessed with bracket notation. So:

```JavaScript
const str = 'String';
const firstCharacter = '';
firstCharacter = str[0];
```

The value of `firstCharacter` in this code would be 'S'.

### Return last character

```JavaScript
const str = 'String';
const lastCharacter = '';
lastCharacter = str[str.length - 1];
```

The '.', or dot, is called the property access operator.

## Arrays

Individual elements are accesed by bracket notation just like strings. The .length property also applies.

To access three dimensional arrays (arrays within arrays), the first set of brackets refers to the entries in the outer-most (first-level) array, and each individual pair of brackets refers to the next level of entries inside.

```JavaScript
const arr = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
  [[10, 11, 12], 13, 14]
];

arr[3] is [[10, 11, 12], 13, 14]
arr[3][0] is [10, 11, 12]
arr[3][0][1] is 11
```

See "Array Methods" file for more detailed information on array methods.