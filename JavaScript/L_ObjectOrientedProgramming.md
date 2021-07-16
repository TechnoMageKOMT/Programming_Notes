# Object Oriented Programming (OOP)

## Constructor Functions

The following code produces an output of undefined, as expected, because nothing is returned from the function.

```JavaScript
const person = function () {

}

const me = person()
console.log(me)
```

The addition of the `new` operator (see below). The new operator generates a new object and gives us access to the new object in the constructor function via the `this` value. `this` Can then be used to set up the properties of the constructor function. The `new` operator also returns the object implicitly without there being a return statement in the function.

```JavaScript
const Person = function (firstName) {
  this.firstName = firstName,

}

const me = new Person('Johann')
console.log(me)
```

Note the capital first letter of the function names of constructor functions.

## Prototypal Inheritance

This is of importance when adding methods to constructor functions. Each constructor function **instance** has a `prototype` property which is an object on which we place everything that we want to share between instances of the constructor function such as methods.

Example:

```JavaScript
const Person = function (firstName, lastName, age) {
  this.firstName = firstName
  this.lastName = lastName
  this.age = age
}

Person.prototype.getBio = function () {
  return `${this.firstName} is ${this.age}`
}

const me = new Person('Johann', 'van Vuuren', 46)
console.log(me.getBio())

const person2 = new Person('Kim', 'Alexander', 58)
console.log(person2.getBio())
```

The property that is placed on the prototype is not limited to a function. It can also be a value, but in practice there is not really any sense in doing this.

Side note: If this needs to be used as part of a callback function that is called within another function always use arrow functions for the callback function. By doing this, `this` will inherit from the parent function.

## Primitives and objects

Using literal syntax to set up a new object:

```JavaSCript
const someObject = {
  someProperty: someValue
}
```

Using a constructor function to do the same:

```JavaScript
const someObject = new Object()
//then setting a property:value pair
someObject.someProperty = someValue
```

or:

```JavaScript
const someObject = new Object({
  someProperty: someValue
})
```

Using prototypal inheritance it is in theory possible to add methods on objects, for example:

```JavaScript
Object.prototype.someNewMethod = () => 'Some code here'
```

This method will now be available on all objects in the same way that `hasOwnProperty()` or any other global method is available.

Just like objects above arrays can also be created by constructor functions:

```JavaScript
const myArray = new Array(['item1', 'item2'])
```

### Prototypal inheritance chain for Objects:

myObject --> Object.prototype --> null

### Prototypal inheritance chain for Arrays:

myArray --> Array.prototype --> Object.prototype --> null

### Prototypal inheritance chain for Functions:

myFunction --> Function.prototype --> Object.prototype --> null

### Prototypal inheritance chain for primitives (string, number, boolean, null, undefined)

When a property is accessed on a primitive, it is converted to a object behind the scenes.

There is by way of explanation constructor functions for primitives:

```JavaScript
const someString = new String('value')
```

This then creates an 'object wrapper' around primitives. This happens behind the scenes which is why constructor functions are not used when creating strings.

myString --> String.prototype --> Object.prototype --> null
myNumber --> Number.prototype --> Object.prototype --> null
myBoolean --> Boolean.prototype --> Object.prototype --> null

null and undefined is never implicitly converted to objects and therefore does not have prototypal inheritance chains.

## Class syntax

Example:

```JavaScript
class Person {
  constructor(firstName, lastName, age, likes = []) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.likes = likes
  }
  getBio() {
    let bio = `${this.firstName} is ${this.age}`

    for (const like of this.likes) {
      bio += ` ${this.firstName} likes ${like}.`
    }

    return bio
  }
  setName(fullName) {
    const names = fullName.split(' ')
    this.firstName = names[0]
    this.lastName = names[1]
  }
}

const me = new Person('Johann', 'van Vuuren', 46, [
  'Music',
  'Coding',
  'Reading',
])

me.setName('Albert Einstein')
console.log(me.getBio())

const person2 = new Person('Clancey', 'Turner', 51)
console.log(person2.getBio())
```

## Subclasses

To create a new class that inherits from an existing class the `extends` keyword is used. Using the example above. If the subclass has to inherit from `Person`:

```JavaScript
class Employee extends Person {

}
```

Any modifications are then performed as follow. The `super` keyword is used to access values from the parent. Once the below has been setup, any methods can be changed or even new methods can be added to the subclass.

```JavaScript
class Employee extends Person {
  constructor(firstName, lastName, age, position, likes) {
    super(firstName, lastName, age, likes) //from parent
    this.position = position // new property(i.e., modification)
  }
}
```

Subclasses are not used very often in day to day JavaScript, but they are useful to know about.
