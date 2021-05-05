# For loops

## Introduction

Many objects in Python are iterable, meaning we can iterate over every element in the object. Examples: Every element in a list or every character in a string. For loops can be used to execute a block of code for every iteration through these objects.

## Syntax

```Python
some_iterable = [a, b, c]

for item_name in some_iterable:
  # code block
```

Alternative, if the loop variable is only used for the iteration count. I.e., If the variable is not used in the code block:

```Python
for _ in some_iterable:
  # code block
```

## Unpacking of tuple lists

```Python
mylist = [(1,2), (3,4), (5,6), (7,8)]
for a,b in mylist:
  print(a)
  print(b)
```

## Iteration through dictionaries

The above syntax will only return the keys in the dictionary. If key:value pairs are required then:

```Python
d = {'k1':1, 'k2':2, 'k3':3}
for item in d.items():
  #code block
```

**NB** Tuples are produced ('key', value) but these can be accessed via tuple unpacking

```Python
for key,value in d.items():
  print(value)
Output: The values of the key:value pairs
```

Alternative, if only values are required:

```Python
for value in d.values():
  #code block
```