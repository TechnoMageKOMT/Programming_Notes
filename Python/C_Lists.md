# Lists

Lists can be though of as the most general version of a sequence in Python. Unlike String, they are mutable.

## Length

The len() method is used just like in strings.

## Indexing and Slicing

Done in exactly the same way as in Strings.

## Concatenation

Lists can be concatenated to form a new list(s) containing the elements of the contributor lists. E.g., `new_list = old_list1 + old_list2`

## Duplication Using *

A list can also be duplicated with the * operator as many times as needed: `my_list * 4`

## Arrays in Other Languages

Refer other programming languages, to draw parallels between arrays and lists in Python. Lists in Python however, tend to be more flexible than arrays in other languages for two reasons: they have no fixed size (meaning we don't have to specify how big a list will be), and they have no fixed type constraint (like we've seen above). **NB** JavaScript shares this quality with Python

## Methods

### .append()

To add elements to the end of a list. (Similar to push in JS)

### .pop()

Removes the last element of a list if no arguments are passed. If an index number is passed then the element at that index number will be removed. `list.pop()` returns the popped elements like it does in JS.

### .sort()

This will sort the list "in place". I.e., It does not return a value, but sorts the existing array directly, so it changes the original list.

### sorted() function

Returns the sorted list. Usage `sorted(some_list)`.

### .reverse()

The same as sort() but in the reverse.

## Nested lists

```Python
lst_1 = [1,2,3]
lst_2 = [4,5,6]
lst_3 = [7,8,9]

matrix = [lst_1,lst_2,lst_3]
matrix = [[1,2,3],[4,5,6],[7,8,9]]
```

To grab elements additional brackets are added, so `matrix[1][1]` will yield `5`.