# Rest Pattern and Parameters

## Rest pattern together with destructuring of Arrays

It shares the same syntax as the spread operator, but does the opposite. I.e., Collects multiple elements and condenses them into an array. Another way to put this; to pack elements into an array.

If `...` is on the RHS of the assignment operator then it functions as the spread operator. If on the LHS it acts as the rest operator:

```JavaScript
//Spread because on RHS of the assignment operator
const str = [1, 2,...[3, 4]];
console.log(str);
Output: [1, 2, 3, 4]
//Rest because on LHS of the assignment operator
const [a, b,...others] = [1, 2, 3, 4, 5];  //Destrtucturing and rest in one
console.log(a, b, others);
Output: 1 2 [3, 4, 5]
```

The rest pattern collects the elements that are unused in a destructuring assignment and places / collects them in a new array.

Using the restaurant example again:

```JavaScript
const [pizza, , risotto, ...otherFood] = [
  ...restaurant.mainMenu,
  ...restaurant.starterMenu,
];
console.log(pizza, risotto, otherFood);
Output: Pizza Risotto [ "Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad" ]
```

Special note: It is everything after Risotto. I.e., the 'rest'. The skipped element is not included. For this reason, the rest pattern must always be the last in the destructuing assignment (LHS). For the same reason, there can only ever be one rest pattern in any destructuring assignment.

## Rest Operator and Objects

The main difference is that the remaining elements will be collected into a new object instead of an array.

```JavaScript
const {sat,...weekDays} = restaurant.openingHours;
console.log(weekDays);
Output: Object { thu: {…}, fri: {…} }
```

### Rest Parameters and Functions

The opposite of the spread pattern here would be to take any arbitrary amount of arguments and to pack them into an array to pass into a function. This is done by the use of rest parameters and the arbitrary arguments are called rest arguments.

```JavaScript
const add = function(...numbers){
  console.log(numbers);
}

add(2, 3);
add(5, 3, 7, 2);
Output: 1: Array [ 2, 3 ]
Output: 2: Array(4) [ 5, 3, 7, 2 ]
```

```JavaScript
const add = function(...numbers){
  let sum = 0;
  for (let i = 0; i < numbers.length; i++){
    sum += numbers[i];
  }
  console.log(sum);
}

add(2, 3);
add(5, 3, 7, 2);
Output: 1: 5
Output: 2: 17
```

An array can also be submitted to this function by using the spread pattern as follow:

```JavaScript
const x = [23, 5, 7];
add(...x)
```

This last example is an excellent example to show that the rest pattern is the reverse or opposite of the spread pattern.

It is highly recommended to use the rest parameter system as far as possible because it removes a lot of restrictions on how arguments can be submitted to a function.

As an example another method has been added to the restaurant function to see the rest parameters in action:

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
  orderDelivery: function ({
    starterIndex = 1,
    mainIndex = 0,
    time = '20:00',
    address,
  }) {
    console.log(
      `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`
    );
  },
  orderPasta: function (ing1, ing2, ing3) {
    console.log(
      `Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`
    );
  },
  orderPizza: function(mainIngredient, ...otherIngredients) {
    console.log(mainIngredient);
    console.log(otherIngredients);
  }
};

restaurant.orderPizza('mushrooms', 'onion', 'olives', 'spinach');
Output:   mushrooms
          Array(3) [ "onion", "olives", "spinach" ]

restaurant.orderPizza('mushrooms');
Output:   mushrooms
          Array []
```

In summary: The spread operator is used where one would use a list of values seperated by commas and the rest operator where one would use variables seperated by commas (like parameters in a function);  
