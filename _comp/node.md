---
title: Node.JS 2022 onwards
permalink: /node/
---

# NodeJS -- 2022 Log

## Kiessling Book 1 on Node, Summer 2022
* p. 7 - What do we need to implement: what tasks must be fulfilled?
	1. HTTP Server to serve webpages
	2. A Router so our server can provide different responses based on different requests. In other words, a component that maps different requests to different responses
	3. Request Handlers to actually fulfill requests as mapped by the Router
	4. Request Data Handling that formats incoming POST requests received by the Request Handlers from the client browser.
	5. View Logic (aka the V in MVC). This takes the URL's obtained by the Request Handlers in response to requests and needs to be presented such that it can be viewed in the user's browser
	6. Finally UPLOAD HANDLER that knows how to ingest pictures uploaded by users.  
* p. 10: invoking http.createServer() method to create an httpServer object that we named 'http'.
	* p. 11-12 explanation about how JS lets you implicitly create anonymous functions with local scope (see the *say()* method created on p. 10). In JS, since functions can just be values, you can "pass functions around". To better understand this, examine the 2 implementations on p. 11-12 with an implicit function passing version of creating an http.Server object and another explicit function creation version of the http.Server object.
* p.12-13 explanation of how JS is single-threaded and therefore requires the asynchronous, event-driven model unlike many other languages. For example, an http server implemented in PHP would spawn a new thread for every incoming client http request.
	* Also review Felix Geisendoerfer's [post](http://debuggable.com/posts/understanding-node-js:4bd98440-45e4-4a9a-8ef7-0f7ecbdd56cb) to better understand how asynch Node and JS works.
* p. 15-16 experimented with packaging asynch code into different modules / js files.
	* created jeff_server.js file with *exports.start = start;* as final expression
	* index.js file just has 2 commands: *var imac_server = require("./jeff_server");* and *imac_server.start();*

## David Flanagan, O'Reilly: JavaScript 7e, Summer 2022
### 13 on Asynchronous JavaScript p. 602
* Discussion of implementing asynch, event-driven for client side and server side JS.
* Prior to ES6, introduced in 2015, asynch a little more manually implemented. But ES6 introduced [Promises](https://www.freecodecamp.org/news/javascript-promises-explained/). It seems that Kiessling doesn't discuss Promises at all in his first book; there are only a few references to Promises in book 2.
### 13.1 Asynch Programming with Callbacks
#### 13.1.4 Callbacks and Events in Node p. 608
* Node’s *fs.readFile()* function takes a two-parameter callback as its last argument. It reads the specified file asynchronously and then invokes the callback. If the file was read successfully, it passes the file contents as the second callback argument. If there was an error, it passes the error as the first callback argument. In this example, we express the callback as an arrow function, which is a succinct and natural syntax for this kind of simple operation.  
* Node also defines a number of event-based APIs. p.609


## Other stuff from 2022
* 6/23/2022 Reinstalled Postgres and updated brew
* 6/24/2022 Decided transition from version 9 to 14 of Postgres caused too many problems. Spent significant time trying to change default port listening behavior because clients just couldn't connect to main Postgres server. Decided my needs were well met by a simple SQLite3 database instead. Built a quick and simple CRUD app with Node.js, Express, and SQLite as the data store using [this tutorial](https://medium.com/swlh/creating-a-crud-application-using-node-js-and-sqlite3-a57d4a39ab69).
	* found a few errors but with some modifications I could get this work. Also used TablePlus as a GUI db browser to verify. 
* 6/25 Built new CRUD app with MongoDB backend. Used new GUI http app to send GET/POST etc. to test and populate backend. Began using vim and VS Code [together](https://www.barbarianmeetscoding.com/blog/boost-your-coding-fu-with-vscode-and-vim).
* 6/26 Mostly finished building my first [MERN app](https://www.mongodb.com/languages/mern-stack-tutorial). 
	* Reading more about Server API Endpoints at:
		* [Hubspot](https://blog.hubspot.com/website/api-endpoint)
		* [SmartBear](https://smartbear.com/learn/performance-monitoring/api-endpoints/)
	* Difference between HTTP [POST versus PUT](https://restfulapi.net/rest-put-vs-post/)
		* POST mostly equivalent to CREATE database operations. If invoked multiple times, will create multiple entries.
		* PUT mostly equivalent to UPDATE database operations. PUT method is idempotent which means if invoked multiple times, will only result in a single entry being updated with the same final value. From [this article](https://www.restapitutorial.com/lessons/idempotency.html), "From a RESTful service standpoint, for an operation (or service call) to be idempotent, clients can make that same call repeatedly while producing the same result. In other words, making multiple identical requests has the same effect as making a single request."
	* Good quick overview of [benefits of linting](https://sourcelevel.io/blog/what-is-a-linter-and-why-your-team-should-use-it), including first lint program written for Unix in 1978
* 6/27 Everything in MERN is working well. Tested multiple times and was able to add and delete records, consistently start and stop server, start and stop React front end etc.
* 6/28 Did some thinking and writing about difference between DevMarketing and DevRel. How DevRel = Evangelism + Advocacy.
* 7/04 Reinstalled Vim on Visual Studio Code. 
* 7/05 - 7/06 More vim practice.
* 7/07 Experimented more with very basic searches in vim. 
	* /[string] then *enter* then *n* to find next instance of [string]. Also realized that to find previous instance of string, type capital *N*.
	* Also, **(** and **)** by themselves move you to the beginning and end of the current sentence, respectively. This means that *d(* means delete from cursor to beginning of sentence. Conversely, *d)* means delete from cursor to the end of the current sentence.
	* More reading of Kiessling Node book 1.
* 7/08 More experimentation with vim. 10G goes to 10th line. gg beginning of document. G end of document. J to join current line with next line.
* 7/09 More building of Kiessling Node app. Built first server.js app. Began studying and thinking about http class in Node.
* 7/10 Began experimenting with Visual Mode in vim for the first time. V = switch to line-wise visual mode. Combine this with regular motion keys like j,k and then y (just once) to yank multiple lines at once (visually) and the p will allow to copy/paste.
* 7/20 Rebuilt hello world Node app to allow me to examine bitwise operations. Working well and I'm able to experiment with rather large decimal numbers and see what happens when I apply XOR operations on them.
* 7/26 Began reading about how to use registers in vim. [Good article here](https://www.brianstorti.com/vim-registers/)
* 7/27 Recorded simple first macro in vim. Turning on line numbers with :set number invoked by @n
* 8/02 Reviewed [JS learning options](https://techbootcamps.utexas.edu/blog/best-ways-to-learn-javascript/)
* 8/03 Started reading *You Don't Know Javascript, 2nd Edition*. On [Chapter 1](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch1.md).
* 8/13 Began combined review of objects, value, scope in Flanagan, Simpson, and on YouTube.
	* confirmed knowledge of back-tick and interpolated expressions in strings. read a bunch about by-ref / by-val; objects / classes / primitive data types; various types of scope and closure. Best knowledge comes from reading Kyle Simpson, supplemented by Flanagan.
* 8/14 Notes on Kiessling Node book
	* p. 10 the require() method is specific to CommonJS as a way of importing modules, files, etc.
	* Module / class / method hierarchy that leads to http.createServer() command: Node.js [**HTTP Module**](https://www.w3schools.com/nodejs/nodejs_http.asp) > createServer() method > http.Server Object. In other words, invoking [http.createServer()](https://nodejs.org/api/http.html#httpcreateserveroptions-requestlistener) createsa a [http.Server object](https://nodejs.org/api/http.html#class-httpserver).
		* Here are the W3Schools articles on [http.createServer()](https://www.w3schools.com/nodejs/met_http_createserver.asp) and [http.Server class](https://www.w3schools.com/nodejs/obj_http_server.asp) 
	* Wrote 2 simple js programs to test out implict versus explicit functions. see ~/js_lang_exercises directory and look at 1-node and 2-node.
	* Also read further into Kiessling Book 1 on implementing different versions of http server with http.createServer(), how to organize a large js program into different modules. exports.start = start; allows the start() function to be accessed by index.js.
	* Thought about various ways to change the datatype of a variable: (1) js default is coercion, (2) Java and other languages also have the concept of casting to *temporarily* change a type, (3) overall topic of type conversion. I *think* that the superset is just called type conversion of which 2 subsets are coercion and casting.
	* Everything that is not a primitive datatype is an object, an instantiation of an abstract class. Every class has a prototype it inherits from (with some minor exceptions). Because everything ultimately inherits from Object.prototype, every object has methods like toString().
* 8/16 experimented with packaging JS programs into modules with export function. Kiessling p. 15-16
* 8/17 turns out Kiessling Book 1 is shorter than expected. I skimmed through to the end of it; the second half is actually a preview of a future book.

# 2024 Log
### 4/30/2024
* Set up next.js for mindscale website.
* See also instructions on [main git page](/git-notes/)
* Following this [react-nextjs course on YouTube](https://www.youtube.com/watch?v=h2BcitZPMn4).

#### Steps for next.js
1. Use `mkdir n1` to create desired directory within demo_f
1. Navigate into new subdirectory, and type 
1. Edit newly created `package.json` file.
1. install dependencies with this command `npm install next react react-dom`
1. This has now edited the `package.json` file with a list of dependencies and versions for next, react, and react-dom.
1. Now go into `package.json` and edit to rename `test` command to `dev` command. It should say `"dev": "next dev"`.
1. Create new subdirectory and two files `/n1/app/layout.js` and `/n1/app/page.js1`.
1. Navigate to n1 and run server by typing `npm run dev` and view in browser at URL localhost:3000
1. Watched up to 10:11. Have mixed in some jsx already meow.


## 7/10/2024
* Trying to find a good library to read the source code of. Some articles analyzing Express.js.
	* Quite good [2018 article](https://blog.laputa.io/understanding-expressjs-d5ef4f4646c8) by Xiao Han. Unfortunately it's a Medium article.
	* Another [2018 article](https://www.sohamkamani.com/nodejs/expressjs-architecture/)--this one by Soham Kamani. Seems pretty good at first glance.

## 7/11/2024
## Back to Kiessling's Node books, Summer 2024
* got initial program p. 10 working. 
* Example of **anonymous function** below from p. 11. See also 2b and 2c in `/_k1-node`:

```javascript

function jhExecute( someFunction, inputString ) {
	someFunction( inputString );
}

// Calling jhExecute while defining function() as an 
// *anonymous function*.

jhExecute(

	// paramater 1
	function (word) {
		console.log(word)
	},

	// paramater 2
	"Is this an input string?"
);
```

* Let's go back to the minimal HTTP server again.
* By now it should be clear what we are actually doing here: we pass the createServer function an anonymous function.  We could achieve the same by refactoring our code to:

```javascript
let httpObj = require("http");

function onRequest( request, response) {
	response.writeHead(200, {"Content-Type": "text/plain"});
	response.write("Hello v 3a!");
	response.end();
}

httpObj.createServer(onRequest).listen(4321);
```

* Note how there is an embedded call of the onRequest() function, who's paramters are fed in from the http.listen() function call. compare `3a.js` with `2a.js`.

### Event-driven asynch callbacks p. 12
* Node's approach is different than that used in the runtimes for Java, Python, Ruby, and PHP.
* Uses the example of a database query. 
* Assume we are using a PHP web server. 
	1. The PHP server would spawn a new thread for each database request. Call it **thread1**. 
	1. It's ok if thread1 just hangs until the DB returns perhaps millions of rows, b/c the PHP server is multi-threaded.
	1. So the PHP thread can just keep spawning new threads for new requests etc. And each of the threads would no block each other, so the server would stay reponsive.
	1. The web server starts its own PHP process for every HTTP request it receives. 
	1. If one of these requests results in the execution of a slow piece of code, it results in a slow page load for this particular user, but other users requesting other pages would not be affected.
* Now, let's see the same situation with a NodeJS server.
	1. Node only has *one* process
	1. If there is a slow database query somewhere in this process, this affects the whole proces--everything comes to a halt until the slow query has finished. 
	1. This delays the experience for *every single client user* interacting with the Node server.
* To avoid this, JavaScript, and therefore Node.js, introduces the concept of event-driven, asyn- chronous callbacks, by utilizing an event loop.

#### Version 1: DB query without asynch promise
* This will be slow b/c the `Query completed!` print statement will not happen until after the DB query has returned all the rows.

```javascript
let result = database.query("Select * From big_table");
console.log("Query completed!");
```

#### Version 2: DB query using asynch promise

```javascript
database.query( 

	// param 1
	"Select * From big_table", 

	// param 2
	function(rows)  {
		let result = rows;
	}
);

console.log("Query completed!");

```

#### More commentary on asynch p. 13
* In *Version 1*, the code was synchronous. **First**, do the DB query. And then--only *after* the query is finished, **secondly** print "Query completed".
* In *Version 2*, the code is asyncronous, assuming that the `database.query()` is part of an asynch library like Node.js.
* In *V2*, the code sends teh query to the DB. But now, instead of waiting for the query to complete, the code makes a 'mental note' that says: 
	'When at some point in the future, the DB server is finished and I get back the results of the query, then I must execute the anonymous function that was passed to *database.query()*'.
* And before we hear back from the DB server, the Node server *immediately executes *console.log()* and then enters teh **event loop**.
* Node.js continuously cycles through this loop again and again whenever there is nothing else to do, waiting for events. Events like, e.g., a slow database query finally delivering its results.
* This also explains why our HTTP server needs a function it can call upon incoming requestsi-- if Node.js would start the server and then just pause, waiting for the next request, continuing only when it arrives, that would be highly inefficent. If a second user requests the server while it is still serving the first request, that second request could only be answered after the first one is done--as soon as you have more than a handful of HTTP requests per second, this wouldn’t work at all.



