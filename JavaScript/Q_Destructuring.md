# Destructuring

## Destructuring Objects

Allows the unpacking of calues from objects and arrays.

So, conventionally if values are needed from an object:

```JavaScript
const todo = {
  id: 'lkjlsakjdl',
  text: 'Pay the bills',
  completed: false,
}

const text = todo.text
const completed = todo.completed
```

Doing the same with destructuring:

```JavaSCript
const todo = {
  id: 'lkjlsakjdl',
  text: 'Pay the bills',
  completed: false,
}

const { text, completed } = todo

console.log(text)
console.log(completed)
```

The name of the variable can be changed as needed:

```JavaScript
const { text:todoText, completed } = todo
```

A default value can also be provided for a value if it does not exist on the object. This default value can be of any type (string, number, boolean, array, object):

```JavaSCript
const todo = {
  id: 'lkjlsakjdl',
  text: 'Pay the bills',
  completed: false,
}

const { text: todoText, completed, details = 'No details provided' } = todo

console.log(todoText)
console.log(completed)
console.log(details)
```

The renaming of variable and assigning of a default value can also be combined into a single statement:

```JavaScript
const { text: todoText, completed, details:otherDetails = 'No details provided' } = todo
```

### Using the rest operator with destructuring objects

If all the other 'un-named' properties of the object also needs to be destructured. It the case of the example, this will only be the id:

```JavaScript
const { text: todoText, completed, details = 'No details provided', ...others } = todo
```

This statement would return an object with all the remaining property:value pairs in it.

## Destructuring arrays

The order fo destructuring with arrays are important unlike with objects.

```JavaScript
const age = [65, 0, 13, 21]
const [firstAge] = age //Grabs first item in the array
const [firstAge, secondAge] = age //Grabs the first two items
const [firstAge, secondAge, , fourthAge] = age //Skips the third item

```

Default values can also be provided as with objects and the rest parapeter can also be used.

Use of a default value:

```JavaScript
const age = [65, 0, 13]
const [firstAge, secondAge, , fourthAge = 123] = age
```

Using the rest parameter:

```JavaScript
const age = [65, 0, 13]
const [firstAge, ...otherAges] = age
```

This will produce a new array with the remaining items in it.

## Destructuring with functions

When an object is passed into a function as an argument it can be destructured immediately:

Conventional:

```JavaScript
const printTodo = (todo) => {
  console.log(`${todo.text}: ${todo.completed})
}
printTodo(todo)
```

Destructuring the object:

```JavaScript
const printTodo = ({ text, completed }) => {
  console.log(`${text}: ${completed}`)
}

printTodo(todo)
```
