# Maps: Fundamentals

## Definition

Maps are data structures that can be used to map values to keys. So data always exist as key:value pairs as they do in objects. The big difference is that in maps, the keys can be of any data type and not just strings as in objects. Keys can even be other maps, objects or arrays. 

## set() method

Just like sets a constructor function, Maps() is used to create maps, but the easiest way to do so is to create an empty map and then fill up the map using the `set()` method. The set() method is analogous to the add method in sets.

```JavaScript
const newMap = new Map();
newMap.set('key name', 'value');
```

In the following example a new restaurant is created and a map is created. The map is then filled out with the set() method. The scenario is that it is a new restaurant with two branches. Note the use of numbers as key in the second and third statements. Also note that the set() method does not only update the map that it is called on, it also returns the map everytime.

```JavaScript
const rest = new Map();
rest.set('name', 'Classico Italiano');
rest.set(1, 'Firenze, Italy');
console.log(rest.set(2, 'Lisbon, Portugal'));
Output: Map(3) { name → "Classico Italiano", 1 → "Firenze, Italy", 2 → "Lisbon, Portugal" }
```

The fact that the set() method returns the updated map is significant. It means the set() method can be applied in chains together. This is because each call returns the updated version of the map.

```JavaScript
rest
  .set('Categories', ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'])
  .set('open', 11)
  .set('close', 23)
  .set(true, `We are open`)
  .set(false, `We are closed`);
```

## get() method  

The get() method is used to read data from a map by simply passing into the method the key of the value that is needed.

```JavaScript
console.log(rest.get('name'));
Output: Classico Italiano

console.log(rest.get(true));
Output: We are open 

```

This data can be manipulated using the data filled into the map so far. Since two of the keys are booleans, the evaluation of boolean expressions can be used to output one of their values.

```JavaScript
const time = 21;
console.log(
  rest.get(
    time > rest.get('open') && time < rest.get('close')
    )
  );
Output: We are open
```

## has() method

The has() method checks if a map has a specified key.

```JavaScript
console.log(rest.has('Categories'));
Output: true
```

## delete() method

The delete method delete based as above on the key.

```JavaScript
rest.delete(2);
console.log(rest);
Output: Map(7) { name → "Classico Italiano", 1 → "Firenze, Italy", Categories → (4) […], open → 11, close → 23, true → "We are open", false → "We are closed" }
```

## size property

Same as sets.

```JavaScript
console.log(rest.size);
Output: 7 
```

## clear() method

Same as sets.

```JavaScript
rest.clear();
console.log(rest);
Output: Map(0)
```

## Using arrays and objects as map keys

**NB** Arrays and objects cannot be passed as key directly. They have to be assigned to a variable first and the variable then gets passed as the key.

```JavaScript
const arr = [1, 2];
rest.set(arr, 'Test')
console.log(rest.get(arr));
Output: 
Map(7)
  size: 8
  <entries>
    0: name → "Classico Italiano"
    1: 1 → "Firenze, Italy"
    2: Categories → Array(4) [ "Italian", "Pizzeria", "Vegetarian", … ]
    3: open → 11
    4: close → 23
    5: true → "We are open"
    6: false → "We are closed"
    7: Array [ 1, 2 ] → "Test"
```

This is very useful where DOM elements are concerned because they are just a special type of object.

```JavaScript
rest.set(document.querySelector('h1'), 'Heading');
console.log(rest);
Output: Map(9)
  size: 9
  <entries>
    0: name → "Classico Italiano"
    1: 1 → "Firenze, Italy"
    2: Categories → Array(4) [ "Italian", "Pizzeria", "Vegetarian", … ]
    3: open → 11
    4: close → 23
    5: true → "We are open"
    6: false → "We are closed"
    7: Array [ 1, 2 ] → "Test"
    8: <h1 style="display: none;"> → "Heading"
```


​







