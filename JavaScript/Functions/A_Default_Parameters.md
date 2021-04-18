# Default Parameters

It is sometimes useful to have default values for some or all function parameters. These will then be used if the necessary arguments are not passed into the function.

In ES6 this is simply done as follows:

```JavaScript
const createBooking = function(flightNum, numPassengers = 1, price = 199){
  //some code
}
```

If value were to be passed into the function for `numPassengers` and `price`, the default values will be overwritten.

## Expressions as default values

Simple expressions can be used as default values and **importantly** any of the values for a parameter before the current parameter can also be use as default value or even inside an expression.

```JavaScript
const createBooking = function(flightNum, numPassengers = 1, price = 199 * numPassengers){
  //some code
}
```

## Skipping parameters

Parameters must always be passed to a function in the same order that they appear in the function definition. If a parameter in the middle of a list is unavailable then a value of `undefined` must be passed to the function. Using the above as example:

```JavaScript
createBooking('LH123', undefined, 1000);
```

Doing this will allow it to fall back to the default value.