# Saving data in local storage

CRUD =

- Create
- Read
- Update
- Delete

Local storage is accessed via the `localStorage` global object. The object is a key/value store similar to ordinary objects encountered thus far. Data can be stored under a specific key and accessed later on.

## Create: setItem() method

Takes two arguments. A key and a corresponding value.

The following code saves the string value 'John' to the key 'username'

```JavaScript
localStorage.setItem('firstName', 'John')
```

## Read: getItem() method

Takes a single argument. The key of the required value.

The following code will read the corresponding value and store it in the variable name.

```JavaScript
const name = localStorage.get('firstName')
```

## Update: setItem() method

The update part of CRUD is simply handled by setItem() but with the value associated with a particular property updated to the new value.

## Delete: removeItem() method

Takes a single argument. The key of the key:value pair that needs to be deleted.

```JavaScript
localStorage.removeItem('firstName')
```

## Delete clear() method

No arguments. This method deletes all data stored in localStorage.

```JavaScript
localStorage.clear()
```

## Storage of arrays and objects

This will require calling a method on a global variable called JSON (JavaScript Object Notation).

There are two methods of interest. the parse() and stringify() methods.

```JavaScript
user = {
  name: 'Johann',
  age: 46
}

const userJSON = JSON.stringify(user)
console.log(userJSON)
Output: {"name":"Johann","age":46}
```

Note that the key's are wrapped in "" and tha there are no spaces. So what appears to be an object is actually an uninterupted string of characters. This string can now be saved to localStorage.

```JavaScript
localStorage.setItem('user', userJSON)
```

To retrieve this at a later stage, the getItem() method is used on localSTorage and parse() on JSON.

```JavaScript
const userJSON = localStorage.getItem('user')
const user = JSON.parse(userJSON)
```

This will convert the parsed string back into an object.

