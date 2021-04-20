# Strings

## Bracket notation and indexing

Individual characters are accessed via bracket notation just like JS.

## Reverse indexing

The characters at the end of a string can be accessed without knowing the length of the string. This is done by reverse indexing. I.e., `string[-1]` Last character; `string[-2]` Second last character etc.

## Escape character

`\` Just like in JS. `\n` is the newline character and `\t` is tab.

## Slicing

`string[start:stop:step]`

Start: The starting index (inclusive).
Stop: End index (up to but not including).
Step: Steps. I.e., 2 would be every second character.

`string[2:]` Segment starting at 2 through to the end of the string
`string[:3]` Segment starting at the beginning of the string through to but not including 3
`string[::]` Entire string
`string[2:7:2]` Every second character from index 2 up to but not including 7
`string[::-1]` String in reverse. **Nifty trick**
`string[:-1]` Whole string except for the last character.

## Length

`len(string)`

## Immutability

Strings are immutable so:

```Python
name = 'Sam`
name[0] = 'P'
```

Is invalid code and produces an error.

## String methods

Objects in Python usually have methods associated with them. **NB** The original string is not changed, so if the changes are required to be permanent then the result after the application of the method should be stored in a new variable.

### .upper() and .lower()

Changes all to uppercase and lowercase respectively.

### .split()

By default splits a string based on the whitespace characters between words. Alternative delimeters can also be passed as arguments.

### Print Formatting

This is the interpolation of strings with variables without having to resort to concatenation

Two methods:

- .format() method
- f-strings (formatted string literals)

#### .format() method

`'String here {} then also {}'.format('something1', 'something2')`

One advantage is that strings can be inserted by index number.

`'String here {1} then also {0}'.format('something2, 'something1')`

One can assign variable names to the inserted string:

`'String here {s1} the also {s2}'.format(s2='something2', s1='something1)`

Can be used to set the precision of floating point numbers

`'String here with value {value:width.precision f}'.format(value)`
`'String here with value {r:1.3f}'.format(r=result)` 

- Value is the interpolated value
- Width is the width of the entire number including white space (use default of 1)
- Precision is the number of rounded decimal points
- **NB** The value should be given a key as above. If the value is used directly, a 'KeyError' is returned.

#### f-strings

This is similar to Template Literals in JS. The difference is that it is triggered by a `f` prefix to the normal string in quotation marks. (Not back ticks like JS)

The handling of numbers allowed by .format() above also applies here. The only difference is that the number variable is used directly:

`f'String here with number {numberVariable:1.3f}.'`
