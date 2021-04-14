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

To generate a random number between two specific values:

```JavaScript
let min = 10;
let max = 20;
let randomNum = Math.floor(Math.random() * (max - min + 1)) + min;
```
