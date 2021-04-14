# Working With Strings

## Similarities to arrays and array methods

Individual characters of a string can be accessed just like arrays are accessed. Their index is also zero based like arrays.

```JavaScript
const airline = `Tap Air Portugal`;
const plane = `A320`;

console.log(plane[0]);
Output: A

console.log(`B737`[0])
Output: B
```

### length Property

The `.length` works in the same way:

```JavaScript
const airline = `Tap Air Portugal`;

console.log(airline.length);
Output: 16
console.log(`B737`.length);
Output: 4
```

### indexOf() method

Produced the first occurence's index number or position of the character that is passed to the method as an argument. The argument here could be single characters and/or entire words or strings. If the argument cannot be found then a value of -1 is returned.

```JavaScript
const airline = `Tap Air Portugal`;

console.log(airline.indexOf('r'));
Output: 6
```

### lastIndexOf() method

This method will produce the index number of the last occurence of the argument passed to it. All aspects of indexOf() also apply here.

### slice() method

The method accepts an index number as argument and all characters including and after that index number is returned. (Remember here that the index system is 0 based)

```JavaScript
const airline = `Tap Air Portugal`;

console.log(airline.slice(4));
Output: Air Portugal
```

The method can also accept an optional end parameter.

```JavaScript
const airline = `Tap Air Portugal`;

console.log(airline.slice(4, 7));
Output: Air
```

**NB** The character at the cutoff is not included in the output. The length of the output is always the end value minus the beginning value (3 in this case).

### Working with unkown strings and the slice() method

Suppose the first word is needed of an unkown string. A combination of slice() and indexOf() can be used. Using our example the word would be Tap, but without knowing that, it can be extracted as follow:

```JavaScript
console.log(airline.slice(0, airline.indexOf(' ')));
```

Extracting the last word:

```JavaScript
console.log(airline.slice((airline.lastIndexOf(" "))+1));
Output: Portugal
```

No end parameter was needed because the slice() method will just extract whatever is left of the string. (Remember the second argument is optional).

When negative numbers are passed in as arguments, the extraction will take place in the opposite direction (in reverse):

```JavaScript
console.log(airline.slice(-2));
Output: al

console.log(airline.slice(1, -1));
Output: ap Air Portuga
```

### Boxing: Why do strings have methods if they are primitive data structures

Whenever a method is called on a string, JavaScript converts the string primitive to a string object with the same content. It is then on this object that the method is called. This behaviour is called boxing

So it basically accepts the string as an argument to a constructor function called String:

```JavaScript
console.log(new String('Johann'));
Output:   String { "Johann" }
            0: "J"
            1: "o"
            2: "h"
            3: "a"
            4: "n"
            5: "n"
            length: 6
            <prototype>: String { "" }

console.log(typeof new String('Johann'));
Output: Object
```

When the method on this object is completed, it is converted back to a regular primitive type string. So all string methods return primitive strings.

## toLowerCase() and toUpperCase methods

Do not require any arguments.

```JavaScript
const airline = `Tap Air Portugal`;

console.log(airline.toLowerCase());
Output: tap air portugal
console.log('Johann'.toUpperCase());
Output: JOHANN
```

### Use Case: Fix capitalisation in name

```JavaScript
const passenger = 'jOnAS'
const passengerLower = passenger.toLowerCase();
const passengerCorrect = passengerLower[0].toUpperCase() + passengerLower.slice(1);
console.log(passengerCorrect);
Output: Jonas
```

## trim() method

Removes white space at beginning and end of a string. There is also trimstart() and trimend() which is self-explanatory.

```JavaScript
const email = 'hello@technomage.io';
const loginEmail = '   Hello@Technomage.Io \n';
const lowerEmail = loginEmail.toLowerCase();
const trimmedEmail = lowerEmail.trim();
console.log(trimmedEmail);
Output: hello@technomage.io

//There is also a much shorter way that will produce equivalent results
const normalisedEmail = loginEmail.toLowerCase().trim();
```

## replace() and replaceAll() method

This method takes in two methods. The first is the substring that needs to be replaced and the second is what it needs to be replaced with.

As in the example above chaining is also possible:

```JavaScript
const priceGB = '288,97&';
const priceUS = priceGB.replace('&', '$').replace(',', '.');
```

**NB** None of the string methods changes the original string. New strings are created instead.

The replaceAll() method is the same but, replace all instances of the first term and not just the first one as is the case with replace().

Another method of removing **all** occurences is the use of regular expressions.

### Regular expressions

A string enclosed within forward slashes is a regular expression. The g in the example below stands for "global".

```JavaScript
const announcement = `All passengers come to boarding door 23. Boarding door 23!`;
console.log(announcement.replace(/door/g, 'gate'));
```

## Methods that return booleans

- includes()
- startsWith()
- endsWith()

### includes() method

```JavaScript
const plane = `A320neo`;
console.log(plane.includes(`A320`));
Output: true
```

In practice it is common practice to convert user input to lowercase to account for irregular use of capitalisation.

```JavaScript
const checkBaggage = function(items){
  const baggage = items.toLowerCase();
  if (baggage.includes(`gun`) || baggage.includes('knife')){
    console.log(`You are not allowed onboard with weapons!`);
  } else {
    console.log(`Welcome aboard`);
  }
}

checkBaggage(`I have a laptop, some food and a pocket Knife`);
checkBaggage(`Socks and camera`);
checkBaggage(`Got some snacks and a gun for protection.`);
```


### startsWith() method

```JavaScript
const plane = `A320neo`;
console.log(plane.startsWith(`A`));
Output: true
```

### endsWith() method

```JavaScript
const plane = `A320neo`;
console.log(plane.endsWith(`neo`));
Output: true
```

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

The methods takes two arguments. The first is the desired length of the string after padding and the second argument is the character that it should be padded with. The default padding character is a space, so if no padding character is specified, a space will be used.

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
