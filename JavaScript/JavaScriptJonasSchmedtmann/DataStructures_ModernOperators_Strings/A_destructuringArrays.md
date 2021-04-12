# Destructuring Arrays

Code for examples:

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
};
```

Destructuring is a ES6 feauture which is a way of unpacking values from an array or object into seperate variables.
I.e., A way of breaking a complex data structure down into smaller data structures such as variables (? primitives).

```JavaScript
Historical way:
const arr = [2, 3, 4];
  const a = arr[0];
  const b = arr[1];
  const c = arr[2];
```

With destructuring this can be done simultateously:

```JavaScript
  const [x, y, z] = arr;     This is called a destructuring assignment
```

The original array is not affected by this process and remains intact.

The restaurant `object` above have several arrays within it.

```JavaScript
  const[first, second] = restaurant.categories;
```

Produces variables `first` and `second` with values corresponding to the first two elements of the array. (i.e., Italian and Pizzeria respectively)

## Only selecting certain of the array elements

It is not necessary to select all elements of the array. Elements can even be skipped over by leaving a space in the specification of the destructuring assignment.

```JavaScript
  const[first, ,third] = restaurant.categories;
```

## Mutating of variable

This method has one very powerful consequency and that is the swapping around of values without having to resort to temporary values.

```JavaScript
  [x, y] = [y, x];
```

_PS> This process would take place on variables from an already destructured arrray_
_PSS> This actually works on any type of normal variable_

## Functions returning arrays that are immediately destructured into variable

### I.e., Functions returning multiple varialble

Another very powerful consequence of the method is that a function can return an array which can immediately be destructured into individual variables. This allows a function to return multiple values!

By way of example, a function will be added to the above code to order food. Since this is an object, the function will be called a method of the object. The method will accept two parameters. An index for the starter menu and another for the main menu. An order will then hypothetically be given as an index number of what the client wants from both menus. The method will then simply return the content of the specified array based on the index number. To do this the `this` keyword will be used and information will be returned as an array. When this method is being called the returned array will immediately be destructured into two seperate variables as can be seen at the end of the code below:

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
  }
};


const [starter, mainCourse] = restaurant.order(2, 0);
```

## Nested arrays

Nested arrays are simply handled like:

```JavaScript
  const nested = [2 ,4, [5, 6]];
  const [i, ,j] = nested
    This results in a variable and an array.
```

Destructuring inside destructuring:

```JavaScript
const [i, ,[j, k]] = nested;
    This will result in 3 seperate variables.
```

## Assigning default values

Default values can also be assigned to the extraction variables. This is very useful when the length of the array is unknown which is often the case in real world applications. If the array is shorter than we expect, then we might attempt to unpack the array in postions that don't even exist.
Suppose we have an array [8, 9] and attempt to destructure this array for three elements

```JavaScript
  const [p, q, r] = [8 , 9];    r would be undefined, so
  const [p=1, q=1, r=1] = [8, 9];  r would be 1
```

This is often useful when dealing with API's.
