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
