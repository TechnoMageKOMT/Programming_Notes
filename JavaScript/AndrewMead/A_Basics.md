# Basics: Variables, Data Types, Operators & Functions

## Linking JavaSCript to a HTML file

### Embedded

Enter code between `<script></script>` tags either in the head section of the HTML document or within the body. Only JavaScript code must appear between the tags. **NB This method is not recommended for various reason**

### Linked as an external Script

Link a script file to the HTML file by way of the script source tag:

`<script src="script.js"></script>`

## Values, Data and Dynamic Typing

The most fundamental unit of data in JavaScript is a value.

All data are either objects of some sort (arrays, objects, sets, maps) or (everything else) primitive data types.

JavaScript is dynamically typed. I.e., Data types are determined automatically. **Very NB** Type is allocated to the value **not** the variable.

## Just In Time (JIT) Compiler

JavaScript is not strictly speaking an interpreted or compiled language. It makes use of the JIT compiler which basically interprets and compiles each line of code as encountered (This is a vast over-simplification). JIT was first implemented by Chrome in 2008.

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

- let = Mutable variable
- const = Immutable or constant variable
- var = Deprecated. Mutable. Function scoped but rest of the time global.

## Escape Character

\n = Line break character in normal strings (i.e., non-template literals)
\t = Tab
\ = In general is the escape character in strings. The character immediately after this will be escaped

## Commenting

// For inline comments
`/*` ...`*/` Block comments (`ctrl+/ in VS Code while on a line or highlighted selection)

## Operators

(`=`) Assingment  
(`*`) Multiplication  
(`/`) Division
(`+`) Addition
(`-`) Subtraction
(`%`) Modulus (Division remainder)
(`**`) Exponentiation

## Conditional Operators

=== Equal to (Strict)
(>= ) Greater than or equal to
(<= ) Less than or equal to
(> ) Greater than
(< ) Less than
(!==) Not equal to (Strict)

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

The NOT (!) operator has precedence over the && and || operators

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

## Casting of Data Types

This refers to the ability to change a variable from one type to another.

```JavaScript
let age = 46
age = String(age)
age = age.replace('6', '4')
age = Number(age)
```

## typeof Operator

The `typeof` operator returns the data type of a variable. `typeof(someVariable)` or `typeof someVariable` will return the type of the variable.

**NB** Legacy Bug: The `typeof null` or `typeof(null)` yields an 'object' result. This is a bug.

## prompt(), confirm() and alert() Methods

- prompt() - Prompts the user for some input. Any input will always be in String format
- confirm() - Returns a boollean value based on a 'OK' vs 'Cancel' response from the user
- alert() - Simple popup window with a custom string message for the user

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

If `condition` is met, then `expression1` will be returned, else `expression2` will be returned.

Because this is an operator, it leads to an expression and can be assigned to variables and/or used in template literals.

It does not replace the if/else statement where larger blocks of code are involved.

It is intended to be used where quick/short control structures/decisions are needed.

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

## Expressions vs Statements

Expression: A Piece of code that produces a value or is a value. E.g., 3 + 4; 1991; true && true && !false.

Statement: A (usually) bigger piece of code that does not produce a value, but performs an action in stead. E.g., if/else and swicth statements.

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
