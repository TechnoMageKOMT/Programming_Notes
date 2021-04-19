# Strings

## Bracket notation and indexing

Individual characters are accessed via bracket notation just like JS.

## Reverse indexing

The characters at the end of a string can be accessed without knowing the length of the string. This is done by reverse indexing. I.e., `string[-1]` Last character; `string[-2]` Second last character etc.

## Slicing

`string[start:stop:step]`

Start: The starting index (inclusive).
Stop: End index (up to but not including).
Step: Steps. I.e., 2 would be every second character.

`string[2:0]` Segment starting at 2 through to the end of the string
`string[:3]` Segment starting at the beginning of the string through to but not including 3
`string[::]` Entire string
`string[2:7:2]` Every second character from index 2 up to but not including 7
`string[::-1]` String in reverse. **Nifty trick**

## Length

`len(string)`
