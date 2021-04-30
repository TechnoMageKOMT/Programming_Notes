# Sets

## Definition

Unordered collections of unique elements. I.e., There can only be one representation of the same object.

## .add() Method

Adds the argument to the set. If the item is already in the set then it will not be added because only **unique** values are contained in sets.

```Python
some_set = set()
some_set.add()
```

## Applied to a list

When applied to a list, a set with only the unique values will be returned.

```Python
mylist = [1,1,1,1,1,2,2,2,2,3,3,3,]
set(mylist)
Return: {1,2,3}
```
