# Basics

Second JavaScript course. Only new notes will be recorded.

## Scope

JS uses lexical scope. Sometimes also referred to as static scope. The idea is that variables are only available within the context that they have been assigned. The keyword here is code blocks.  

There are two scopes. Global and Local. Global scope is defined outside of all code blocks. Local scopes are defined inside code blocks.

## Leaked Scope

```JavaScript
if (true){
  if (true) {
    name = `Jen`;
    console.log(name);
  }
}

if (true) {
  console.log(name);
}
```

This happens in cases like the code immediately above when a variable assignment is encountered. JS will go up the scoping chain and if not found will automatically declare a global scope for the variable in question. 

This can cause some unforseen and difficult to detect bugs and should be avoided at all cost.

## undefined versus null

Undefined = A value has never been assigned to a variable.
Null = The value of a vairiable was reset by the developer.

## Function scopes

All same rules applies but it is important to remember that the arguments are also part of the function's local scope and does therefore not form part of the global scope.

There can also be local scopes nested within a function if there are for instance if statements within the function.
