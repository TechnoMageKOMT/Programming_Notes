# Ajax

Asynchronous JavaScript and XML  

jQuery offers several function to handle Ajax requests:

- $.load() (to get data from your own server)
- $.get()
- $.post()
- $.ajax()
- $.getJSON()

## Get data with Ajax

[https://jsonplaceholder.typicode.com/] - Free fake API for testing and prototyping.  

When making a request for data from a database, two things are required:

1. Method
2. URL

The URL in this  example would be [https://jsonplaceholder.typicode.com/users]. (This URL is obtained from the API documentation of the external database under normal circumstances.) To get data the GET method is used.

The code then to get the data in question using Ajax is:

```JavaScript
  const METHOD = "GET"
  const URL = "https://jsonplaceholder.typicode.com/users"

  $.ajax(URL, {
    method: METHOD,
    error: function() {
      console.log('Something went wrong');
    },
    success: function(data) {
      console.log(data);
    }
  })
```

## Post data with Ajax

The first change to the above is the method which will now be POST. The URL will again depend on the server that is used and will be specified in the API documentation, but for jsonplaceholder.typicode.com it is the same as the GET url. There are also additional fields that needs to be included with POST request. Using the same example, the POST request looks like:

```JavaScript
  const METHOD = "POST"
  const URL = "https://jsonplaceholder.typicode.com/users"
  const DB = JSON.stringify({name:"Johann",lastname:"van Vuuren"})

  $.ajax(URL, {
    method: METHOD,
    data: DB,
    dataType: "json",
    contentType: "application/json",
    error: function() {
      console.log('Something went wrong');
    },
    success: function(data) {
      console.log(data);
    }
  })
```

## getJSON() method


