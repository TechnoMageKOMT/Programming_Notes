# Short Circuiting (&& and ||)

## The OR (||) Operator

In addition to using the && and || to combine boolean values, there are several other uses for them as well.

There are three other properties of these operators:

- They can use any data type
- They can return any data type
- They also do short circuit evaluation (short circuiting) - If the first value is a truthy value the expression will immediately  return that value. I.e., if the first operand is a truthy value, the second value will not be evaluated at all.

```JavaScript
console.log(3 || `Jonas`);
Output: 3

console.log(`` || `Jonas`);
Output: Jonas

console.log(true || 0);
Output: true

console.log(undefined || null);
Output: null
  //The first operand here were a falsy so the second was immediately returned even though it is a falsy as well.

console.log(undefined || 0 || `` || `Hello` || 23 || null);
Output: Hello //I.e., the first truthy value in the list of operands
```

An interesting use case is if we need to use a variable but do not know if it already exists.

```JavaScript
const guests = restaurant.numGuests ? restaurant.numGuest : 10;
console.log(guests);
//I.e., We wanted to know if restaurant.numGuests exist before either using it (if it exists) or assigning a value to it (if it does not exist)
```

An equivalent statement would be:

```JavaScript
const guests = restaurant.numGuests || 10;
//I.e., The default value if restaurant.numGuests does not exist is 10.
```

This is much better method to set default values instead of using the ternary operator or even worse, if..else statements.

**NB** This will not work if the value of restaurant.numGuests is 0 because it will be evaluated as a falsy value and an incorrect value of 10 will be assigned. This will be discussed in the (Nullish Coalescing Operator section).

## The AND (&&) Operator

As far as short circuit evaluation is concerned the AND operator acts in the exact opposite way as the OR operator. I.e., It short circuits as soon as the first value is found to be falsy.

```JavaScript
console.log(0 && `jonas`);
Output: 0

console.log(7 && `Jonas`);
Output: Jonas

console.log(`Hello` && 23 && null && `Jonas`);
Output: null
```

With this knowledge the following code can be simplified:

```JavaScript
if (restaurant.orderPizza) {
  restaurant.orderPizza('mushrooms', 'spinach')
}
```

to 

```JavaScript
restaurant.orderPizza && restaurant.orderPizza('mushrooms', 'spinach')
```

So, if the first operand does not exist nothing will happen, if it does then the second operand will be excecuted.

**CAUTION** Don't repeat all if..else statements with the && and || operators because it will make the code very difficult ro read.

## Summary

The || operator will return the first truthy value of all operands or the last value if all operands are falsy.
The && operator will return the first falsy value or the last value if all of the operands are truthy. 

**Practical Applications** The || operator can be used to set default values and the && can be used to excecute code in the second operand if the first one is true.
