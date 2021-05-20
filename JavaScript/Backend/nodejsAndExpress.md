# Nodejs and Express

## REPL - Read, evaluate, print loops

To access Node.js' REPL enter the command node in the terminal. The functionality is the same as that of the single line interpreter that is found in the console of browsers. To exit REPL, simply type .exit.

## Native Node Modules

There are native modules that are included with Node.js "out of the box". To access these they first have to be "required". An example would be the file system module which is needed to interact directly with the PCs file system. The code to require this module would be:

```JavaScript
//jshint esversion:6
const fs = require('fs');
```

The syntax for all modules and code associated with them are found in the documentation at nodejs.org

## Copying a file using the fs module

```JavaScript
fs.copyFileSync('sourceFile', 'destinationFile')
```

## Node Package Manager (NPM)

There are a multitude of external modules or packages available for nodejs as well and NPM is the largest package manager in the world dedicated to these. These packages are pre-written code that is simply incorporated into one's own code instead of having to write every bit of code from scratch.

To make use of npm packages issue the command `npm init` in the terminal while in the current project's folder. (This is done from scratch for every new project). A seperate `package.json` file is automatically created during this process.

To find packages simply search for them at www.npmjs.com. There is installation and usage instructions included for each package. When a package is installed and "required", it is automatically included as a dependency in the relevant `package.json` file.

## Creating anExpress server

Create folder with a new file `app.js` file in it. Initialise npm while in the new folder with the command `npm init`. This will create a new `package.json` file as discussed above.

Express documentation can be found at [https://expressjs.com].

To install Express and body-parser `$ npm install express request body-parser`. This will also be done for every new project or App.

Click on 'Getting Started' link on their website for instructions on the installation process of express if needed.

Once installed enter the following code in `app.js`

```JavaScript
//jshint esversion:6

const express = require("express");

const app = express();

app.listen(3000)  //The listen() method tells it to listen on a specific port (3000) for any http requests that gets sent to the server
```

Once this code is saved, we have now built the barebones of an express server. To run the server simply run `app.js` from the command line with `node app.js`.

To trigger a comment in the console that the server is running simply add a callback function to the listen() method:

```JavaScript
app.listen(3000, function(){
  console.log('Server started on port 3000');
});
```

## The GET request: Handling requests and responses

The get() method is a method that comes with Express to handle incoming requests and responses and it is added just above the listen() method (see above).

```JavaScript
app.get('/', function(req, res){
  res.send('Hello World');
});
```

The server can be connected to locally by typing `localhost:3000` in the browser address bar.

The `/` refers to the home route. To created additional routes, additional get() methods should be applied.

```JavaScript
app.get('/contact', function(req, res){
  res.send('Contact me at johann@gmail.com')
})
```

Each new route would just be added as required.

## Express Template (All files will have these components)

```CLI
npm init
npm i express body-parser
```

```JavaScript
//jshint esversion:6
const express = require('express')
const bodyParser = require('body-parser')

const app = express()

app.use(bodyParser.urlencoded({extended: true}))

app.get('/', function(req, res) {
  res.send('Hello')
  or
  res.sendFile(__dirname + '/index.html')
  etc
})

app.listen(3000, function(){
  console.log('Server started on port 3000)
})
```

## nodemon Utility

The nodemon utility is an npm utility that will monitor for any changes in you source code and automatically restart your server.

Installation ` sudo npm install -g nodemon`. This is done only once per PC and is a global installation so nodemon can be run from anywhere in the filing structure.

After the installation use `nodemon app.js` to start server instead of `node app.js`.

## res.sendFile() method

This is to send a file when a get request is received in place of sending the "Hello World" and other text messages that we have used so far.

Refer: 'API reference' link on the Express website. Then click on 'Response' and then 'res.sendFile()'.

Takes in as argument a filepath. Use constant `__dirname` which will automatically populate the absolute file path that the server is running from. The file name is then concatenated with a +:

```JavaScript
app.get('/', function(req, res){
  res.sendFile(__dirname + '/index.html);
});
```

## Processing Post Requests with Body Parser

HTTP return codes cheat sheet (refer Wikipedia for full list):

- `1**` Hold on (International responses)
- `2**` Here you go (successful responses)
- `3**` Go away (security issues) (Redirects)
- `4**` You fucked up (Client errors)
- `5**` I fucked up (Server errors)

Reminder: `method` attribute when defining form input fields. If this is `post` then a way should be defined on the server for the handling of these requests.

```JavaScript
app.post('/', function(){
  res.send('Thanks for posting that');
});
```

In order to tap into the pieces of data entered into the form fields and "posted" to the server another npm packaged is needed called 'body-parser'. Install by entering command: `sudo npm install body-parser`. This will be done for every new project.

Once installed it needs to be required:

```JavaScript
const bodyParser = require('body-parser');
```

After require, our app needs to be setup to use it. body-parser Has a couple of modes. Eg `.text`, \_`.json`, `.urlencoded`. The latter is used when you are trying to grab data from a form.

```JavaScript
app.use(bodyParser.urlencoded({extended: true}))
```

The `extended: true` section of the code allows the posting of nested objects. This line of code needs to be included whenever body-parser needs to be used.

Body-parser allows you to go into any of your routes and tap into `req.body` which contains the form data that was "posted".

The following is an example where two text input fields were submitted with the HTML "name" attributes num1 and num2:

```JavaScript
app.post('/', function(req, res){
  const num1 = Number(req.body.num1);
  const num2 = Number(req.body.num2);
  const result = num1 + num2;
  res.send(`The result of the calculation is ${result}`);
});
```

## Send get request to external server

[https://twilio.com/blog/2017/08/http-requests-in-node-js.html]

The first option is the native https module within nodejs is the best since all other options are external npm packages.

[https://nodejs.org/api/https.html] Several options are listed. Click on the `https.get(url[,options][,callback])` option for information on its usage.

To set up the send get request change the root get route to:

```JavaScript
app.get('/', function(req, res){

  const url = "The API url used in the Postman app"

  https.get(url, function(response){
    console.log(response.statusCode)
  })
})
```

This example will return the http status code (see HTTP return codes above). All codes are available on the MDN websites.

The URL is obtained from the API documentation and guidelines of the website server to whom the request is sent.

## Searching through data received res.on() method

To retrieve the raw data that was returned add the .on() method to the code.

```JavaScript
app.get('/', function(req, res){

  const url = "The API url used in the Postman app"

  https.get(url, function(response){
    console.log(response.statusCode)

    response.on('data', function(data){
      console.log(data);
    })
  })
})
```

The result will be in hexadecimal format and needs to be converted to JSON.

```JavaScript

app.get('/', function(req, res){

  const url = "The API url used in the Postman app"

  https.get(url, function(response){
    console.log(response.statusCode)

    response.on('data', function(data){
      const weatherData = JSON.parse(data);
      console.log(weatherData)
    })
  })
})
```

Individual values in the resultant object is simply accessed using normal object methods.

```JavaScript
app.get('/', function(req, res){

  const url = "The API url used in the Postman app"

  https.get(url, function(response){
    console.log(response.statusCode)

    response.on('data', function(data){
      const weatherData = JSON.parse(data);
      const temp = weatherData.main.temp;
      console.log(temp)
    })
  })
})
```

To see the structure of the object in order to find the required data, copy the `url` in a Google browser and view it with the JSON Viewer Pro extension. (Note: Firefox version is very limited so rather use Google to find the paths to data if needed)

## Using Express to Render a Website with Live API Data

**NB** There can only be one res.send() method in each app.get(), but that is not the case with res.write() so multiple sends will be handled as follow

```JavaScript
app.get('/', function(req, res){

  const url = "The API url used in the Postman app"

  https.get(url, function(response){
    console.log(response.statusCode)

    response.on('data', function(data){
      const weatherData = JSON.parse(data);
      const temp = weatherData.,main.temp;
      const weatherDescription = weatherData.weather[0].description
      const icon = weatherData.weather[0].icon
      const imageURL = `http://openweathermap.org/img/wn/${icon}@2x.png`
      res.write(`<h1>The temperature in Johannesburg is ${temp} degrees celcius.`)
      res.write(`<p>The weather is currently ${weatherDescription}.</p>`)
      res.write('<img src' + imageURL + '>')
      res.send()
    })
  })
})
```

## Final "Weather App" solution

### HTML

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Weather App</title>
  </head>
  <body>
    <form action="/" method="post">
      <label for="cityInput">City Name: </label>
      <input type="text" name="cityName" id="cityInput" />
      <button type="submit">Go</button>
    </form>
  </body>
</html>
```

```JavaScript
const express = require('express')
const https = require('https')
const bodyParser = require('body-parser')

const app = express()

app.use(bodyParser.urlencoded({ extended: true }))

app.get('/', function (req, res) {
  res.sendFile(__dirname + '/index.html')
})

app.post('/', function (req, res) {
  console.log(req.body.cityName)
  const query = req.body.cityName
  const apiKey = ''
  const unit = ''
  const url =
    'https://api.openweathermap.org/data/2.5/weather?q=' +
    query +
    '&appid=*****************API ID******************'

  https.get(url, function (response) {
    console.log(response.statusCode)

    response.on('data', function (data) {
      const weatherData = JSON.parse(data)
      const temp = weatherData.main.temp
      const weatherDescription = weatherData.weather[0].description
      const icon = weatherData.weather[0].icon
      const imageURL = `http://openweathermap.org/img/wn/${icon}@2x.png`
      res.write(
        `<h1>The temperature in ${query} is ${temp} degrees celcius</h1>`
      )
      res.write(`<p>Conditions: ${weatherDescription}</p>`)
      res.write('<img src=' + imageURL + '>')
      res.send()
    })
  })
})

app.listen(3000, function () {
  console.log('Server started on port 3000.')
})
```

## Serve static pages on server

A special function of Express is needed, called static. To use this function create a `public` subfolder in the project folder with `images` and `css` subfolder inside of it. Move the style.css and images to their folders. Within the HTML document give file paths from the public level (I.e., not including public.) E.g., `css/styles.css` and `images/image.png`.

Once this is done, add the code `app.use(express.static('public'))` above the app.get() statements.

## Example of logic used in app.get

```JavaScript
const express = require('express')
const bodyParser = require('body-parser')

const app = express()

app.get('/', function(req, res){
  const today = new Date()
  if (today.getDay() == 6 || today.getDay() == 0) {
    res.send('Yay! It is the weekend.')
  }else {
    res.send('Boo! I have to work.')
  }
})

app.listen(3000, function(){
  console.log('Server started on port 3000')
})
```

**NB Note** Multiple res.send are not accepted. The browser sees a res.send as the final send.
