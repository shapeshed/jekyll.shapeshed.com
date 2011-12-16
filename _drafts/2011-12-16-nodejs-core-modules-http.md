---
layout: post
title: Node.js core modules - HTTP
description: The HTTP module is a low level way of creating HTTP clients and servers
date: 2011-12-16 07:41
categories: 
- Node.js
- JavaScript
---

## Low level and elegant

Node.js has a first class module for creating HTTP clients and servers. The Module supports HTTP 1.1 by default 

## Creating HTTP servers

The approach that Node.js takes in serving applications is different from other frameworks. In [Rails][1] and [Django][2] for example the web server is separate from the application. You might serve Rails from [Unicorn][3] and [Nginx][4] or Django from [Apache][5] with [mod\_python][6]. Node.js puts the server in the same process as your application meaning there is one single process for the application and web server. 

The API is designed around the request and response objects and callbacks. For a web server the request is the incoming request. This could be a web browser or a search engine robot requesting data. The response object is the data that the web server returns to the client (or requester). The pattern of requesting and responding is one that sits well with JavaScript's Evented features. 

You might be familiar with the `onclick` event in JavaScript. Here is an example where the code listens for the event of a user clicking an element in the DOM and then doing something.

``` javascript An onclick event in JavaScript
trigger = document.getElementById("trigger");
if (!trigger) { return;}
trigger.onclick = function(){
  alert("I was listening! I'm here!")
}
```

This evented style of programming is applied to Node.js everywhere and maps well to an HTTP cycle. If you think about it a web server is very similar to to the tiny JavaScript function above:

* It listens for an incoming event
* It responds accordingly
* It continues to listen for the same event again

This is commonly referred to as the event loop and although it is very simple has strong implications. In more traditional web servers like Apache a combination of threads and processes is used to serve responses. For each request a new thread is spawned. The approach that Node.js takes is to use a single process and utilise the event loop. This approach means that as much as possible nothing should block the Node.js process as this would result in everything being blocked. 

The callback style of programming ensures that this happens. You might also hear this referred to as asynchronous programming. Consider the Node.js Hello World server:

``` javascript Hello World Node.js Server
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(5000, "0.0.0.0");
console.log('Server running at http://0.0.0.0:5000/');
```

Let's examine what's happening here:

* Firstly the HTTP module is required. This gives the script access to all of the functions in the HTTP module. This is assigned to a variable so it can be used within the script. 
* Next the `createServer` function is called, taking an anonymous function as an argument. The anonymous function takes the request and response as arguments and is key to the callback style of programming. This sets up a listener much like the `onclick` example earlier in this article. 
* Whenever the server receives a request this anonymous function will be called and the response will be sent. A request to the `createServer` function triggers a callback to be fired on the anonymous function and as a result the response will be sent. 
* The `writeHead` function is called on the response object to set the response code to 200 and the content type to plain text. 
* The `end` function is called on the response object to tell the server that the response is complete and should be sent to the client.
* The `listen` function is called on the server object and declares which IP address and port the server should bind to. 
* The final line does nothing other than log that the server is running to the terminal. 

[1]: http://rubyonrails.org/
[2]: https://www.djangoproject.com/
[3]: http://unicorn.bogomips.org/
[4]: http://nginx.com/
[5]: http://httpd.apache.org/
[6]: http://www.modpython.org/

