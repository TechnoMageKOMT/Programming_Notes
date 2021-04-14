# Maps: Iteration

## Population by passing of arrays

The `set()` method is not the most efficient way to populate maps with data.  

One alternative is to pass into the Map() constructor function an array composed of multiple smaller arrays each composed of two values, a key and value pair.

```JavaScript
const question = new Map([
  ['Question', 'What is the best programming language in the world?'],
  [1, 'C'],
  [2, 'Java'],
  [3, 'JavaScript'],
  ['Correct', 3],
  [true, 'Correct!'],
  [false, 'Try again.'],
]);
console.log(question);

Output: Map(7) { Question → "What is the best programming language in the world?", 1 → "C", 2 → "Java", 3 → "JavaScript", Correct → 3, true → "Correct!", false → "Try again." }
```

When, however pairs of data are continuously added to a map programatically, then the `set()` method is still the way to go.

## Converting from Objects to Maps

```JavaScript
const openingHours = {
  [weekdays[3]]: {
    open: 12,
    close: 22,
  },
  [weekdays[4]]: {
    open: 11,
    close: 23,
  },
  [weekdays[5]]: {
    open: 0, // Open 24 hours
    close: 24,
  },
};
```

Recall that `console.log(Object.entries(openingHours));` produced the output of:

```JavaScript
Array (3) […]
  0: Array [ "thu", {…} ]
  1: Array [ "fri", {…} ]
  2: Array [ "sat", {…} ]
```

, which is an array of arrays as discussed in the first section above. So to convert an object to a map all that is needed is:

```JavaScript
const hoursMap = new Map(Objects.entries(openingHours));
console.log(hoursMap);
Output: Map(3) { thu → {…}, fri → {…}, sat → {…} }
script.js:72:9
```

## Iteration

```JavaScript
const question = new Map([
  ['Question', 'What is the best programming language in the world?'],
  [1, 'C'],
  [2, 'Java'],
  [3, 'JavaScript'],
  ['Correct', 3],
  [true, 'Correct!'],
  [false, 'Try again.'],
]);
 /*To print out the the key:value pairs where the key is a number*/
 for (const [key,value] of question) {
  if (typeof key === 'number') {
    console.log(`Answer ${key}: ${value}`);
  }
 }
 Output:  Answer 1: C 
          Answer 2: Java 
          Answer 3: JavaScript  
```

## Converting a map into an array

This is done by building a new array using the spread operator.

```JavaScript
console.log(...question);
Output: Array [ "Question", "What is the best programming language in the world?" ]
        Array [ 1, "C" ]
        Array [ 2, "Java" ]
        Array [ 3, "JavaScript" ]
        Array [ "Correct", 3 ]
        Array [ true, "Correct!" ]
        Array [ false, "Try again." ]
```

## Object methods

All three object methods, `keys()`, `values()` and `entries()` are also available with maps but they have to be used together with the spread operator to create new arrays when using these methods.

```JavaScript
console.log(...question.entries());
console.log(...question.values());
console.log(...question.keys());
```

There is however almost never a use case for this.
