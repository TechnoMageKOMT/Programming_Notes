# Arrays

Arrays are ordered lists of data. They can contain any type of data, even other arrays or objects etc. It is furthermore possible to have different types of data in the same array.

Individual elements are accesed by bracket notation just like strings. The .length property also applies.

To access three dimensional arrays (arrays within arrays), the first set of brackets refers to the entries in the outer-most (first-level) array, and each individual pair of brackets refers to the next level of entries inside.

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

Two ways:

`const arrayName = [element1, element2,...]`

`const arrayName = new Array(element1, element,...)`

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

This method avoids the referencing problem that is encountered when copying arrays and objects.


## .forEach() Method

The forEach() method loops over an array. It takes a single argument and that is a call back function.

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

- forEach() if an array exists and it needs to be looped through in order of the index
- for loop when looping in reverse order or in any other specfified way than the index number.

## Array composed of objects

All normal array methods still apply to these even though the elements are objects.

The one exception is indexOf() because of object referencing. The object specified in the indexOf() method will not be referencing the same object, so even if all property value pairs are the same, it is **not** the same object.

## Last item of an array

The last item of an array can be identified even if the length of the array is unknown, using the length property:

```JavaScript
  const lastArrayItem = arrayName[arrayName.length - 1]
```

## push() method

`arrayName.push(someElement)`: Adds 'someElement' to the end of the array and returns the length of the array after the addition of the new element.

## unshift() method

`arrayName.unshift(someElement`: Same as push(), but add the new element to the beginning of the array. Also retuns the length of the new array.

## pop() method

`arrayName.pop()`: Removes the last item from the array and returns that item.

## shift() method

`arrayName.shift()`: Removes the first item from the array and returns that item.

## indexOf() method

`arrayName.indexOf(someElement)`: Returns the position of the element given as an argument. If the element is absent, a value of `-1` is returned.

## includes() method

`arrayName.includes(someElement)`: Returns a value of `true` if the element passed as argument is present and `false` if not. This is useful in conditional statements involving arrays. **NB** === Strict comparison applies.

## slice() method

The slice() method returns the selected elements in an array, as a new array object.

The slice() method selects the elements starting at the given start argument, and ends at, but does not include, the given end argument.

Note: The original array will not be changed.

## splice() method

`arrayName.splice(arg1, arg2, arg3)`: Removes or replaces items based on the 3 arguments. arg1: Index number to start; arg2: Number of items to remove or replace; arg3: Item to replace with (optional).

```JavaScript
let arr = ['foo', 'bar', 10, 'qux'];

// arr.splice(<index>, <steps>, [elements ...]);

arr.splice(1, 1);// Removes 1 item at index 1
// => ['foo', 10, 'qux']

arr.splice(2, 1, 'tmp');// Replaces 1 item at index 2 with 'tmp'
// => ['foo', 10, 'tmp']

arr.splice(0, 1, 'x', 'y');// Inserts 'x' and 'y' replacing 1 item at index 0
// => ['x', 'y', 10, 'tmp']
```

## findIndex() method

This method is an alternative if the array is composed of objects and works a bit like the forEach() method; it loops through an array until it finds the first occurence of the search element based on a **truthy** value.

```JavaScript
const index = notes.findIndex(function(note, index){
  return note.title === 'Some Note'
})
console.log(index)
```

This piece of code will output the index number of the object with the property value pair, title:'Some Note'.

## find() Method

Identical to findIndex() except that it returns the item or object directly instead of the index number

```JavaScript
const findNote = function(notes, noteTitle) {
  return note = notes.find(function(note, index){
    return note.title.toLowerCase() === noteTitle.toLowerCase();
  })
}
const note = findNotes(notes, 'office modification');
console.log(note)
```

This function would return the search item by taking as input a `notes` array as well as a `noteTitle`.

## Arrays are also passed by reference

So any changes made in functions like the above will also be made to the original array.

## Filtering Arrays

### filter()

The filter() method works in an analogous way to findIndex() and find() in that it loops over the array looking for the search term. It however returns a new array composed of objects in the original array that contains the search criteria.

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
    return !todo.completed;
  });
  return filteredToDoList;
};
console.log(getThingsToDo(todos));
```

This code takes in a to do list array that is composed of todo objects. Each todo object has a boolean property `completed`. The code returns a new array composed of all task that have `completed` values of false.

## sort() method 

For arrays composed of simple methods the method will simply sort the array in alphabetical order.

```JavaScript
array.sort();
```

When sorting objects a callback function needs to be included in the method:

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