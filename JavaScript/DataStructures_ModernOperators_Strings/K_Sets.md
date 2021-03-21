# Sets

JavaScript used to be limited to arrays and objects where data structures are concerned, but in ES6 sets and maps were introduced. These may be new to JS, but have existed in other programming languages for a long time.

## Definition

A set is any collection of _unique_ values. I.e., A given value appears only once in the set.

To create a new set:

```JavaScript
const someNewSet = new Set(); where an interable is passed into the set construction function.
```

Aside: Iterables encountered so far (strings and arrays)

If an array with duplicated items is passed to the Set() constructor function, for example, the resultant `set` will retain only one copy of each duplicated value so that the collection conforms to the definition above.

```JavaScript
const ordersSet = new Set([
  'Pasta',
  'Pizza',
  'Pizza',
  'Risotto',
  'Pasta',
  'Pizza',
]);
concole.log(ordersSet);
Output: Set(3) [ "Pasta", "Pizza", "Risotto" ]
```

Note the similarities to an array. As such they are also iterables. Unlike arrays, however, there are no identical elements and the order of the elements are irrelevant. I.e., Elements cannot be retrieved by an index number such as arrays. There are no indeces. There is actually no way of retrieving individual elements out of a set. If all values are unique and order is irrelevant, then there is no point in retrieving elements from a set.

Aside: This makes iterable data structures strings, arrays and sets.

## Methods / Properties

### Size

```JavaScript
concole.log(ordersSet.size);
Output: 3
```

### has() method

```JavaScript
console.log(ordersSet.has('Pizza'));
Output: true

console.log(ordersSet.has('bread'));
Output: false
```

This method is similar to the array method includes().

### add() method

```JavaScript
ordersSet.add('Garlic Bread');
console.log(ordersSet);
Output: Set(4) [ "Pasta", "Pizza", "Risotto", "Garlic Bread" ]
```

### delete() method

```JavaScript
ordersSet.delete('Risotto');
console.log(ordersSet);
Output: Set(3) [ "Pasta", "Pizza", "Garlic Bread" ]
```

### clear() method

```JavaScript
ordersSet.clear();
console.log(ordersSet);
Output: Set []
```

## Looping over a set

```JavaScript
for(const order of ordersSet) {
  console.log(order);
}
```

## Use case - To remove duplicate values from arrays

```JavaScript
const staff = ['Waiter', 'Chef', 'Waiter', 'Manager', 'Chef', 'Waiter'];
//Need a list of unique positions at a restaurant
const staffUnique = new Set(staff);
console.log(staffUnique); 
Output: Set(3) [ "Waiter", "Chef", "Manager" ]
```

This now has to be converted to an array. Since the spread operator applies to all iterables it can be used here.



