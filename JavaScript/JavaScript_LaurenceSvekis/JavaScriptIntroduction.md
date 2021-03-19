# JavaScript Introduction - Laurence Svekis

## Output Options

```JavaScript
document.write(`Message`);
```

This message will print out wherever the `<script>` tags are within the structure of the HTML document.

```JavaScript
document.getElementById('someID').innerHTML = `Message`;
```

This option offers full  control of where the output will appear because we're targeting an element by it's unique ID.

```JavaScript
console.log()
console.error()
console.warn()
```

These are built in functions that are mainly used for debugging.
