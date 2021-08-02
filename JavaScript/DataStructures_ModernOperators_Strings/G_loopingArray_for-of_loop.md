# Looping Array: The for-of Loop

This is a new way of looping over an array that was introduced in ES6.

Generic syntax:

```JavaScript
for (const newVariable of array){
  console.log(newVariable);
}
```

This will print out to the console each item in the array.

The continue and break keywords are also still valid with this loop.

The index numbers are not readily available using the loop in it's standard format, but by adding the `entries()` method this is possible. I.e.,

```JavaScript
for(const newVariable of array.entries())

```

This results in multiple arrays listed one after the other consisting of each index number and it's corresponding value. `array.entries()` Is an array iterator which will be covered at a more advanced level.

Because `newVariable` is an array, it can be destructured immediately and the items can be listed with their index numbers:

```JavaScript
for(const [i, el] of array.entries()){ //i = index number and el = element
  console.log(`${i + 1}: ${el});
}
```
