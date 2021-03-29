# The Nullish Coalescing Operator(??)

Recalling the problem with the OR operator:

```JavaScript
restaurant.numGuests = 0;
const guests1 = restaurant.numGuests ? restaurant.numGuests : 10;
console.log(guests1);
```

Because 0 is a falsy value this code would result in the incorrect output of 10 instead of 0.

The nullish coalescing operator solves this problem by working with nullish values instead of falsy values. I.e., Undefined or null values which does not include 0 or an empty string. It therefore sees 0 and `` as truthy values. Only null or undefined values will shortcut the statement below and go to the default value of 10:

```JavaScript
restaurant.numGuests = 0;
const guestCorrect = restaurant.numGuests ?? 10;
console.log(guestCorrect);
Output: 0
```