# Error Handling

## Error Handling - try {...} catch (error) {...}

The `try` statement lets you test a block of code for errors. The `catch` statement lets you handle the error. The `throw` statements lets you create custom errors. The `finally` statement lets you execute code, after try and catch, regardless of the result.

An example of using the throw statement on its own:

```JavaScript
const getTip = (amount) => {
  if (typeof amount === 'number') {
    return amount * 0.25
  } else {
    throw Error('Argument must be a number')
  }
}

const result = getTip('test')
console.log(result)
```

This code will, however, crash the program which is not always desirable. To implement a more elegant way of handling errors, the `try..catch` methods should be added:

```JavaScript
const getTip = (amount) => {
  if (typeof amount === 'number') {
    return amount * 0.25
  } else {
    throw Error('Argument must be a number')
  }
}

try {
  const result = getTip('test')
  console.log(result)
} catch (e) {
  console.log('catch block is running')
}
```

The `try..catch` method will attempt to run the code if it is possible. If it is, the code will run and the `catch` code block will be ignored. If there is an error, the `catch` code block will be excecuted.

The error message can be accessed within the `try..catch` statement by tapping into e.message as follows:

```JavaScript
const getTip = (amount) => {
  if (typeof amount === 'number') {
    return amount * 0.25
  } else {
    throw Error('Argument must be a number')
  }
}

try {
  const result = getTip('test')
  console.log(result)
} catch (e) {
  console.log(e.message)
}
```

This whole process can also be done by checking for false conditions instead of true. This will make it easier to add `throw..try..catch` statements to existing code. Example:

```JavaScript
const getTip = (amount) => {
  if (typeof amount !== 'number') {
    throw Error('Argument must be a number')
  }
  return amount * 0.25
}

try {
  const result = getTip('test')
  console.log(result)
} catch (e) {
  console.log(e.message)
}
```
