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
