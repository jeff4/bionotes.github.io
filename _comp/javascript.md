---
title: Javascript
permalink: /javascript/
---

## Kiessling Book 1 on Node
* p. 7 - What do we need to implement: what tasks must be fulfilled?
	1. HTTP Server to serve webpages
	2. A Router so our server can provide different responses based on different requests. In other words, a component that maps different requests to different responses
	3. Request Handlers to actually fulfill requests as mapped by the Router
	4. Request Data Handling that formats incoming POST requests received by the Request Handlers from the client browser.
	5. View Logic (aka the V in MVC). This takes the URL's obtained by the Request Handlers in response to requests and needs to be presented such that it can be viewed in the user's browser
	6. Finally UPLOAD HANDLER that knows how to ingest pictures uploaded by users.  

## Flanagan 7e Definitive 

## Kyle Simpson - You Don’t Know Javascript, 2e

### [Get Started](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/README.md)
* <del>Chapter 1 - What is Javascript?</del>
* [Chapter 2 - Surveying JS](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch2.md)
* [Chapter 3 - Digging to the Roots of JS](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch3.md)
* [Chapter 4 - The Bigger Picture](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch4.md)
* [Appendix A - Explorining Further](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/apA.md)
* [Appendix B - Practice!](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/apB.md)

### [Scope & Closures](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/README.md)
* [Foreward](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/foreword.md)
* [Preface](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/preface.md)
* Chapter 1 - What's the Scope?
* Chapter 2 - Illustrating Lexical Scope
* Chapter 3 - The Scope Chain
* Chapter 4 - Around the Global Scope
* Chapter 5 - The (Not So) Secret Lifecycle of Variables
* Chapter 6 - Limiting Scope Exposure
* Chapter 7 - Using Closures
* Chapter 8 - The Module Pattern
* Appendix A: Exploring Further
* Appendix B: Practice

### [Objects and Classes](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/README.md)
* [Foreward](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/foreword.md)
* [Preface](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/preface.md)
* Chapter 1 - Object Foundations
* Chapter 2 - How Objects Work
* Chapter 3 - Classy Objects
* Chapter 4 - This Works
* Chapter 5 - Delegation




### [Types and Grammar](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/types-grammar/README.md) 
* Foreward
* Preface
* [Chapter 1 - Primitives](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/types-grammar/ch1.md)
* [Chapter 2 - Value Behaviors](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/types-grammar/ch2.md)
* [Chapter 3 - Object Values](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/types-grammar/ch3.md)



## 2022 Log
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
