# Optional Chaining (.?)

## Objects Properties

This is also an ES6 features that applies to objects as well as arrays.

If a certain property in a chain of properties does not exist then undefined is returned immediately. 

```JavaScript
const openingHours = {
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
};

console.log(restaurant.openingHours.mon?.open);
```

So the way this works is that only if the property on the LHS of the ? exist will the property on the right be read or evaluated. If it does not, a message of undefined will immediately be returned. **NB** A property exist if it is not null nor undefined.

Chains of these statements can also be used. E.g.,

```JavaScript
console.log(restaurant.openingHours?.mon?.open);
```

This statement will first evaluate if the property `openingHours` exists, then `mon` and if both exist read or evaluate the last property or object.

Another example:

```JavaScript
const openingHours = {
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
};

const days = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun'];

for (const day of days) {
  const open = restaurant.openingHours[day]?.open ?? 'closed'; //Setting a default value if the first statement is a falsy value such as undefined. Using the nullish coalescing operator so that 0 does not cause incorrect results as it would on Saturdays when the resutaurant opens at 0.
  console.log(`On ${day}, we open at ${open}`);
}
```

Both the nullish coalescing (??) and optional chaining (?.) operators were introduced in ES2020 because they tend to work so well together.  

## Object Methods

Using the optional chaining operator we can check if a method exists before calling it. 

```JavaScript
const restaurant = {
    name: 'Classico Italiano',
    location: 'Via Angelo Tavanti 23, Firenze, Italy',
    categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
    starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
    mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  
    // ES6 enhanced object literals
    openingHours,
  
    order(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]];
    },
  
    orderDelivery({ starterIndex = 1, mainIndex = 0, time = '20:00', address }) {
      console.log(
        `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`
      );
    },
  
    orderPasta(ing1, ing2, ing3) {
      console.log(
        `Here is your declicious pasta with ${ing1}, ${ing2} and ${ing3}`
      );
    },
  
    orderPizza(mainIngredient, ...otherIngredients) {
      console.log(mainIngredient);
      console.log(otherIngredients);
    },
  };


console.log(restaurant.order?.(0, 1) ?? 'Method does not exist');
Output: Array [ "Focaccia", "Pasta" ]

console.log(restaurant.orderRisotto?.(0, 1) ?? 'Method does not exist');
Output: Method does not exist
```

## Arrays

Example:

```JavaScript
const users = [{name: 'Jonas', email: 'hello@jonas.io'}];
console.log(users[0]?.name ?? 'User array empty');
Output: Jonas
```

**NB** The two operators as mentioned above is almost always used together.
