# Error Handling

## Error Handling - try {...} catch (error) {...}

The `try` statement lets you test a block of code for errors. The `catch` statement lets you handle the error. The `throw` statements lets you create custom errors. The `finally` statement lets you execute code, after try and catch, regardless of the result.

```JavaScript
function getMaxLifeValue () {
  const enteredValue = prompt('Maximum life for you and the monster', '100')

  const parsedValue = parseInt(enteredValue)
  if (isNaN(parsedValue) || parsedValue <= 0) {
    throw {message: 'Invalid user input, not a number!'} // Error handling
  }
  return parsedValue
}
```

The idea with try/catch is to wrap it around the code that might fail.

```JavaScript
function getMaxLifeValue () {
  const enteredValue = prompt('Maximum life for you and the monster', '100')

  const parsedValue = parseInt(enteredValue)
  if (isNaN(parsedValue) || parsedValue <= 0) {
    throw {message: 'Invalid user input, not a number!'}
  }
  return parsedValue
}

let chosenMaxLife

try {
  chosenMaxLife = getMaxLifeValue()

} catch (error) {
  console.log(error)
  chosenMaxLife = 100
} finally {
  //code block regarless of the above
}
```
