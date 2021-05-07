# EJS - Embedded JavaScript Templating

Refer: [https://ejs.co]. "Using EJS with Express" heading on the home page and follow the Github Wiki page link.

## Basic setup

`npm install ejs`

In Express v4, a very basic setup using EJS would look like the following. (This assumes a views directory containing an index.ejs page.

```JavaScript
let express = require('express');
let app = express();

app.set('view engine', 'ejs');

app.get('/', (req, res) => {
  //some login producing variable foo = FOO
  res.render('index', {foo: 'FOO'});
});

app.listen(4000, () => console.log('Example app listening on port 4000!'));
```

The *.ejs file contains normal HTML but with variables from the app.js script inserted via EJS. Example:

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To Do List</title>
</head>
<body>
  <h1>The inserted varialble <%= foo %></h1>
  
</body>
</html>
```

The above shows that complex logic can be used to return variables from the express server to the HTML template file (*.ejs) by using templating.

## Scriptlet tags <% %>

This should only be used for control flow issues that affects the CONTENT of the html in *.ejs. This should not be abused for other types of logic which should be kept in the app.js file.

```Javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To Do List</title>
</head>
<body>

  <% if (kindOfDay === 'Saturday' || kindOfDay === 'Sunday') { %>
    <h1 style="color: purple;"><%= kindOfDay %> To Do List</h1>
  <% } else { %>
    <h1 style="color: blue;"><%= kindOfDay %> To Do List</h1>
  <%}%>
  
</body>
</html>
```

The tags are added line by line around JavaScript code ONLY. If two or more consequitive lines of JS code then each line is wrapped individually.
