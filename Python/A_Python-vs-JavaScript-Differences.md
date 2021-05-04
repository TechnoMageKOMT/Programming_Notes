# Python versus JavaScript Differences

## Print to screen

Py: `print()`
JS: `console.log()`

## String length

Py: `len(string)`
JS: `string.length`

## String reverse indexing

Py: Reverse indexing of strings
JS: None

## String slicing

Py: `string[start:stop:step]`
JS: `string.slice(start,stop)`

## Commenting

Py: `#`
JS: `//` and `/* */`

## Reversing a string

Py: `string[::-1]`
JS: None. Done by way of a `for loop` or using combination of string.split(), array.reverse() and array.join() methods.

## String concatenation and multiplication

Py: Both + and * operators work on strings
JS: Only +

## Uppercase and Lowercase String methods
Py: .upper() and .lower()
JS: .toUpperCase() and .toLowerCase

## .split() String method

Py: Default delimiter is a whitespace character. Otherwise works like JS
JS: Requires explicit naming of the delimeter as an argument.

## Template Literals

Py: .format() method and f-strings (formatted string literals)
Py: f-strings almost identical to JS (See string notes)
JS: Template literals

## Array vs List Add Elements

Py: .append() method
JS: .push() method

## Object Keys Syntax

Py: Must be in quotation marks.
JS: Can be entered with or without quatation marks

## Boolean values

Py: True or False (capitalised)
JS: true false (lowercase)

## Lobical operators

Py: Keywords and, or, not
JS: &&, ||, !

## Equality Operator

Py: == Strict comparison only
JS: == Value and === Type and value comparison

## else if

Py: elif
JS else if

## If statement

Py:

```Python
if some_condition:
  # code block
```

JS:

```JavaScript
if (some_condition) {
  // code block
}
```

## if else statement

Py:

```Python
if some_condition:
  # code block
else:
  # code block
```

JS

```JavaScript
if (some_condition) {
  // code block
} else {
  //code block
}
```

## if else if

Py:

```Python
if some_condition:
  # code block
elif some_other_condition:
  # code block
else:
  # code block
```

JS:

```JavaScript
if (some_condition) {
  // code block
} else if (some_other_condition) {
  // code block
} else {
  //code block
}
```