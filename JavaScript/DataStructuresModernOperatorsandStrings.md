# Data Structures, Modern Operators and Strings

## Destructuring Arrays

Code for examples:

```
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
};
```

Destructuring is a ES6 feauture which is a way of unpacking values from an array or object into seperate variables.
I.e., A way of breaking a complex data structure down into smaller data structures such as variables (? primitives).

```
Historical way:
const arr = [2, 3, 4];
  const a = arr[0];
  const b = arr[1];
  const c = arr[2];
```

With destructuring this can be done simultateously:

```
  const [x, y, z] = arr;     This is called a destructuring assignment
```

The original array is not affected by this process and remains intact.

The restaurant `object` above have several arrays within it.

```
  const[first, second] = restaurant.categories;
```

Produces variables `first` and `second` with values corresponding to the first two elements of the array. (i.e., Italian and Pizzeria respectively)

### Only selecting certain of the array elements

It is not necessary to select all elements of the array. Elements can even be skipped over by leaving a space in the specification of the destructuring assignment.

```
  const[first, ,third] = restaurant.categories;
```

### Mutating of variable

This method has one very powerful consequency and that is the swapping around of values without having to resort to temporary values.

```
  [x, y] = [y, x];
```

_PS> This process would take place on variables from an already destructured arrray_
_PSS> This actually works on any type of normal variable_

### Functions returing arrays that are immediately destructured into variable

### I.e., Functions returning multiple varialble

Another very powerful consequence of the method is that a function can return an array which can immediately be destructured into individual variables. This allows a function to return multiple values!

By way of example, a function will be added to the above code to order food. Since this is an object, the function will be called a method of the object. The method will accept two parameters. An index for the starter menu and another for the main menu. An order will then hypothetically be given as an index number of what the client wants from both menus. The method will then simply return the content of the specified array based on the index number. To do this the `this` keyword will be used and information will be returned as an array. When this method is being called the returned array will immediately be destructured into two seperate variables as can be seen at the end of the code below:

```
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
  }
};


const [starter, mainCourse] = restaurant.order(2, 0);
```

### Nested arrays

Nested arrays are simply handled like:

```
  const nested = [2 ,4, [5, 6]];
  const [i, ,j] = nested
    This results in a variable and an array.
```

Destructuring inside destructuring:

```
const [i, ,[j, k]] = nested;
    This will result in 3 seperate variables.
```

### Assigning default values

Default values can also be assigned to the extraction variables. This is very useful when the length of the array is unknown which is often the case in real world applications. If the array is shorter than we expect, then we might attempt to unpack the array in postions that don't even exist.
Suppose we have an array [8, 9] and attempt to destructure this array for three elements

```
  const [p, q, r] = [8 , 9];    r would be undefined, so
  const [p=1, q=1, r=1] = [8, 9];  r would be 1
```

This is often useful when dealing with API's.

## Destructuring Objects

The general process is very similar to array destructuring except that

- { } braces are used instead of [ ] (i.e., object vs array)
- The variable names in the destructuring assignment need to match the object property names _exactly_
- The order of the variables do not matter because objects are not ordered data structures like arrays. (E.g., data is retrieved via property name not index number like arrays.

The generic syntax would be:

```
  const {property1, property2, property3} = objectName;
```

Using the restaurant example above again. An example of the general syntax is:

```
  const {name, openingHours, categories} = restaurant;
```

This destructures the object into one variable (name), an object (openingHours) and an array (categories.) Destructuring objects is very important when deadling with APIs where data is usually received in the form of objects.

### Allocating new variable names

New names can be allocated to the destructured variables in the following generic manner:

```
  const {property1: newName1, property2: newName2, property3: newName3} = objectName;
```

To use our example:

```
  const {name: restaurantName, openingHours: hours, categories: tags} = restaurant;
```

The ability to rename varialbles in this way is very useful when dealing with third party software.

### Assigning default values

Similar to arrays, default values can be set for the same reasons as above. I.e., To deal with properties that do not exist in the object that is being destructured. An example would be:

```
  const {menu, openingHours, categories} = restaurant;
  menu = undefined because it does not exist in the object restaurant.
```

So, default values can be assigned and it can even be combined in the renaming of variables:

```
  const {menu = [], starterMenu: starters = []} = restaurant;
```

All of this is important when dealing with APIs and third party software.

### Mutating variables

Variables can also be mutated, but not in the same way as arrays:

```
  let a = x;
  let b = y;
  const obj =  {a:23, b:7, c:14};

  ({a, b} = obj);
  console.log(a, b);    => 23 7
```

### Nested objects

Using the restaurant example again. `openingHours` have already been extracted as an object, so

```
  const {fri} = openingHours;
  yields the object fri that lies withing the object openingHours which is a property of the object restaurant.

  const {fri: {open, close}} = openingHours;
  console.log(open, close);
  yields the inner values of the object friday
```

All other functions such as assigning new names to the variables and setting default values still apply despite the nested nature of the extraction.

### Functions with numerous parameters

It happens often in JavaScript that a function requires numerous parameters. It is then very difficult to remember the order of the parameters for someone who is using the function. The way around this is to, instead of defining the parameters manually, simply pass an object into the function as an argument and the function will then immediately destructure that object.

```
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
  orderDelivery: function ({starterIndex, mainIndex, time, address}){
    console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`);

  }
};

restaurant.orderDelivery({
  time: '22:30',
  address: 'Via del Sole, 21',
  mainIndex: 2,
  starterIndex: 2,
})
```

Note that the order of the properties in the destructuring statement does not matter as long as they match that of the object in the function call exactly.

**Take home point here:** A function can accept an object that is immediately destructured as above and the order of the arguments then does not have to be know because of the destructuring process. This will become increasingly important as the number of function paramaeters increases.

## The Spread Operator (...)

Expand an array into all of its elements. Unpacking all the elements at once.

Let a starting array be declared as `const arr = [x, y, z]` and the numbers v and w need to be added to the beginning of the array:
```
  const arr = [x, y, z];
  const newArr = [v, w, ...arr];
    By using the `...` operator a new array then forms as [v, w, x, y, z]
```
This is useful when dealing with array literals and also when passing arguments into functions. A simple example using the above:
```
  console.log(newArr) gives an arrays [v, w, x, y, z] as output, but
  console.log(...newArr) gives the variables v w x y z as output.
```
Suppose the mainMenu array in the restaurant object above needs to be updated. The spread operator enables the following easy way of doing so:
```
const newMenu =[...restaurant.mainMenu, 'Gnocci']
```
**NB** This creates a completely new Array. It is not a manipulation of the original Array.

**Diffenerence between spread operator and destructuring**
The spread operator takes out all elements from the array, but does not create new variables. Because of this, it can only be used in places where we would otherwise write values seperated by commas as when passing arguments into a function or when building a new array.

Two use cases of the spread operator:
1) Create shallow copies of arrays
2) Merge two array

**Copying an array**
```
const mainMenuCopy = [...restaurant.mainMenu];
```
***Mergeing of arrays***
```
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];
```
### Iterables

The spread operator works on all iterables and there are several of these in JavaScript. Examples of iterables inlude arrays, strings, maps or sets, but *not* objects. Most built in data structures in JS are iterables with the exception of objects. An example:
```
  const str = `Jonas`;
  const letters = [...str, ' ', 'S.'];
  console.log(letters) => Array(7) [ "J", "o", "n", "a", "s", " ", "S." ]
```
Using the restaurant example again, an orderPasta methods has been added to illustrate the above:
```
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

### ... and Objects

Since ES6 in 2018 the spread operator also works for objects even though they are not iterable. Using the restaurant example again:
```
const newRestaurant = {foundedIn: 1998,...restaurant, founder: 'Guiseppe'}
```

Shallow copies of objects can also be made by using the ... operator.
```
const restaurantCopy = {...restaurant};
```
The nice thing with these shallow copies is that a value changed on one of the objects will not affect the other. I.e., They are seperate objects unlike the situation where a object is copied by merely assigning it to another variable name. 