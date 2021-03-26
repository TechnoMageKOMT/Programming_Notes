# Working With Strings - Part 2

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