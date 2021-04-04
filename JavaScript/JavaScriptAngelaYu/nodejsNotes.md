# nodejs Notes

Node documentation

[https://nodejs.org/api/]

## File system module

To load the file system module which will enable node.js to interact with the PC's file system directly use 

```JavaScript
const fs = require('fs')
```

## Copy file

```JavaScript
fs.copyFileSync('sourceFile', 'destinationFile')
```


