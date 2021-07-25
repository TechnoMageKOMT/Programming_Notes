# List comprehensions

## Definition

A unique way of quickly creating a list with Python.

If you find yourself using a for loop along with .append() to create a list, list comprehensions are a good alternative.

## Examples

```Python
mystring = 'hello'
mylist = []
for letter in mystring:
    mylist.append(letter)
mylist
Output: ['h', 'e', 'l', 'l', 'o']

vs

mylist = [letter for letter in mystring]
```

Another example:

```Python
mylist = [num for num in range(0,11)]
mylist [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

Mathematical operations can also be included:

```Python
mylist = [num**2 for num in range(0, 11)]
mylist: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

#or

mylist = [num for num in range(0, 11) if num%2 == 0]
mylist:[0, 2, 4, 6, 8, 10]

#or

celcius = [0,10,20,34.5]
fahrenheit = [((9/5) * temp + 32) for temp in celcius]
fahrenheit: [32.0, 50.0, 68.0, 94.1]

#or incorporating if else

result = [x if x%2 == 0 else 'ODD' for x in range(0,11)]
result: [0, 'ODD', 2, 'ODD', 4, 'ODD', 6, 'ODD', 8, 'ODD', 10]
```

## Nested list comprehensions

```Python
#Nested for loop
mylist = []
for x in [2,4,6]:
    for y in [1,10,1000]:
        mylist.append(x*y)

#vs nested list comprehension
mylist = [x*y for x in [2,4,6] for y in [1,10,1000]]
```
