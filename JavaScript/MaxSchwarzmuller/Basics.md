# Basics: Variables, Data Types, Operators & Functions

## Linking JavaSCript to a HTML file

### Embedded

Enter code between `<script></script>` tags either in the head section of the HTML document or within the body. Only JavaScript code must appear between the tags. **NB This method is not recommended for various reason**

### Linked as an external Script

Link a script file to the HTML file by way of the script source tag:  

`<script src="script.js"></script>`

## Variable Naming

- cameCase
- Only alphanumeric digits
- No special characters except $ and _
- No JavaSCript reserved words
- May not start with a number

## Variable Declarations

- let = Mutable variable
- const = Immutable or constant variable
- var = Deprecated. Mutable. Function scope but rest of the time global.

## Escape Character

\n = Line break character in normal strings (i.e., non-template literals)
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

(===) Equal to (Strict)
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

## undefined versus null

undefined = A value has never been assigned to a variable.
null = The value of a vairiable was reset by the developer.

## Data Structures

- Function
- Arrays
- Objects
- Sets
- Maps
- Classes

## Variables

Variables are "data containers" in which data is "stored" for re-use during the excecution of a program. The data may change if declared as `let` or `var` variables, but not if declared as `const`.

Variables can be declared and initialise at the same time or in the case of `let` and 'var` variables can be declared without initialisation.

## Scope

JS uses lexical scope. Sometimes also referred to as static scope. The idea is that variables are only available within the context that they have been assigned. The keyword here is code blocks.  

There are two scopes. Global and Local. Global scope is defined outside of all code blocks. Local scopes are defined inside code blocks.

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

Strings can be concatenated together with the +, concatenation operator, and variables can be inserted in strings using the same:

```JavaScript
const temp = 37
'The current tmeparature is ' + temp + 'degrees celcius.';
```

A better and more modern way of achieving the same task is to use **template literals**:

```JavaScript
const temp = 37
`The current temperature is ${temp} degrees celcius`
```
