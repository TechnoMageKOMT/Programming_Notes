# Destructuring Objects

The general process is very similar to array destructuring except that

- { } braces are used instead of [ ] (i.e., object vs array)
- The variable names in the destructuring assignment need to match the object property names _exactly_
- The order of the variables do not matter because objects are not ordered data structures like arrays. (E.g., data is retrieved via property name not index number like arrays.

The generic syntax would be:

```JavaScript
  const {property1, property2, property3} = objectName;
```

Using the restaurant example above again. An example of the general syntax is:

```JavaScript
  const {name, openingHours, categories} = restaurant;
```

This destructures the object into one variable (name), an object (openingHours) and an array (categories.) Destructuring objects is very important when deadling with APIs where data is usually received in the form of objects.

## Allocating new variable names

New names can be allocated to the destructured variables in the following generic manner:

```JavaScript
  const {property1: newName1, property2: newName2, property3: newName3} = objectName;
```

To use our example:

```JavaScript
  const {name: restaurantName, openingHours: hours, categories: tags} = restaurant;
```

The ability to rename varialbles in this way is very useful when dealing with third party software.

## Assigning default values

Similar to arrays, default values can be set for the same reasons as above. I.e., To deal with properties that do not exist in the object that is being destructured. An example would be:

```JavaScript
  const {menu, openingHours, categories} = restaurant;
  menu = undefined because it does not exist in the object restaurant.
```

So, default values can be assigned and it can even be combined in the renaming of variables:

```JavaScript
  const {menu = [], starterMenu: starters = []} = restaurant;
```

All of this is important when dealing with APIs and third party software.

## Mutating variables

Variables can also be mutated, but not in the same way as arrays:

```JavaScript
  let a = x;
  let b = y;
  const obj =  {a:23, b:7, c:14};

  ({a, b} = obj);
  console.log(a, b);    => 23 7
```

This code will mutate the variables a and b to the new values from the destructuring of the object.

## Nested objects

Using the restaurant example again. `openingHours` have already been extracted as an object, so

```JavaScript
  const {fri} = openingHours;
  //yields the object fri that lies withing the object openingHours which is a property of the object restaurant.

  const {fri: {open, close}} = openingHours; //Note the special syntax
  console.log(open, close);
  yields the inner values of the object friday
```

All other functions such as assigning new names to the variables and setting default values still apply despite the nested nature of the extraction.

## Functions with numerous parameters

It happens often in JavaScript that a function requires numerous parameters. It is then very difficult to remember the order of the parameters for someone who is using the function. The way around this is to, instead of defining the parameters manually, simply pass an object into the function as an argument and the function will then immediately destructure that object.

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
