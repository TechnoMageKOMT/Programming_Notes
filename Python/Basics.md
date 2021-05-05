# Numbers

## Data Types

- int: Integers (1, 2, -5, 1000)
- float: Floating point numbers (including exponents) (1.5, -0.5, 2e2, 3E2)
- str: String
- list: Lists (arrays in JS)
- tuple
- dict: Dictionary
- set
- bool: Boolean

## None keyword and NoneType

The None keyword is used to define a null value (no value at all). It is not the same as 0, False or an empty string, but a data type of its own (NoneType).

```Python
some_variable = None
type(some_variable)
Return: NoneType
```

## Mathematical Operators

`+` Addition
`-` Subtraction
`*` Multiplication
`/` Division
`//` Floor division: Truncates the decimal result without rounding, returning an integer.
`%` Modulus: Division remainder
`**` To the power of.
`=` Assignment operator

## range() operator

`range(x)` - Generates the numbers up to but not including x
`range(x, y)` - Numbers from x (incl.) to y (excl.)
`range(x, y, z)` Same but z as a step size.  

The syntax is reminiscent of string slicing except that round parentises are used.

The operator on itself does not generate anything, but list(range(0, 10, 2)) for instance generates a list.

This will be discussed in greater depth in the generator section.

## Enumerate

Consider:

```Python
index_count = 0
word = 'abcde'

for letter in word:
  print(word[index_count])
  index_count += 1
```

as opposed to:

```Python
word = 'abcde'

for item in enumerate(word):
  print(item)
```

Which produces tuples of the index number with it's matching letter.

## zip function

Does the opposite of enumerate:

```Python
mylist1 = [1,2,3,4,5]
mylist2 = ['a','b','c','d','e']
for item in zip(mylist1, mylist2):
    print(item)
```

This will out put:
(1, 'a')
(2, 'b')
(3, 'c')
(4, 'd')
(5, 'e')

```Python
list(zip(mylist1, mylist2))
Output: [(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd'), (5, 'e')]
```

## in operator

```Python
'x' in [1,2,3]
Output: False

'a' in 'a world'
Output: True

'mykey' in {'mykey': 345}
Output: True #Only works for keys (see below)

d = {'mykey': 345}
345 in d.values()
Output: True

d = {'mykey': 345}
345 in d.keys()
Output: False
```

## min() max() Functions

`min(mylist)` - Returns the lowest value.max  
`max(mylist`  - Returns the highest value

## Random library

To import functions from a library:

```Python
from random import shuffle
# Entering tab after import will bring up a number of functions that can be used from the random library in this case
mylist = [1,2,3,4,5,6,7,8,9,10]
shuffle(mylist)
mylist
Output: [1, 3, 9, 10, 7, 4, 2, 5, 6, 8]
```

**NB** Shuffle does not return anything. It shuffles the list "in place".

```Python
from random import randint
randint(0, 100)
# Output: Returns a random integer from 0 to 100
```

## input() function - User input

`response = input('Enter a number here: ')` - This will trigger a user input field. **NB** Everything is accepted as a string. To recast variable. `int(response)` or `float(response)`

## Variable Names

- May not start with a number
- No spaces
- No special characters except for '_'
- Lowercase only
- Avoid using l (el), I(eye) and O(oh) as single character variable names
- Avoid using reserved words

## type() function

Similar to typeof in JS.

## print() function

Similar to console.log in JS.

## Simple Input/Output (I/O)

To create a new text file in a Jupyter notebook (ONLY)  

```Python
%%writefile myfile.txt
This is a text file.
This is the second line.
This is the third line.
```

myfile = open('myfile.txt') - To open a file  
myfile = open('/path/myfile.txt')  
myfile.read() - Produces a single string of the contents of the file.  
myfile.readlines() - Produces a list with each line as a seperate element of the list.  
myfile.close() - Always close files that are opened in a Jupyter Notebook  
A better way to open files is:  

```Python
with open('myfile.txt) as my_new_file:
  contents = my_new_file.read()
```

Read/write:  

```Python
with open('myfile.txt, mode='*') as myfile:
  
```

The * placeholder:  

- r: Read only
- w: Write only
- a: Append only
- r+: Reading and writing
- w+: Writing and reading (Overwrites existing files or creates new file!)

To append to a file:

```Python
with open('myfile.txt', mode='a') as my_new_file:
  my_new_file.write('Some text')
```

## break, continue, pass: Loop keywords

- break: Breaks out of the current closest enclosing loop
- continue: Goes to the top of the closest enclosing loop
- pass: Does nothing at all.