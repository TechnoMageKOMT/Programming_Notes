# Application Programming Interface (API)

A set of command, functions, protocols and objects that programmers can use to create software or interact with an external system.

Some important aspects of API usage is:

- Endpoints
- Paths
- Parameters
- Authentication

## API endpoint

An API endpoint is a point at which an application program interface (API) -- the code that allows two software programs to communicate with each other -- connects with the software program. APIs work by sending requests for information from a web application or web server and receiving a response.

## API Path

A Path is a unit of a REST API that you can call. A Path comprises an HTTP verb and a URL path that, when exposed, is combined with the base path (endpoint) of the API. By configuring the Path, you define how the API is exposed to your developers.

## API Parameters

API parameters are the variable parts of a resource. They determine the type of action you want to take on the resource. Each parameter has a name, value type ad optional description. ... In simple terms, API parameters are options that can be passed with the endpoint to influence the response. These appear after the ? in the url. This is usually in the form of a key value pair that is seperated by a '=' sign. E.g., ?contains=debugging. If there are more than one query, they are sepearetd by '&' symbols.

## API Authentication

The API key is usually a long series of numbers and letters that you either include in the request header or request URL. When the client authenticates the API key, the server stamps their identity and allows them to access data.
