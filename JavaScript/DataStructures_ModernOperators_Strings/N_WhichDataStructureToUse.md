# Summary: Which Data Structure To Use

(Refer: PDF theory notes)

Sources of data:

1. The _program itself_: Data written directly in source code(eg error logs etc)
2. _UI_: Data input from the user or data written in DOM (eg tasks in a todo app)
3. _External sources_: Fetched from web APIs (eg, recipe objects)

So, more often than not, data is in the form of collections of items of data. As such data structures are used to process the data.

## Arrays versus Sets

Arrays are used when:

- Ordered lists of values are dealt with
- When this data needs to be manipulated (ref large amount of methods available for arrays)

Sets:

- Working with **unique** values
- When high performance is **really** important. They can be up to 10 times faster than arrays
- Used to removed duplicated values from arrays

## Objects versus Maps

Objects are used 

- More traditional way of dealing with key/value pairs 
- Easier to write and access values with . and [] operators
- Use when functions (methods) need to be included
- Use when working with JSON (can convert to map)

Maps

- Better performance
- Keys can have **any** data type
- Easy to iterate
- Easy to compute size
- Use when simply need to map keys to values
- Use when non-string keys are needed