# Number Methods

## .toFixed(num)

Specifies the number of decimal places.

## Math methods

Google search MDN Math. All Math methods are listed on the MDN page. In VS Code Math. ctrl spacebar will list all math methods as well.

Usage:

Math.method(number)

Math.round() - Rounded to the nearest integer
Math.floor() - Rounds down.
Math.ceil() - Rounds up.
Math.random() - Generates a random number between 0 and 1 (not including 1)
Math.abs() - Returns the absolute value

Math is a JavaScript object that has numerous methods defined in it (see MDN list). 

To generate a random number between two specific values:

```JavaScript
let min = 10;
let max = 20;
let randomNum = Math.floor(Math.random() * (max - min + 1)) + min;
```

## toFixed() method

Method to fix the decimal points of a number.

```JavaScript
const num = 5.56789
const newNum = num.toFixed(2)
```

This will return a newNum value of 5.57. If no number is specified as an argument then the default of 0 will be used.

## parseInt() method

Converts strings to integers. `parseInt(stringVariable)`. If the string is not a number then NaN is returned.

## parseFloat() method.

Converts strings to floating (decimal) point numbers. `parseFloat(stringVariable)`

## toString() method

Converts numbers to strings. `numberVariable.toString()`

## Using + to convert strings to numbers

A string variable can also be prefixed with a + sign to convert it to a number. The methods above are better for readability and also offers much finer control. `+stringVariable`

## Mixing strings and numbers

3 + '3 => '33'
'Hi' - 'i' => NaN
3 * '3' => 9 (the number; not a string) 
3 - '3' => 0
3 / '3' => 1

## isNaN() function and Number.isNaN() method

`isNaN()` function: Converts the variable to a number and then tests if it is NaN. Returns true if the value is NaN (Recommended)
`Number.isNaN()` method: Returns true if the value is of the type Number and equates to NaN. Otherwise it returns false. It does not convert the value to a Number and will not return true for any value that is not of the type Number.
