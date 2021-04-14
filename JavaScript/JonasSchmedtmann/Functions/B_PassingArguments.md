# Passing of Arguments Into Function - How Does it Work?

This is linked to primitive data types versus objects, so it is actually about how primitives and objects work within the context of functions.

When passing a primitive to a function it is a copy of its value that is submitted and not the variable itself, so any changes made to the variable inside the function will have no effect on the value of the original variable because it is **not the same variable**.

The opposite is true for objects. So changes made to object values will be changed in the original object because it is the exact same object that is being operated on.

Confusion on these points can cause major bugs in complex applications.

## Passing by Value and Passing by Reference

JavaScript unlike other programming languages only accomodates passing by value and **not** passing by reference.

