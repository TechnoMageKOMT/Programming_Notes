# Arrays

## What is an iterable?

Any object that can be looped over with a for loop. I.e., Any object that can be iterated over. Not all iterables are arrays. Refer: NodeList, String, Map, Set.

## Array-like objects

Objects that have a length property and use indexes to access items. Again, not all array-like objects are arrays. See NodeList and Strings.

## What is an array?

Arrays are ordered lists of data. They can contain any type of data, even other arrays or objects etc. It is furthermore possible to have different types of data in the same array.

Individual elements are accesed by bracket notation just like strings. The .length property also applies.

To access three dimensional arrays (arrays within arrays), the first set of brackets refers to the entries in the outer-most (first-level) array, and each individual pair of brackets refers to the next level of entries inside.

To access the last item in a list `array[array.length - 1]`.

```JavaScript
const arr = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
  [[10, 11, 12], 13, 14]
];

arr[3] is [[10, 11, 12], 13, 14]
arr[3][0] is [10, 11, 12]
arr[3][0][1] is 11
```

See "Array Methods" file for more detailed information on array methods.

## Declaring / Constructing / Assigning an Array

Three ways:

`const arrayName = [element1, element2,...]` (Most common and recommended way)

`const arrayName = Array.of(element1, element2)`

`const arrayName = Array(element1, element2,...)`

`const arrayName = new Array(element1, element,...)`

If only one argument is passed to the last 2 methods then the number will determine the length of the array and not an element.

The literal syntax is by far the most common way compared to the use of the Array constructor function.

Individual elements/values in `const` declared arrays and objects can be changed, but not the entire array/object. Only primitive data types are truly immutable with `const` declaration.

Arrays can contain any type of and mixture of different data types:

- Primitives
- Expressions
- Variables
- Other arrays
- Objects
- etc

## Array.from() method

An array can also be constructed from an existing array by use of the Array.from() method.

```JavaScript
const newArray = Array.from(existingArray)
```

This method takes in an iterable as argument and also avoids the referencing problem that is encountered when copying arrays and objects.

This is also a nifty way of splitting a string into an array of individual letters. It is also a way of transforming a NodeList into an array where all array methods can be used.

## .forEach() Method

The forEach() method loops over an array. It takes a single argument and that is a call back function. The callback function is not called directly. It gets passed to the forEach API and it is from there that it gets called.

The callback function takes two optional arguments of its own. The first is the item itself and the second is the index of the item.

```JavaScript
array.forEach(function(item, index){
  //Code that will be executed on each element in the array
})
```

Using an arrow function:

```JavaScript
array.forEach((item, index) => {
  //Code that will be executed on each element in the array
})
```

## For loops

Covered extensively in Jonas's course.

Use case:

- forEach() if an array exists and it needs to be looped through in order of the index from the beginning to the end
- for loop when looping in reverse order or in any other specfified way than the index number is required.

## Array composed of objects

All normal array methods still apply to these even though the elements are objects.

The one exception is indexOf() because of object referencing. The object specified in the indexOf() method will not be referencing the same object, so even if all property value pairs are the same, it is **not** the same object.

## Passing arrays to functions as arguments

Arrays are also passed by reference, so any change that is made to the array within the function, will also affect the original array.

## Last item of an array

The last item of an array can be identified even if the length of the array is unknown, using the length property:

```JavaScript
  const lastArrayItem = arrayName[arrayName.length - 1]
```

## push() method

`arrayName.push(someElement)`: Adds 'someElement' to the end of the array and returns the length of the array after the addition of the new element.

## unshift() method

`arrayName.unshift(someElement`: Same as push(), but add the new element to the beginning of the array. Also retuns the length of the new array. Slower than push() because all elements of the array are affected.

## pop() method

`arrayName.pop()`: Removes the last item from the array and returns that item.

## shift() method

`arrayName.shift()`: Removes the first item from the array and returns that item. Slower than pop() because all elements in the array are affected.

## indexOf() method

`arrayName.indexOf(someElement)`: Returns the position of the first occurence of the element given as an argument. If the element is absent, a value of `-1` is returned. It can also take a second argument. This second argument would be the index to start searching.

Cannot be used on arrays composed of objects or any other reference values. See findIndex() method below for an alternative method. The reason for this is that the object passed as an argument is not identical to the object referenced in the array (i.e., its position in memory.)

## lastIndexOf() method

The same as indexOf() but will look for the last occurence of the element passed as argument.

## includes() method

`arrayName.includes(someElement)`: Returns a value of `true` if the element passed as argument is present and `-1` if not. This is useful in conditional statements involving arrays. **NB** === Strict comparison applies. I.e., Will not work with reference values such as objects.

## slice() method

The slice() method returns the selected elements in an array, as a new array object.

The slice() method selects the elements starting at the given start argument, and ends at, but does not include, the given end argument. Negative indexes can also be used here.

If no arguments are given, a copy of the array will be returned without being subject to reference object problems. I.e., The copied array is a brand new array.

Note: The original array will not be changed.

## splice() method

This method is only available on real arrays and not all iterables. The same is true for all the specialised array methods.

`arrayName.splice(arg1, arg2, arg3)`: Removes or replaces items based on the 3 arguments. arg1: Index number to start; arg2: Number of items to remove or replace; arg3: Item to replace with (optional). If 0 is passed as the second argument then nothing will be removed. The third argument will simply be inserted at that point in the array before the index number specified as argument 1. It can also use a -ve number as the first argument in which case it will start at the end of the array and go backwards.

**Note** The method returns the removed element.

```JavaScript
let arr = ['foo', 'bar', 10, 'qux'];

// arr.splice(<index>, <steps>, [elements ...]);

arr.splice(1, 1);// Removes 1 item at index 1
// => ['foo', 10, 'qux']

arr.splice(2, 1, 'tmp');// Replaces 1 item at index 2 with 'tmp'
// => ['foo', 'bar', 'tmp', 'qux']

arr.splice(0, 1, 'x', 'y');// Inserts 'x' and 'y' replacing 1 item at index 0
// => ['x', 'y', 10, 'tmp']
```

## concat() Method

This method adds a array or multiple arrays to an existing array. It combines the values of the arrays. I.e., It does not add the new arrays as nested arrays. The end result is a brand new array with all elements.

## forEach() Method

This method simply loops through the array. The anonymous function here can take 3 arguments. Apart from the first argument, the other two are optional.

1. Individual element of the array (note above)
2. The index number of that individual element
3. The full array

## findIndex() method

This method is an alternative to indexOf() if the array is composed of objects; and works a bit like the forEach() method; it loops through an array until it finds the **first occurence** of the search element based on a returned **truthy** value. The moment it finds a match, the index number is returned and the loop is exited.

```JavaScript
const index = notes.findIndex(function(note, index){
  return note.title === 'Some Note'
})
console.log(index)
```

This piece of code will output the index number of the object with the property value pair, title:'Some Note'.

The anonymous function here can take 3 arguments. Apart from the first argument, the other two are optional.

1. Individual element of the array (note above)
2. The index number of that individual element
3. The full array

## find() Method

Identical to findIndex() except that it returns the item or object directly instead of the index number. If no match is found a value of undefined will be returned.

```JavaScript
const findNote = function(notes, noteTitle) {
  return notes.find(function(note, index){
    return note.title.toLowerCase() === noteTitle.toLowerCase();
  })
}
const note = findNotes(notes, 'office modification');
console.log(note)
```

This function would return the search item by taking as input a `notes` array as well as a `noteTitle`.

The anonymous function here can take 3 arguments. Apart from the first argument, the other two are optional.

1. Individual element of the array (note above)
2. The index number of that individual element
3. The full array

## every() Method

The method tests whether all elements in an array pass the test implemented within the callback function. It returns a boolean value.

```JavaScript
const array1 = [1, 30, 39, 29, 10, 13]
console.log(array1.every((currentValue) => currentValue < 40))
//expected output: true
```

## map() Method

map() calls a provided callbackFn function once for each element in an array, in order, and constructs a new array from the results. callbackFn is invoked only for indexes of the array which have assigned values (including undefined). (MDN reference)

```JavaScript
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

The anonymous function here can take 3 arguments. Apart from the first argument, the other two are optional.

1. Individual element of the array (note above)
2. The index number of that individual element
3. The full array

## some() Method

This method will check if some of the items in the array fullfills the testing condition:

```JavaScript
const hasInexpensiveItems = items.some((item) => {
  return item.price <= 100
})
```

The method will return a boolean value.

## reduce Method

This method carries out an cumulative operation on the items of an array.

```JavaScript
const total = items.reduce((currentTotal, item) => {
  return item.price + currentTotal
},0)
```

The `currentTotal` here is the current total after each iteration of the loop and `0` is the starting point. So, `currentTotal` will start at `0` at the very beginning of the iteration sequence.

## Arrays are also passed by reference

So any changes made in functions like the above will also be made to the original array.

## Filtering Arrays

### filter()

The filter() method works in an analogous way to findIndex() and find() in that it loops over the array looking for the search term. It however returns a new array composed of objects in the original array that contains the search criteria. More specifically where a boolean of true was returned for the test condition(s).

```JavaScript
const findNotes = function(notes, query){

  const filteredNotes = notes.filter(function(note, index){
    const isTitleMatch = note.title.toLowerCase().includes(query.toLowerCase());
    const isBodyMatch = note.body.toLowerCase().includes(query.toLowerCase());
    return isTitleMatch || isBodyMatch;
  })
  return filteredNotes;
}

console.log(findNotes(notes, 'work'));
```

This code will return an array of note objects from a notes array that contain the word work.

```JavaScript
const getThingsToDo = function (todos) {
  const filteredToDoList = todos.filter(function (todo) {
    return !todo.completed; // alternative return todo.completed === false
  });
  return filteredToDoList;
};
console.log(getThingsToDo(todos));
```

This code takes in a to do list array that is composed of todo objects. Each todo object has a boolean property `completed`. The code returns a new array composed of all task that have `completed` values of false.

## sort() method

For arrays composed of simple data types the method will simply sort the array in alphabetical order.

```JavaScript
array.sort();
```

When sorting objects, a callback function needs to be included in the method. If a should come before b then the callback function should return -1, if b should come first 1 and if the order is unchanged 0.

```JavaScript
const sortArray = function (array) {
  array.sort(function(a, b){

  })
}
```

`a` and `b` Here would be individual elements of the array that will be compared. The sorting is then done via an if..else structure and conditions.

```JavaScript
//Let notes be a arrays of objects (notes)
const sortNotes = function (notes {
  notes.sort(function(a, b){
    if (a.title.toLowerCse() < b.title.toLowerCase()) {
      return -1;
    } else if (b.title.toLowerCase() < a.title.toLowerCase()) {
      return 1;
    } else {
      return 0;
    };
  });
});

sortNotes(notes);
console.log(notes;
Output: Sorted list
```

**NB** Capital letters comes before lowercase letters so it is very important to convert all toLowerCase() or toUpperCase() when doing comparisons.

## map() method

The map() method creates a new array with the results of calling a function for every array element.

The map() method calls the provided function once for each element in an array, in order.

Note: map() does not execute the function for array elements without values.

Note: this method does not change the original array.

```JavaScript
const myArray = ['Sam', 'Alice', 'Nick', 'Matt'];

// Appends text to each element of the array
const newArray = myArray.map(name => {
	return 'My name is ' + name;
});
console.log(newArray); // ['My name is Sam', 'My Name is Alice', ...]

// Appends the index of each element with it's value
const anotherArray = myArray.map((value, index) => index + ": " + value);
console.log(anotherArray); // ['0: Sam', '1: Alice', '2: Nick', ...]

// Starting array is unchanged
console.log(myArray); // ['Sam', 'Alice', 'Nick', 'Matt']
```
