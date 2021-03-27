# Working With Strings - Part 3

## split() method

Allows the splitting of a string into multiple parts based on a dividing string. The result of applying the method is an array with the individual "pieces" as elements.

```JavaScript
console.log(`a+very+nice+string`.split(`+`));
Output: Array(4) [ "a", "very", "nice", "string" ]
```

Because an array is involved, the method can be used together with destructuring to create new variables from splitting a string into segments.

```JavaScript
const [firstName, lastName] = `Jonas Schmedtmann`.split(` `);
console.log(firstName);
Output: Jonas
console.log(lastName);
Output: Schemdtmann
```

## join() method

Join does the opposite of split. So segements are submitted as an array and then joined with a divider.

```JavaScript
const newName = [`Mr`, firstName, lastName.toUpperCase()].join(` `);
console.log(newName);
Output: Mr Jonas SCHMEDTMANN
```

## Using split() and join() together in a use case scenario

Suppose two name strings had to be capitalised into sentence case.

```JavaScript
const capitalisedName = function(name){
  const names = name.split(` `);
  const namesUpper =[];

  for (const n of names){
    namesUpper.push(n[0].toUpperCase() + n.slice(1));
  }
  console.log(namesUpper.join(` `));
}

capitalisedName(`jessica ann smith davis`);
Output: Jessica Ann Smith Davis
capitalisedName(`johann jansen van vuuren`);
Output: Johann Jansen van Vuuren
```

An alternative solution would be to replace the statement in the for loop with.

```JavaScript
namesUpper.push(n.replace(n[0], n[0].toUpperCase()));
```

## padStart() and padEnd() methods

The methods takes two arguments. The first is the desired length of the string after padding and the second argument is the character that it should be padded with.

```JavaScript
const maskCreditCard = function(number){
  const str = number + '';
  const last = str.slice(-4);
  return last.padStart(str.length, `*`)
}

console.log(maskCreditCard(6546321565798798));
Output: ************8798 
console.log(maskCreditCard(4653287968943413));
Output: ************3413
```

## repeat() method

Repeat the same string multiple times.

```JavaScript
const message2 = `Bad wheather...All Departures Delayed...`
console.log(message2.repeat(5));
Output: Bad wheather...All Departures Delayed...Bad wheather...All Departures Delayed...Bad wheather...All Departures Delayed...Bad wheather...All Departures Delayed...Bad wheather...All Departures Delayed...
```

```JavaScript
const planesInLine = function(n){
  console.log(`There are ${n} planes in line.`.repeat(n));
}

planesInLine(5);
Output: There are 5 planes in line.There are 5 planes in line.There are 5 planes in line.There are 5 planes in line.There are 5 planes in line. 
```



