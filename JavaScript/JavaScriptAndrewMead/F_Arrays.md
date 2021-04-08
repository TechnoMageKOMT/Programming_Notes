# Arrays

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

