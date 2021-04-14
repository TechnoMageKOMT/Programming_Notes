# String Methods

Refer: Google search MDN string for all available methods

## Properties

.length

Returns the length or numbers of characters of a string

```JavaScript
someString.length 
```

## .toUpperCase()

Changes all characters to uppercase.

## .toLowerCase()

Changes all characters to lowercase.

## .inlcudes(searchString, [startingPoint])

Searches a string for a given substring and returns a boolean. The startingPoint parameter is optional.

## .trim()

Removes white space at the beginning and end of a string.

## .search(searchString)

Returns the index number where the searchString starts.

## .slice(numberStart, numberEnd)

Returns the substring that starts at index number numberStart (inclusive) and ends at numberEnd (excluding).

## .substr(numberStart, length)

Returns the substring starting at index number numberStart "length" characters long.

## .replace(searchString, replacementString)

Replaces the first occurence of the searchString with the replacementString.

## .replaceAll(searchString, replacementString)

Replace all occurences of the searchString with the replacementString

## .split('delimeter')

Returns an array of substrings defined by the delimeter. A sentence with delimiter ' ' will for instance be split into the constituent words.

## .indexOf()

Returns the index number of the first occurence of the search character or substring.

## .lastIndexOf()

Returns the index number of the last occurence of the search character or substring.

## .startsWith()

Returns a boolean based on whether the string starts with the substring entered as argument.

## .endsWith()

Returns a boolean based on whether the string ends with the substring entered as argument.

## .join()

Joins elements of a string array together. Opposite of .split(). Takes in as an arguments the delimiter that should be used.

```JavaScript
[array].join(' ');
```

## .padStart(desiredLength, 'character')

Returns a string padded to the desired length with the specified string character. The padding is before the string

## .padEnd(desiredLength, 'character')

The same as .padStart() but the padding is at the end of the string.

## .repeat(number)

Repeats the attached string the number of times of the number passed in as argument.