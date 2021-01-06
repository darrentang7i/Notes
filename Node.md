# Node.JS
- Node.js is single threaded, asynchronous
- process.argv array allows us to pass parameters into the program
- can use process.stdin for standard input, process.stdout for standard output, need to output \n at the end 
- setTimeout(callbackFunc, waitTime) allows us to set a time out of waitTime ms
- using modules can make our code cleaner, require in modules to use them

EventEmitter allows us to emit, or raise, custom events
- emitter.emit emits the event, and emitter.on(eventName, calllback) allows us to handle this event
- For example. everytime user answers a question, we can emit the answer, and tell the program to do something with the answers with emitter.on(), this is a listener for an event

```js
const emitter = new events.EventEmitter();
emitter.on("trigger", (a, b) => {
  // do something
});

//this will raise an event for the emitter handler above
emitter.emit("trigger", "text1", "text2");
```

## Express.js

Express is a framework for Node.js, it provides mechanisms to:
1) write handlers for GET, POST, DELETE, etc. requests 
2) Set common web app settings, ie. port to use for connecting, location of templates used for rendering the response
3) Add additional request processing "middleware" 

### A sample Hello World Program
```js
//imports the express module, and creates an express app
var express = require('express');
var app = express();

//route definition, callback funtion invoked whenever there is an HTTP GET request to path ('/') relative to the site route
app.get('/', function(req, res) {e
  res.send('Hello World!');
});

//starts up server on port '3000', now accessible through localhost:3000
app.listen(3000, function() {
  console.log('Example app listening on port 3000!');
});
```

- app.use allows u to add mmiddleware to your path
- to load static files (ie. a jpg, pdf, etc.), u can do: 
```js
//to link images folder on path images
app.use('/images', express.static('images'));
```
then, u can simply do something like https://localhost:3000/images/image.jpg to display the images.

## Parameters 
To pass a parameter into the path, parameters are marked by a `:`
```js
app.get('/item/:id', (req, res) => {
  console.log(req.params.id);
  let user = Number(req.params.id); //converts string to int
  res.send(data[user])
})
```
- In the above example, if we access localhost:3000/item/04, assuming data is a JSON object of user objects, each with an id. This will send the user with id 4.


## Multiple callback functions in route handlers
To have multiple callback functions, use the next() call.
```js
app.get('/me', callback1, callback2, async (req, res) => {
  res.send("hello");
}
const callback1 = (req, res, next) => {
  //do something
  next();
}
const callback2 = (req, res, next) => {
  //do something
  next();
}

```
Here, when there is a get request to the `/me` route, callback1 will be invoked, followed by callback2, before it finally goes back into the app.get callback function and sends a response. Callback1 and callback2 in this case are essentially middleware functions.

## Common routing methods
- res.send sends anything
- res.json sends json
- res.end() ends a call to the API
- res.redirect('https://www.google.ca') will redirect you to the link
- res.download('images/image.jpg') will download a file 

## Routing: Chaining
You can group all handlers for the same route together with app.route()
```js
app.route('/path')
    .get((req.res) => {
      res.send('a get request');
    })
    .put((req, res) => {
      res.send('a put request');
    })
    .delete((req, res) => {
      res.send('a delete request');
    }
  );

```

## Middleware
A function that has access to the req and res of the request.