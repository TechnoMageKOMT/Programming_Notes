# The Spread Operator (...)

Expand an array into all of its elements. Unpacking all the elements at once.

Let a starting array be declared as `const arr = [x, y, z]` and the numbers v and w need to be added to the beginning of the array:

```JavaScript
  const arr = [x, y, z];
  const newArr = [v, w, ...arr];
    By using the `...` operator a new array then forms as [v, w, x, y, z]
```

This is useful when dealing with array literals and also when passing arguments into functions. A simple example using the above:

```JavaScript
  console.log(newArr) gives an arrays [v, w, x, y, z] as output, but
  console.log(...newArr) gives the variables v w x y z as output.
```

Suppose the mainMenu array in the restaurant object above needs to be updated. The spread operator enables the following easy way of doing so:

```JavaScript
const newMenu =[...restaurant.mainMenu, 'Gnocci']
```

**NB** This creates a completely new Array. It is not a manipulation of the original Array.

**Diffenerence between spread operator and destructuring**
The spread operator takes out all elements from the array, but does not create new variables. Because of this, it can only be used in places where we would otherwise write values seperated by commas as when passing arguments into a function or when building a new array.

Two use cases of the spread operator:

1. Create shallow copies of arrays
2. Merge two array

## Copying an array

```JavaScript
const mainMenuCopy = [...restaurant.mainMenu];
```

**_Mergeing of arrays_**

```JavaScript
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];
```

## Iterables

The spread operator works on all iterables and there are several of these in JavaScript. Examples of iterables inlude arrays, strings, maps or sets, but _not_ objects. Most built in data structures in JS are iterables with the exception of objects. An example:

```JavaScript
  const str = `Jonas`;
  const letters = [...str, ' ', 'S.'];
  console.log(letters) => Array(7) [ "J", "o", "n", "a", "s", " ", "S." ]
```

Using the restaurant example again, an orderPasta methods has been added to illustrate the above:

```JavaScript
const restaurant = {
  name: 'Classico Italiano',
  physicalAddress: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0,
      close: 24,
    },
  },
  order: function (starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]];
  },
  orderDelivery: function ({starterIndex = 1, mainIndex = 0, time = '20:00', address}){
    console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`);
  },
  orderPasta: function(ing1, ing2, ing3){
    console.log(`Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`);
  },
};

const ingredients = [prompt("Let's make pasta! Ingredient 1?"), prompt("Ingredient 2?"), prompt("Ingredient 3?")];

restaurant.orderPasta(...ingredients);
```

## ... and Objects

Since ES6 in 2018 the spread operator also works for objects even though they are not iterable. Using the restaurant example again:

```JavaScript
const newRestaurant = {foundedIn: 1998,...restaurant, founder: 'Guiseppe'}
```

Shallow copies of objects can also be made by using the ... operator.

```JavaScript
const restaurantCopy = {...restaurant};
```

The nice thing with these shallow copies is that a value changed on one of the objects will not affect the other. I.e., They are seperate objects unlike the situation where a object is copied by merely assigning it to another variable name.
