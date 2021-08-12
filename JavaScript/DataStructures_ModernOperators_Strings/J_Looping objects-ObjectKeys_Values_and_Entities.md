# Looping Objects: Object Keys, Values and Entities

The for..of loop was introduced which can loop through iterables, but also through non-iterables like objects, in an indirect way.

When looping over objects, the options are to loop over:

1. Property names (aka keys)
2. Values
3. Both together

Even though the loops apply to objects, it is still fundamentally, a process of looping through an array.

## keys() method

The following generic syntax produces an array of an objects's keys called `newArray`:

```JavaScript
const newKeysArray = Object.keys(objectName);
```

This array can then be looped through using the for..of loop:

```JavaScript
for (const someKey of newKeysArray) {
  //some code
}
```

which is the same as:

```JavaScript
for (const someKey of Object.key(objectName)){
  //some code
}
```

The second snippet is just a more efficient and shorter piece of code that achieves the same outcome.

## values() method

This operates very much in the same way but instead using the Object.values() method.

```JavaScript
const newValuesArray = Object.values(objectName);
```

## entries()

The generic syntax here is:

```JavaScript
const newEntriesArray = Object.entries(objectName);
```

If any of these loops produce objects or further arrays, destructuring can always be done to extract the desired information of a nested object.

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
    open: 0, // Open 24 hours
    close: 24,
  },
};

const entries = Object.entries(openingHours);

for (const [key, { open, close }] of entries) {
  console.log(`On ${key} we open at ${open} and close at ${close}`);
}
```
