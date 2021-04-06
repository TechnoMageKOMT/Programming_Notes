# Nodejs

## REPL - Read, evaluate, print loops

To access node's REPL enter the command node in the terminal. The functionality is the same as that of the single line interpreter that is found in the console of browsers. To exit REPL, simply type .exit.

## Native Node Modules

There are native modules that is included with nodejs "out of the box". To access these they first have to be "required". An example would be the file system module which is needed to interact directly with the PCs file system. The code to require this module would be:

```JavaScript
//jshint esversion:6
const fs = require('fs');
```

The syntax for all modules and code associated with them are found in the documentation at nodejs.org

## Node Package Manager (NPM)

There are a multitude of external modules or packages available for nodejs as well and NPM is the largest package manager in the world dedicated to these. These packages are pre-written code that is simply incorporated into one's own code instead of having to write every bit of code from scratch.

To make use of npm packages issue the command `npm init` in the terminal while in the current project's folder. (This is done from scratch for every new project). A seperate `package.json` file is automatically created during this process. 

To find packages simply search for them at www.npmjs.com. There is installation and usage instructions included for each package. When a package is installed and "required", it is automatically included as a dependency in the relevant `package.json` file.