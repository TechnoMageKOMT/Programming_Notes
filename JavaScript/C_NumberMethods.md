# Number Methods

## .toFixed(num)

Specifies the number of decimal places.

## Math methods

Google search MDN Math. All Math methods are listed on the MDN page.

Usage:

Math.method(number)

Math.round() - Nearest integer
Math.floor() - Rounds down.
Math.ceil() - Rounds up.
Math.random() - Generates a random number between 0 and 1 (not including 1)

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
