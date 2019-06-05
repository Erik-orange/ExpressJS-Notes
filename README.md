# ExpressJS-Notes

___

## Routing

`Routing` refers to how an application’s endpoints (URIs) respond to client requests.

You define routing using methods of the Express app object that correspond to HTTP methods.

These routing methods specify a callback function (sometimes called “handler functions”) called when the application receives a request to the specified route (endpoint) _and_ HTTP method. 

In other words, the application “listens” for requests that match the specified route(s) **and** method(s), and when it detects a match, it calls the specified callback function.

```js
var express = require('express')
var app = express()

// respond with "hello world" when a GET request is made to the homepage
app.get('/', function (req, res) {
  res.send('hello world')
})
```
