# Objects

Objects are variables that contains unordered data that is structured into key:value pairs

## Create an object

```JavaScript
const objectName = {
  property1: value1,
  property2: value2,
  property3: value3,
}
```

## Reading value of a property

Values can be retrieved or read by either bracket ([]) or dot (.) notation. Dot notation is usually favoured with bracket notation reserved for situations when the value in the brackets needs to be an expression

```JavaScript
console.log(objectName.property1)

concsole.log(objectName['keyName'])
```

## Change value of a property

```JavaScript
objectName.property = valueAlternative
```

## Passing an object into a function

```JavaScript
let myBook = {
  title: `1984`,
  author: `George Orwell`,
  pageCount: 326,
}

let otherBook = {
  title: `A Peoples History`,
  author: `Howard Zinn`,
  pageCount: 723,
}

let getSummary = function(book){
  console.log(`${book.title} by ${book.author}`);
}

getSummary(myBook)
getSummary(otherBook)
Output:   1984 by George Orwell
          A Peoples History by Howard Zinn
```

## Returning objects from a function

Using the two book objects above again:

```JavaScript
let getSummary = function(book){
  return {
    summary: `${book.title} by ${book.author}.`,
    pageCountSummary: `${book.title} is ${book.pageCount} pages long.`

  }
}

let bookSummary = getSummary(myBook)
let otherBookSummary = getSummary(otherBook)
console.log(bookSummary.pageCountSummary);
Output: 1984 is 326 pages long.
```

Another examples that takes in temperature in degrees Fahrenheit and converts it into degrees Celcius and Kelvin:

```JavaScript
let tempCalculator = function(fahrenheit){
  celcius = Math.round((fahrenheit-32) * (5/9))
  kelvin = Math.round((fahrenheit+459.67) * (5/9))
  return {
    'fahrenheit': fahrenheit,
    'celcius': celcius,
    'kelvin': kelvin,
  }
}

let convertedTemps = tempCalculator(32)
console.log(`${convertedTemps.fahrenheit} degrees Fahrenheit is ${convertedTemps.celcius} degrees Celcius and ${convertedTemps.kelvin} degrees Kelvin.`);
Output: 32 degrees Fahrenheit is 0 degrees Celcius and 273 degrees Kelvin.
```

## Object References

What happens when objects are passed around within a program. An example would be the two book object examples above. What happens when one of them is passed to the function as an argument.

When an object is passed into a function as an argument it is not just a clone of the object, it is a reference to the **exact same object** in memory. A pointer to that object. The argument itself is a reference or pointer to the actual object.

If an object is passed into a function as an argument and a property value is changed within the function, the value is changed in the "original" object as well because it is the **exact identical object**.

If however a new value is assigned to the object as a whole (i.e., assigning an empty object to it or chaning all properties and values) then this binding is broken and from that point onwards we are dealing with two different objects. Because of this it is best practice not to re-assign complete value to a previously defined object.

The same behaviour would hold if we were to assign an object to a different variable name. This would **not** be the same as copying the object. The new variable would still refer to the original object.

## Methods

A method is a object property whose value is a function.

The `this` keyword is available within methods and simply refers to the object. So instead of using `objectName.property`, `this.property` can be used.
