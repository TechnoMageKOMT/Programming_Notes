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