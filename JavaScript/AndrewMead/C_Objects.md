# Objects

Objects are variables that contains unordered data that is structured into key:value pairs. The keys are also called the properties of the object.

A major difference between objects and arrays, is that the order does not matter when retrieving data from objects.

Arrays: Ordered data lists  
Objects: Unordered data lsists

## Create an object

There are numerous ways to declare/construct/define objects, but the simplest is the **object literal syntax**:

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

## Adding data to objects

`objectName.newKey = 'newValue'`
`objectName['newKey'] = 'newValue'`

## Contents of objects

Objects can contain any type of data, including arrays, other objects and even functions (methods). Function expressions are values themselves which is why objects can contain them.

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

- It must be a function expression. Function declarations and arrow functions are not allowed.
- The function name is the key/property.
- The expression (LHS) becomes the value.


The `this` keyword is available within methods and simply refers to the object. So instead of using `objectName.property`, `this.property` can be used.

An Example of a object method using classical JavaScript:

```JavaScript
const person = {
  name: 'Johann',
  age: 46,
  height: 1.76,
  speak: function (want='cookies') {
    console.log(`I want ${want}`)
  }
}
```

Note the allocation of a default value for the required argument. This can be done with any type of function, not just object methods.

In modern JavaScript:

```JavaScript
const person = {
  name: 'Johann',
  age: 46,
  height: 1.76,
  speak (want='cookies') {
    console.log(`I want ${want}`)
  }
}
```

To invoke the method:

`person['speak'](want)`
`person.speak(want)` **more commonly used**

**NB** If a method returns a value, that value should be stored as a new key:value pair as far as possible. I.e., 

```JavaScript
this.newProperty = expression
return expression
```

If a function calss on another function in the same object, it should be done with a proper function call and not by referring to a newly stored key:value pair. The reason: There is no guarantee that the other function has been called. If the other function has not been called a undefined result will be returned.

**Aside** Arrays are just special types of objects, so the methods used on arrays are analogous to these methods created manually on objects. 

## this Keyword

There is a special variable with the keyword `this` built into JavaScript. The keyword refers to the object that it belongs to. So in an object it points to or refers to the object. If there is a property/key called age then the expression this.age within a object method would be equivalent objectName.age. In such cases it is more efficient to use `this` keyword.

Using the example above:

```JavaScript
const person = {
  name: 'Johann',
  age: 46,
  height: 1.76,
  speak (want='cookies') {
    console.log(`${this.name} wants ${want}`)
  }
}
```