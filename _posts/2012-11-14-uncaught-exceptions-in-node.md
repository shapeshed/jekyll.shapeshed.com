--- 
layout: post
title: Uncaught Exceptions in Node.js
description: Dealing with uncaught exceptions in Node.js is not straightforward
categories: 
- JavaScript
- Node.js
---

## The problem of uncaught exceptions

Because Node.js runs on a single process uncaught exceptions are an issue to be aware of when developing applications. Node.js follows a callback pattern where an error object is the first argument and data is the second argument. It is not uncommon to see examples in the documentation where an error is thrown if an error is returned by the callback.

    var fs = require('fs');

    fs.readFile('somefile.txt', function (err, data) {
      if (err) throw err;
      console.log(data);
    });

If you run this and assuming you have no file called 'somefile.txt' an error will be thrown.

  Error: ENOENT, open 'somefile.txt'

This has the effect of crashing the process to bringing down you whole application. This is by design. Node.js does not separate your application from the server. 

## How to deal with uncaught exceptions

So what's the best way of dealing with uncaught exceptions? There are many opinions floating around on this.

* You application shouldn't have uncaught exceptions. This is clearly insane.
* You should let your application crash, find uncaught exceptions and fix them. This is clearly insane.
* You should let your application crash, log errors and restart your process with something like upstart, forever or monit. This is pragmatic.
* You should start using domains to handle errors. Clearly the way to go, although this is an experimental feature of Node.

Let's look at these in a bit more detail.

### An application without uncaught exceptions

This opinion is completely bizarre to me. Applications will always have exceptions at some stage and will probably have uncaught exceptions. If you hold this opinion you push error handling onto your users and are likely to get some late night calls that the server has gone down.

### Let your application crash

The only defence I can find in this opinion is the fail fast argument. You are going to fix your application quickly if it unavailable. If an application without uncaught exceptions is denial letting your application crash is acceptance. But you are still pushing exception handling onto your users.

### Let your application crash, log and restart

With this approach you simply let your application crash in the event of an uncaught exception and use a tool like forever or upstart to restart it (almost) instantly. Because node will write the exception to STERR your can redirect this to a log file that you can use it to assess errors at a later time. The disadvantages of this are that for i/o where the error might be outside your codebase it doesn't really offer an elegant way to deal with scenarios like temporary outages or errors with networked i/o. It is a big hammer to crack a nut - restart the process and try again. 


   process.on('uncaughtException', function(err) {
      console.log('Caught exception: ' + err);
    });

  var domain = require('domain');
  var d = domain.create();
  var fs = require('fs');

  d.on('error', function(err) {
    console.error(err);
  });

  d.run(function() {
    fs.readFile('somefile.txt', function (err, data) {
      if (err) throw err;
      console.log(data);
    });
  });

