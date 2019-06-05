# ExpressJS-Notes

___

## Routing

`Routing` refers to how an application’s endpoints (URIs) respond to client requests.

You define routing using methods of the Express app object that correspond to HTTP methods.

These routing methods specify a callback function (sometimes called “handler functions”) called when the application receives a request to the specified route (endpoint) _and_ HTTP method. 

In other words, the application “listens” for requests that match the specified route(s) **and** method(s), and when it detects a match, it calls the specified callback function.

In fact, the routing methods can have more than one callback function as arguments. (Must provide the `next` argument and call the `next()` function.)

```js
// Basic route example
var express = require('express');
var app = express();

// respond with "hello world" when a GET request is made to the homepage
app.get('/', function (req, res) {
  res.send('hello world')
});
```

___

### Route Methods

A route method is derived from one of the HTTP methods, and is attached to an instance of the `express` class.

The following example shows routes that are defined for the `GET` and the `POST` methods to the root of the app.

```js
var express = require('express');
var app = express();

// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage')
});

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage')
});
```

___

#### Route Paths

Route paths, in combination with a request method, define the endpoints at which requests can be made. 

Route paths can be strings, string patterns, or regular expressions.

Query strings are not part of the route path.

Examples:
```js
// String based route path
app.get('/about', function (req, res) {
  res.send('about');
});

//  This route path will match requests to /about.
```

```js
// String pattern route path
app.get('/ab+cd', function (req, res) {
  res.send('ab+cd');
});

//  This route path will match abcd, abbcd, abbbcd, and so on.
```

```js
// Regular expression route path
app.get(/.*fly$/, function (req, res) {
  res.send('/.*fly$/');
});

//  This route path will match butterfly and dragonfly, but not butterflyman, dragonflyman, and so on.
```

___

### Route Parameters

Route parameters are named URL segments that are used to capture the values specified at their position in the URL. 

The captured values are populated in the `req.params` object, with the name of the route parameter specified in the path as their respective keys.

```
Route path: /users/:userId/books/:bookId
Request URL: http://localhost:3000/users/34/books/8989
req.params: { "userId": "34", "bookId": "8989" }
```

To define routes with route parameters, simply specify the route parameters in the path of the route as shown below.

```js
app.get('/users/:userId/books/:bookId', function (req, res) {
  res.send(req.params)
});
```



___

### Route Handlers



___

### Response Methods

`res.end()` - End the response process.

`res.json()` - Send a JSON response.

`res.redirect()` - Redirect a request.

`res.render()` - Render a view template.

`res.send()` - Send a response of various types.

`res.sendFile()` - Send a file as an octect stream

`res.sendStatus(`) - Set the response status code and send it as a string in the response body.


