# Babel

## Installation

Install locally in root folder of project:

Specific to **every** folder that it is used in:

````CLI
npm init
sudo npm install @babel/core @babel/cli
npm install babel-preset-env --save
npm install live-server

## Usage

```CLI
babel input.js -o output.js --presets @babel/env
````

The file can be called anything as long as the first is the input file and the second the output.

When linking js code to projects, the output.js file will be used with the "translated" code in it.

## npm_modules

These are normally not included with production code. If this folder was deleted, it can be retrieved again by the CLI command `npm install`.

## Setting up a boilerplate

Add `public` and `src` (source) folders to project folder. The code before babel processing will be placed in the `src` folder and the processed code in `public`.

Inside public, a subfolder `scripts` is then created. Then move bundle.js (output) to scripts.

Next create index.html in `public`.

## Running scripts via package.json

Remove the standard key:value pair from "scripts" in package.json and replace it with a new pair consisting of a command and then the CLI script used for babel processing:

```JavaScript
{
  "scripts":
    "server": "live-server public",
    "build": "babel src/index.js -o public/scripts/bundle.js --presets @babel/env"
}
```

Note the standard usage of naming the input file `index.js` and the output file `bundle.js`.

Once this is done the command is run by the folowing command in the CLI
`npm run build`.

## Babel to check for changes automatically

Just add --watch to the script in package.json (see immediately above).

With this in place, babel will "watch" index.js for any changes and run the script when changes are detected. I.e., Autoamtically process the code with babel.

## Webpack

Install locally in the project folder **every** time:

```CLI
npm install --save-dev webpack
npm install --save-dev webpack-cli
```

Add script to package.json as above:

```JavaScript
{
  "scripts":
    "webpack": "webpack",
    "build": "babel src/index.js -o public/scripts/bundle.js --presets @babel/env"
}
```

Once this is done a configuration file needs to be created. The configuration file is created in the root folder of the project. The name of the config file should be `webpack.config.js`.

The content of the configuration file:

```JavaScript
const path = require('path')

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'public/scripts'),
    filename: 'bundle.js',
  },

```

To run webpack `npm run webpack` via the script in package.json.

## Adding support for Babel into Webpack

The Webpack Babel loader is needed for this.

`npm install babel-loader@7.1.4`

Then adjust the webpack.config.js file to:

```JavaScript
const path = require('path')

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'public/scripts'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['env'],
          },
        },
      },
    ],
  },
}
```

## Webpack Dev Server

`npm install webpack-dev-server@3.1.3`

## JavaScript Modules

Import/export system.

If there are two js files, index.js and utilities.js.

In index.js which is the entry point or main file:

```JavaScript
//utilities.js
export const add = (a, b) => a + b
//index.js
import { add } from './utilities'
```

Multiple export/imports

```JavaScript
//utilities.js
export const add = (a, b) => a + b

export const name = 'Johann'
//index.js
import { add, name } from './utilities'

```

In addition to multiple 'named' exports there can also be a 'default' export per file. The code below will export `square` in addition to the named exports.

```JavaScript
//utilitie.js
const square = (x) => x * x
export default square
//index.js
import square, { add, name } from './utilities'
```

If there is only the default import the above code would look like:

```JavaSCript
import square from './utilities'
```

**Note** The function can be given any name with the import statement if it is the default import. I.e. It does not have to be the same name as in the original file.

All exports can also be grouped together as one line of code as the last line of code in a file.

```JavaScript
//utilities.js
export { add, name, square as default }
```

## Environments and Source Maps

There are two modes available for Webpack. Development and production mode. The type of mode is determined by the CLI command so it is setup in the scrips section of package.json as follow:

```JavaScript
"scripts": {
    "dev-server": "webpack-dev-server --mode development",
    "build": "webpack --mode production"
  },
```

A source map enables the browser to map the compiled code to the source code.
To setup this availability, another property is added to the webpack.config.js file so that the final file looks like this:

```JavaScript
const path = require('path')

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'public/scripts'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['env'],
          },
        },
      },
    ],
  },
  devServer: {
    contentBase: path.resolve(__dirname, 'public'),
    publicPath: '/scripts/',
  },
  devtool: 'source-map',
}
```

## Babel Polyfil

`npm install core-js regenerator-runtime`
14:08
entry: ['core-js/stable', 'regenerator-runtime/runtime', './src/index.js']

17:08
"core-js": "^3.6.5",
"regenerator-runtime": "^0.13.5",

17:39
When updating webpack.config.js line 4
use 14:08
