# Basics: Variables, Data Types, Operators & Functions

## Linking JavaSCript to a HTML file

### Embedded

Enter code between `<script></script>` tags either in the head section of the HTML document or within the body. Only JavaScript code must appear between the tags. **NB This method is not recommended for various reason**

### Linked as an external Script

Link a script file to the HTML file by way of the script source tag:

`<script src="script.js" defer="defer"></script>`

Load scripts in the `<head>` section of the HTML file below the CSS link(s), making sure that the `defer` attribute is specified. This will download the scripts while the HTML file is being parsed and will improve performance.

If a script(s) does not rely on the DOM and needs to excecute at the beginning of the HTML page use the attribute `async`. This will however stop the parsing of the HTML document and run the script first. The order of script execution is also not guaranteed with `async`

**NB** Embedded and external script cannot be used together. If both are present, the embedded script will simply be ignored.

## Values, Data and Dynamic Typing

The most fundamental unit of data in JavaScript is a value.

All data are either objects of some sort (arrays, objects, sets, maps) or (everything else) primitive data types.

JavaScript is dynamically typed. I.e., Data types are determined automatically. **Very NB** Type is allocated to the value **not** the variable.

## Just In Time (JIT) Compiler

JavaScript is not strictly speaking an interpreted or compiled language. It makes use of the JIT compiler which basically interprets and compiles each line of code as encountered (This is a vast over-simplification). JIT was first implemented by Chrome in 2008.

## Fundamental Problem Solving

1. Ask the right question
2. Divide and conquer. Break into smaller pieces
3. Use flow charts for complex flow controls
4. Do as much research as needed before tackling the solution
5. Write pseudocode before starting the actual formal coding

Debugging Tools:

- Read and utilise error messages
- Use IDEs debugging capabilities
- Use console.log(), console.warn(). console.error()
- console.table() to view objects
- Use debugger tools in the browser browser developer console
- Insert line `debugger` in code at points of concern and the browser will jump to the debugger at that point when running the code

## 'use strict'

It is recommended to make use of the `use strict` directive at all times. This is done by adding the string`'use strict'` to the beginning of all code. This directive is to run code in "strict mode" which will:

- Avoid "silent" errors
- Code runs faster in the JavaScript engine
- Enable more secure code
- Generates additional errors in the console to aid in faster and more secure code
- Forbids certain unsafe actions.

## Variable Naming

- camelCase
- Only alphanumeric digits
- No special characters except '$' and `_`
- No JavaSCript reserved words
- May not start with a number

## Variable Declarations

- let = Mutable variable. Uses block scope (including functions).
- const = Immutable or constant variable. Uses block scope (including functions).
- var = Deprecated. Mutable. Allows variable creation in the function and global scope.

In modern JS only let and const is used. It forces the writing of cleaner code.

## Escape Character

\n = Line break character in normal strings (i.e., non-template literals)
\t = Tab
\ = In general is the escape character in strings. The character immediately after this will be escaped

## Commenting

// For inline comments
`/*` ...`*/` Block comments (`ctrl+/ in VS Code while on a line or highlighted selection)

**Good Practice** Use commenting throughout code to assist thinking process, reference when returning to code after some time has passed and also to communicate with other developers when collaborating. Commenting makes code far more readable.

The idea is that comments should add some context that is not immediately apparent.

## Operators

(`=`) Assingment  
(`*`) Multiplication  
(`/`) Division
(`+`) Addition
(`-`) Subtraction
(`%`) Modulus (Division remainder)
(`**`) Exponentiation

## Conditional Operators

(===) Equal value and type (Strict)
(==) Equal values only (type coercion)
(>= ) Greater than or equal to (type coercion)
(<= ) Less than or equal to (type coercion)
(> ) Greater than (type coercion)
(< ) Less than (type coercion)
(!==) Not equal to (Strict; value and type)
(!=) Not equal in value only (type coercion)

## Truthy and Falsy Values

Falsy values are not exactly false, but will become false when converted into a boolean. There are only 5 falsy values:
`0`
`' '` Empty String
`undefined`
`null`
`NaN`

Everything else are truthy values.

**NB** An empty object is counter-intuitively a truthy!

Explicit conversion to Boolean type is almost never done in practive. Mostly done implicitly by coersion in two scenarios

- Logical Operators
- Logical Contexts (e.g., conditional statements)

Examples:

```JavaScript
const money = 0
if (money) {
  //some code
} else {
  //some other code
}
```

or to check if a variable is defined before using it

```JavaScript
let height;
if (height) {
  //some code
} else {
  //variable not defined handling
}
```

**NB** Logical bugs are the most difficult to find because they often don't trigger error messages.

## Comparing Objects and Arrays

**CAUTION** When comparing Objects and Arrays
const obj1 = {name: 'Max'}
const obj2 = {name: 'Max'}

{name: 'Max'} === or == {name: 'Max'} --> False!
obj1.name === or == obj2.name --> True

The same applies to arrays, since they are in the end specialised Objects.

A way of thinking abput this is that even though they appear identical, they were not created identically, hence JavaSCript considers them as not equal.

## Conversion (Casting) versus Coersion

There is also == and !=. These operator converts variables behind the scenes to the same type before doing the comparison. This is called coersion and may cause unforseseen bugs. It should therefore be avoided in favour of === and !==.

Conversion on the other hand is when a programmer manually convert data from one type to another (casting).

```JavaScript
let str = '46'
str1 = Number(str)
```

Aside: If this was attempted on a string literal value, the statement will result in a NaN result. NaN stands for "Not a Number". **NB** `typeof NaN` or `typeof(NaN)` results in `number`. This is however an invalid number.

There is only three types of manual conversion:

- Number()
- String()
- Boolean() (See note under Truthy and Falsy Values above)

## Additional Operators

`++ Incremental increase`
`-- Incremental decrease`
`+= Assignment operator (x += y --> x = x + y)`
`-= Assignment operator (x -= y --> x = x - y)`
`*= Assignment operator (x _= y --> x = x * y)`
`/= Assignment operator (x /= y --> x = x / y)`
`%= Assignment operator (x %= y --> x = x % y)`

If ++ and -- appears after the operand then the value is incremented and the value before incrementing is returned. If not (i.e., before the operand) then the value is incremented and the value after incrementation is returned.

## Logical Operators

&& AND
|| OR
! NOT

The NOT (!) operator has precedence over the && and || operators

### "Boolean Tricks" with Logical Operators

#### !! Double NOT (Double Bang)

Coercion of truthy and falsy values to real true and false values using the double NOT (double bang) operator, !!. E.g., !!'' is false and !!1 is true.

#### Default Value Assignment via OR operator

E.g., const name = someInput || 'Max'. The value of 'Max' here would be assigned if someInput was a falsy value. (Remember: An OR statement is left-to-right, so the first value that is a truthy will be returned from an expression involving the || operator).

#### Use a Value If The Condition is True with the AND operator

E.g., const name = isLoggedIn && 'Max' will return 'Max' if isLoggedIn is true. If isLoggedIn is a falsy, then the falsy value will be returned.

#### "Boolean Tricks" Examples

```JavaScript
const userName = 'Johann'
const altName = ''
console.log(userName === 'Johann') //Generates boolean true
console.log(userName) //userName was not changed and still returns 'Johann'
console.log(userName || null) //userName truthy and therefore returns 'Johann'
console.log(altName || 'Johann') //altName falsy and therefore returns 'Johann'
console.log(altName || '') //Both falsy but if first is falsy then second is always returned so '' is returned
console.log(altName || null || 'Kim') //altName and null falsy so 'Kim' is returned

console.log(userName && 'Johann')//userName is truthy so 'Johann' is returned
console.log(altName && 'Johann')//altName is falsy so '' is returned (first value)
console.log(userName && '')//userName is truthy so '' is returned
```

## Operator Precedence

Refer: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence] for a table of operator precedence as well as associativity of operations. The higher the number in this table, the higher the priority. I.e., 21 will be performed before 20 etc. Associativity is the direction; i.e., right to left or left to right.

## Modulus(%) Use Case

Even number have a modulus value of 0 and odd numbers will have non-zero modulus values.

## Primitive Data Types

- String: Sequences of characters
- Number: Floating point numbers are used for both decimal and integers "behind the scene"
- Boolean: Logical true or false
- null: Empty value. Not the same as undefined (see below)
- undefined: The value of a variable that has been declared without initialisation
- Symbol: Value that is unique and cannot be change (?Natural constants)
- BigInt: Numbers larger than the Number type can accomodate

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

More than one variable can be declared in one statement. E.g., `let x, y, z`.

DRY Principle: Don't calculate a variable more than once. Store the value and then re-use as needed.

## Global variables

It is good coding practice to make use of either local or global variables (declared at the beginning of programs) as far as possible and not to hardcode actual values in the code itself. This will reduce errors and also smoothline IDE support when these values are used later in the program. [needs revision]

## Casting of Data Types

This refers to the ability to change a variable from one type to another.

```JavaScript
let age = 46
age = String(age)
age = age.replace('6', '4')
age = Number(age)
```

## typeof Operator

The `typeof` operator returns the data type of a variable. `typeof(someVariable)` or `typeof someVariable` will return the type of the variable. The output is a string in lowercase

**NB** Legacy Bug: The `typeof null` or `typeof(null)` yields an 'object' result. This is a bug.

## prompt(), confirm() and alert() Methods

- prompt(arg1, arg2) - Prompts the user for some input. Any input will always be in String format, so if a number is needed it needs to be re-cast using Number() or parseInt(). `arg1`: User prompt. `arg2`: Default value (optional).
- confirm() - Returns a boollean value based on a 'OK' vs 'Cancel' response from the user
- alert() - Simple popup window with a custom string message for the user

## Scope

JS uses lexical scope. Sometimes also referred to as static scope. I.e., Scoping is controlled by the placement of functions and code blocks. The idea is that variables are only available within the context that they have been assigned. The keyword here is code blocks.

There are three scopes. Global, function and block. Global scope is defined outside of all code blocks. Function and block scopes are defined inside code blocks and functions.

The difference between function and block scopes only becomes apparent when using `var` variables, which are function scoped, but not block scoped. `let` and `const` are Function and block scoped.

A function inside of another has access to the variables of the parent function

If access to a variable is needed outside the function or code block where it is changed, then declare the function before entering the function or code block. The declaration can be done without assigning a value to the variable.

A scope always have access to all variables from outer scopes within which it is nested (parent scopes). Outer scopes, however, never have access to variables of inner scopes. When a variable is not in a scope, it looks up the scope chain until it is found in one of the parent scopes. This is called **variable lookup**. The scope chain of variables is one way. It does not work from the outside in.

**NB** The scope chain does not have anything to do with the call stack order in the JS Engine. The call stack is constructed in the order that functions are called with the global excecution context at the bottom. This has no relevance to the scope chain.

All scoping rules also apply to arguments passed to a function. **CAUTION** If variable names are duplicated it could cause bizarre bugs because of scoping and the lexical occurence of the variables or functions containing them.

The declaration of an object is **not** a code block and therefore does not have its own scope.

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

Strings can be concatenated together with the +, concatenation operator, and variables can be inserted in strings using the same. The result of such a concatenation is called a **string literal**. Be mindful of type coersion when concatenating strings with the concatenation operator when numbers are present. I.e., Make sure all variables are of the String type and if not then cast any non-String variables to String before the concatenation

```JavaScript
const temp = 37
'The current tmeparature is ' + temp + 'degrees celcius.';
```

A better and more modern way of achieving the same task is to use **template literals**:

```JavaScript
const temp = 37
`The current temperature is ${temp} degrees celcius`
```

Template literals also allow multiline strings. So:

```JavaScript
const str = `String with
              multiple
              lines`
```

Be mindful of concatenation anomallies like: 2 + 3 + 4 + '5'; which will result in 95.

## Conditional Statements (if/else) Control Structure

### General structure

```JavaScript
if (conditional statement) {
  //Some code
} else {
  //Some code
}
```

Or multiple chained statements

```JavaScript
if (conditional statement) {
  //Some code
} else if (conditional statement2) {
  //Some code
} else {
  //Some code
}
```

Should global access be required for any variable used inside the code **block** of the statement, declare the variable(s) before starting the if/else statement.

### Ternary Operator

```JavaScript
condition ? expression1 : expression2
```

If `condition` is met, then `expression1` will be returned, else `expression2` will be returned. The condition can have multiple logically (&&, ||,!) connected conditions just like if statements can.

Because this is an operator, it leads to an expression and can be assigned to variables and/or used in template literals.

It does not replace the if/else statement where larger blocks of code are involved.

It is intended to be used where quick/short control structures/decisions are needed.

**NB** Can be chained/nested just like if/else..if. Deeply nested expressions should be avoided in favour of traditional if statements.

```JavaScript
condition1 ? expression1 : condition2 ? expression2 : expression3
```

## Switch Statements

When the number of conditional statements in a if/else chain gets too long, the switch statement can serve as an handy alternative:

```JavaScript
switch (expression) {
  case x:
    //code block
    break;
  case y:
    //code block
    break;
  default:
    //code block
}
```

The expression is evaluated once and its value is then compared against each case until it finds a match.

Switch versus if

If the condition is a simple equality (===) check with numerous cases then use switch. If the condition involves more complex combinations of logical operators, rather use if.

**NB** If `break` statement is left out of a switch statement, all the code below it will be executed without checking any of the cases (conditions).

## Expressions vs Statements

Expression: A Piece of code that produces a value or is a value. E.g., 3 + 4; 1991; true && true && !false.

Statement: A (usually) bigger piece of code that does not produce a value, but performs an action in stead. E.g., if/else and swicth statements.

Having said that, all expressions are also statements, but not the otherway around.

The distinction between the two is important because JavaScript expects them in different places. For example, a template literal only accepts expressions and not statements.

Aside: Statement and declaration is synonymous in JavaScript

## Functions

DRY Principle - Don't Repeat Yourself.

Functions are re-usable pieces of code that take care of repetitive tasks (code) within a program. The terms invoking, calling, or running are all equivalent statements for the excecution of a function.

Parameters: Represent input data. Within the function these are used as variables.
Arguments: Actual values passed to a function's parameters during a particular invocation of the function.

A function may or may not have parameters depending on its purpose.

When a value is returned by the invocation, it is common practice to "capture" the value by storing it in a variable defined outside of the function.

### Function Declaration Structure

```JavaScript
  function functionName (parameters) {
    //code block
  }

  const someVariable = functionName(arguments)
```

### Function Expression

```JavaScript
  const functionName = function (parameters) {
    //code block
  }

  const someVariable = functionName(arguments)
```

### Arrow Function

```JavaScript
  const functionName = (parameters) => {
    //code block
  }

  const someVariable = functionName(arguments)
```

Cannot be used as methods in objects or constructor functions or anywhere where `this` keyword is applicable. I.e., Do not have argument objects or `this`.

### Difference: Declaration vs Expression

Declaration:

- Can be invoked before the declaration (hoisting)

Expression

- Can be used anywhere an expression can be used
- Must be declared before invocation. (no hoisting)
- Arrow functions are abbreviated function expressions
- A value is implicitly returned so there is no need for an explicit return statement.

### Undefined Returned

- Parameters are specified, but no arguments are passed in
- No return value is specified and the "value" of the function is assigned to a variable when invoked

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

Refer: Seperate dedicated Strings document.

## For loops

```JavaScript
for (let i = 0; condition; i + 1) {
  //code block
}
```

- Step 1: Initialisation of "counter" variable
- Step 2: Boolean conditional statement (be mindful of infinite loops)
- Step 3: Incremental increase of "counting" variable
- Step 4: Code block to be excecuted. Has access to current value of i to use in this excecution

Looping through arrays are one of the most frequent uses of for loops. Loop iteration can even be used to create new arrays.

```JavaScript
const array1 = [var1, var2, var3,..., var4]
const array2 = []

for (i = 0; i < array1.length; i++) {
  array2.push(newValue/expression) (1)
}
```

An alternative to (1) is `array2[i] = newValue/expression`, but (1) should be used as far as possible in the interest of clean code.

**Local Scope** `i` is locally scoped to its for loop, so the variable name can be used for all for loops in a program except for nested for loops in which case additonal j,k,l would be used.

### Continue or Break

```JavaScript
for (let i = 0; i < array.length; i++) {
  if (conditional statement) {
    continue
  } else {
    //code block
  }
}
```

`continue`: If condition is `true` then exit/bypass the rest of the current iteration and continue with the next iteration.
`break`: Stop/break the current iteration and exit the loop completely without any further iterations.

#### Labelled Statements

```JavaScript
let j = 0
  outerWhile: do {
    console.log('Outer', j)
    innerFor: for (let k = 0; k < 5; k++){
      if (k === 3) {
        break outerWhile
      }
      console.log('Inner', k);
    }
    j++
  } while (j< 3)
```

This can be used with any statemen. Both the `break` and `continue` can be used.  

### Looping backwards

```JavaScript
for (let i = array.length -1; i >= 0; i--) {
  //code block
}
```

### Nested loops

```JavaScript
for (...) {
  for (...){

  }
}
```

### for-of loop

Excecutes for every element in an array. (**NB Arrays or Strings only**)

```JavaScript
for (const el of array {
  console.log(el)
})
```

### for-in loop

Excecutes for every key in an object.

```JavaScript
for (const key in obj) {
  console.log(key)
  console.log(obj[key])
}
```

## While Loops

General case:

```JavaScript
while (conditional statement) {
  //code block
}
```

It is more versatile than the for loop because it does not really need a counter at all.

Example. Roll a dice until a 6 is encountered then stop

```JavaScript
let dice = Math.trunc(Math.random() * 6) + 1

while (dice !== 6) {
  //code block
}
```

While loops are generally used when the number of iterations are unknowable and for loops when dealing with known or finite iterations (e.g., arrays).

## do wgile Loops

Excecutes the code block before the conditional statements.

```JavaScript
do {
  //code block
} while (conditional statement)


### Constructor Functions and Objects

These function are used to create objects:

```JavaScript
function SomeName(var1, var2, var3, var4){
  this.var1 = var1;
  this.var2 = var2;
  this.var3 = var3;
  this.var4 = var4;
  this.someFunction = function(){
    //statement / expression
  }
}
```

**Sidenote** By assigning a value to a object property, one is simply creating a variable associated with that object

```JavaScript
const objectName = new SomeName(value1, value2, value3, value4);
```

Take note of the `new` keyword that must precede the name of the constructor when invoked. Another difference is that the **function name starts with a capital**, unlike normal functions.

To call the method in this object:

```JavaScript
SomeName.someFunction();
```

Constructor functions are what is behind JS's methods. Refer to drumkit project:

```JavaScript
let crash = new Audio("sounds/crash.mp3");
crash.play();
```

This is clearly a new object that is being created by the Audio constructor function that has a function called play within it which is invoked in the second line.

### Methods

Functions that belongs to or form part of objects are called methods. To call the method, dot notation is used as with all object properties. `object.method()`. Methods can also be incorporated into constructor functions. See in the constructor function example above.

## JavaScript Behind The Scenes

The JavaScript engine is a program written in C++ that excecutes JavaScript code. Chrome uses V8 and Firefox uses SpiderMonkey. Node.js and Express can build server side applications outside of the browser.

Some important aspects of JavaScript

- Functions are simply treated as variables, so they can be passed into other functions or even returned by functions
- Dynamic typing: Type only becomes known at runtime
- Dynamic typing: Data types of variables can be changed automatically/dynamically when assigning a new value to a variable
- **NOT** an interpreted language: Just-in-time (JIT) compilation is a combination between interpretation adn compilation.
- The 'Heap" is 'long-term memory' and the 'Stack' is 'short-term memory'

### Excecution Context

- Variable environment
- Scope chain
- `this`Keyword

### Hoisting

Hoisting makes some variables and functions available before they have been declared. This is a common cause of difficult to find bugs. Commonly there are undefined returns instead of errors when hoisting takes place which makes the errors difficult to detect.

To avoid hoisting problems:

- Do not use `var` variable declarations
- Use `const` as far as possible
- Use `let` only when definitely mutable
- Keep code as immutable as possible
- Declare variables at the top of each scope
- Always define functions before invoking them

One of the dangers of using `var` to declare variables is that it creates a property with that value on the `window`object.

### window Object

The `window` object is the global object of JavaScript in the browser.

### this Keyword

- Special variable created for every excecution context (functions)
- Takes the value of (points to) the "owner" of the function in which the `this` keyword is used
- `this` Is **not** static. It depends on how the function is called and its value is only assigned when the functio is actually called
- Methods: `this` points to the object that is calling the method
- Simple function calls: `this` is undefined
- Arrow functions: Don't own `this`. `this` points to the parent function or `window` object if there isn't one
- Event listeners: `this` Points to the DOM element that the handler is attached to.
- `this` Outside of any function points to the `window` object
- Never use arrow functions as methods even if `this` keyword is not used

#### Method borrowing and this

```JavaScript
const jonas = {
  year: 1991,
  calcAge: function (){
    console.log(this)
  }
}

const matilda = {
  year: 2017,
}

matilda.calcAge = jonas.calcAge//Method borrowing
```

Even though `this` keyword was copied with the method, it will point to the `matilda` object if called. This is an example that the `this` keyword is dynamic and depends on how the function is called.

#### A function inside of a method

Still regular function and `this` is therefore undefined.

There are two solutions:

1. Declare a variable called `self` outside of the inner function and set it equal to `this`. Then replace all instances of `this` with self in the inner function.
2. Use an arrow function as the inner function. It does not have its own `this` keyword and inherits it from the parent scope. `this` Would therefore point to the method that it is embedded in.

### arguments Keyword

Not really used in modern JavaScript anymore, but may appear in old code.

Only regular functions gets the `arguments` keyword. I.e., Function declarations and function expressions.

The `arguments` keyword produces an array of the arguments passed to the function. It is useful when a function needs to take in more variables/arguments than initially specified.

The arrow function does not have the `arguments` keyword.

### Memory handling of primitive vs reference data types

Reference data types are:

- Object literals
- Arrays
- Functions
- Sets
- Maps
- etc

All reference types are stored in the memory 'Heap' of the JS Engine. Primitive types are stored in the 'Call Stack' within the excecution context in which they were declared.

Whenever an object or reference type is copied, there is merely the creation of a new variable that points to the same object in the memory "Heap'. Any changes to the object will therefore be reflected by both the original and "copied" variables.

Example:

```JavaScript
const me = {
  name: 'Jonas',
  age: 30,
}

const friend = me
friend.age = 27

console.log(me.age) --> 27
console.log(friend.age) --> 27
```

To create a real, but superficial, copy of an object, a function called `Object.assign()` must be used. This essentially merges two objects and returns a new one. Syntax: `const newObject = Object.assign({}, oldObject)`. This works, however, only on the first level. I.e., If there are objects such as arrays or other objects embedded in the original object then the above behaviour would persist for the embedded items. The only solution is to create a 'deep clone' which is very complex and requires the use of external libraries.

## Sorting a number array

```JavaScript
array.sort(function(a, b){
  return a - b
})
```

## Set timeout

`setTimeout(function(),milliseconds)`

Useful for animation on added class which can be removed after a set time. A square or button etc can then be pressed and returned to its previous state as if it flashes or jumps back (depending on the styling)

## Whitespace

JavaScript ignores whitespace, so it is good practice to make use of whitespace for readability. The removal of all whitespace is called minimizing.

## Not defined versus undefined

Not defined: Does not exist. I.e., Not declared.
undefined: Exists (i.e., declared) but no value has been assigned to it

## IIFE - Immediately Invoked Function Expressions

These functions are excecuted immediately without being called. The generic format is:

```JavaScript
(function functionName(){
  //code block
})()
```

## forEach() method

```JavaScript
array.forEach(function(currentValue, index){
  //code block
})
```

This invokes the function for each element in the iterable.
