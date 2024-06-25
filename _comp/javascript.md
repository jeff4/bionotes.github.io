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
* p. 10: invoking http.createServer() method to create an httpServer object that we named 'http'.
	* p. 11-12 explanation about how JS lets you implicitly create anonymous functions with local scope (see the *say()* method created on p. 10). In JS, since functions can just be values, you can "pass functions around". To better understand this, examine the 2 implementations on p. 11-12 with an implicit function passing version of creating an http.Server object and another explicit function creation version of the http.Server object.
* p.12-13 explanation of how JS is single-threaded and therefore requires the asynchronous, event-driven model unlike many other languages. For example, an http server implemented in PHP would spawn a new thread for every incoming client http request.
	* Also review Felix Geisendoerfer's [post](http://debuggable.com/posts/understanding-node-js:4bd98440-45e4-4a9a-8ef7-0f7ecbdd56cb) to better understand how asynch Node and JS works.
* p. 15-16 experimented with packaging asynch code into different modules / js files.
	* created jeff_server.js file with *exports.start = start;* as final expression
	* index.js file just has 2 commands: *var imac_server = require("./jeff_server");* and *imac_server.start();*

## David Flanagan, O'Reilly: JavaScript – The Definitive Guide, 7e 
### 13 on Asynchronous JavaScript p. 602
* Discussion of implementing asynch, event-driven for client side and server side JS.
* Prior to ES6, introduced in 2015, asynch a little more manually implemented. But ES6 introduced [Promises](https://www.freecodecamp.org/news/javascript-promises-explained/). It seems that Kiessling doesn't discuss Promises at all in his first book; there are only a few references to Promises in book 2.
### 13.1 Asynch Programming with Callbacks
#### 13.1.4 Callbacks and Events in Node p. 608
* Node’s *fs.readFile()* function takes a two-parameter callback as its last argument. It reads the specified file asynchronously and then invokes the callback. If the file was read successfully, it passes the file contents as the second callback argument. If there was an error, it passes the error as the first callback argument. In this example, we express the callback as an arrow function, which is a succinct and natural syntax for this kind of simple operation.  
* Node also defines a number of event-based APIs. p.609


## Kyle Simpson - You Don’t Know Javascript Yet, 2e

### [Get Started](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/README.md)
* <del>Chapter 1 - What is Javascript?</del>
* [Chapter 2 - Surveying JS](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch2.md)
* [Chapter 3 - Digging to the Roots of JS](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch3.md)
* [Chapter 4 - The Bigger Picture](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch4.md)
* [Appendix A - Exploring Further](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/apA.md)
* [Appendix B - Practice!](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/apB.md)

### [Scope & Closures](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/README.md)
* [Foreward](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/foreword.md)
* [Chapter 1 - What's the Scope?](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch1.md)
* [Chapter 2 - Illustrating Lexical Scope](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch2.md)
* [Chapter 3 - The Scope Chain](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch3.md)
* [Chapter 4 - Around the Global Scope](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch4.md)
* [Chapter 5 - The (Not So) Secret Lifecycle of Variables](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch5.md)
* [Chapter 6 - Limiting Scope Exposure](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch6.md)
* [Chapter 7 - Using Closures](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch7.md)
* [Chapter 8 - The Module Pattern](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch8.md)
* [Appendix A: Exploring Further](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/apA.md)
* [Appendix B: Practice](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/apB.md)

### [Objects and Classes](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/README.md)
* [Foreward](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/foreword.md)
* [Chapter 1 - Object Foundations](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/ch1.md)
* [Chapter 2 - How Objects Work](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/ch2.md)
* [Chapter 3 - Classy Objects](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/ch3.md)
* [Chapter 4 - This Works](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/ch4.md)
* [Chapter 5 - Delegation](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/objects-classes/ch5.md)




### [Types and Grammar](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/types-grammar/README.md) 
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

## 2024 Log
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

### 6/19/2024
#### setting up authentication
* See dialog in ChatGPT with suggested Astro code.
* From [this DevTo post](https://dev.to/itsabdessalam/password-protect-your-site-with-netlify-and-github-actions-1aah), I found these options for securing a site via Netlify--possibly with minimal or zero code changes to GitHub itself. [Main Netlify article](https://docs.netlify.com/security/secure-access-to-sites/)
	1. [Authenticate with Netlify Identity](https://docs.netlify.com/security/secure-access-to-sites/identity/)
	1. [Basic authentication with custom headers](https://docs.netlify.com/security/secure-access-to-sites/basic-authentication-with-custom-http-headers/)o 
	1. [Use OAuth provider tokens on site](https://docs.netlify.com/security/secure-access-to-sites/oauth-provider-tokens/) 
	1. [Basic password protection vs. team login protection](https://docs.netlify.com/security/secure-access-to-sites/site-protection/#basic-password-protection-versus-team-login-protection) 
	1. [Protect your site with a single shared password](https://docs.netlify.com/security/secure-access-to-sites/site-protection/#protect-your-site-with-a-basic-password) 
* Also, this is an interesting [Oct 2023 post](https://github.com/lucia-auth/lucia/discussions/1231) by the creator of the Lucia auth library. Found at 1:33 of this [YouTube video](https://www.youtube.com/watch?v=S37uRvBr65k)

### 6/20/2024
* Created dev.to account and found this April, 2024 [article](https://dev.to/snikidev/astrojs-as-an-alternative-to-nextjs-pushing-the-limits-30ga) by Nikita Kakuev on how the Astro approach (if not necessarily the Astro framework) is the future. "The future is simple, vanilla JS because simplicity always wins."
* Found this 2022 piece by Stas Klymenko with a [Node.js Roadmap for Beginners](https://dev.to/hellnar/nodejs-roadmap-for-beginners-25ml). Starts with theory/fundamentals bfore building CRUD / MERN servers. Also covers authentication of JWT vs. Sessions.
* Started rereading Flanagan's O'Reilly book on Javascript, 7th Edition (2020).
* Up to pg. 53 of SVP 'Javascript, Beginner to Pro' (2021).
* See also these [NodeJS Learning Resources](https://nodejs.org/en/about/get-involved). No Discord channel for Node apparently.
* from 6/24, see this [reddit answer](https://www.reddit.com/r/learnjavascript/comments/wthq0b/best_way_to_learn_javascript/), esp the Intermediate section.

#### datastructures
* Table comparing the names used in various languages for common data structures

|             | **Array**    | **Map**          | **Set**       |
|-------------|--------------|------------------|---------------|
| **JavaScript** | array        | map              | set           |
| **Python**     | list         | dict             | set           |
| **Java**       | Array / ArrayList | HashMap          | HashSet       |
| **CS**         | Dynamic Array | Hash Table / Associative Array / Dictionary | Hash-Set      |

#### explanation of differences between JS and Python for arrays, maps, and sets
Here are the definitions for the specified items along with their equivalent data structures or objects in Python, including differences:

1. **Array**
	*  **JavaScript Definition:** An `Array` is an ordered collection of values (elements) that are indexed by integers. Each element in an array has a specific position, starting from index 0. Arrays can store elements of any type, including other arrays, objects, or primitive values.
		*  **Example:**
		     ```javascript
		     let fruits = ["apple", "banana", "cherry"];
		     console.log(fruits[1]); // Output: banana
		     ```
	* **Python Equivalent:** `list`
		* **Definition:** A `list` in Python is an ordered collection of elements that can be of any type. Lists are indexed by integers, starting from index 0, similar to JavaScript arrays.
		* **Example:**
		       ```python
		       fruits = ["apple", "banana", "cherry"]
		       print(fruits[1]) # Output: banana
		       ```
	* **Differences:** Python lists can also hold elements of any type, including other lists and objects, just like JavaScript arrays. Both data structures are dynamic in size and allow for element modifications.

2. **Map**
	*  **JavaScript Definition:** A `Map` is a collection of key-value pairs where both keys and values can be of any type. Unlike plain objects, which use strings as keys, maps can use objects, functions, and other data types as keys. Maps maintain the order of their elements based on the order of insertion.
		* **Example:**
			```javascript
			let map = new Map();
			map.set('name', 'Alice');
			map.set('age', 30);
			console.log(map.get('name')); // Output: Alice
			```
	* **Python Equivalent:** `dict`
		* **Definition:** A `dict` (dictionary) in Python is a collection of key-value pairs where keys can be of any immutable type (e.g., strings, numbers, tuples), and values can be of any type. Dictionaries maintain insertion order since Python 3.7.
		* **Example:**
		```python
		info = {'name': 'Alice', 'age': 30}
		print(info['name']) # Output: Alice
		```
	* **Differences:** Python dictionaries only allow immutable types as keys, while JavaScript maps allow any type of keys. Both structures maintain insertion order and allow for dynamic addition and modification of elements.

3. **Set**
	* **JavaScript Definition:** A `Set` is a collection of unique values. Unlike arrays, sets do not allow duplicate elements. Sets can store values of any type and maintain the order of insertion.
		* **Example:**
		```javascript
		let set = new Set();
		set.add(1);
		set.add(2);
		set.add(2); // Duplicate value, won't be added
		console.log(set.size); // Output: 2
		```
	* **Python Equivalent:** `set`
		* **Definition:** A `set` in Python is an unordered collection of unique elements. Sets do not allow duplicate values and can store elements of any immutable type.
		* **Example:**
		```python
		s = set()
		s.add(1)
		s.add(2)
		s.add(2) # Duplicate value, won't be added
		print(len(s)) # Output: 2
		```
	* **Differences:** Both JavaScript sets and Python sets store unique values and do not allow duplicates. JavaScript sets maintain insertion order, while Python sets are unordered collections. Both support basic set operations like union, intersection, and difference.

### 6/20/2024
* Restarted Chapter 2 of Sampson "You Don't Know Javascript Yet".
* Verified that I have working Hello World across all machines in both the terminal and browser, using Firefox Developer Tools to view console there. cmd-option-io.
* Up to p. 49 of Flanagan. Wrote simple programs with arrays and functions and used node to print out to `console.log();`.
* Flanagan talks about arrow functions `=>` in ES6 and later on p. 50.
* Out of curiousity, began looking at Maps, Chapter 11, p. 485

### 6/23/2024
* Got Flanagan's histogram program working (Example 1-1, p. 56). See proj-2.
* Completed miles --> km program in SVP p. 43 (end of Chap 2).
* Next step: continue with SVP chapter 3.
* Up to p. 53 in SVP chapter 3; about to begin using Array methods.
    * Note also there are good reasons why a javascript does not have a simple equivalent to this Objective C method `NSStringFromSelector`. Need to do something like `let arrayName = Object.keys({arr})[0]`. and then reference `arrayName` later in console.log(), per [this answer](https://stackoverflow.com/a/52598270). For byVal and byRef discussion see [this answer](https://stackoverflow.com/a/51005683)

```
let arr = [1, 2, 3];
let arrayName = Object.keys({arr})[0];
console.log(arrayName);
```



### 6/24/2024
* splice() on SVP p.54. First argument indicates which index location the splice will begin. Second argument indicates how many existing entries (starting at the point of splicing--will be deleted). Note that if you accidentally delete more entries than exist in the original array, splice() will *not* throw an error; it will just delete all the elements available to the end of the array (going to the right edge).
* Completed practice exercise 3.2, shopping list, SVP p. 59.
* completed multi-dimensional arrays, seei `7array-multidimensional.js`
* Completed up to Object p.63.
* Up to Arrays in Objects p. 65

### 6/25/2024
* Completed Chapter 3, now on SVP Chapter 4 'Control Flow'.
* Goal is to finish everything before Chapter 8 (build in JS methods like Array Methods, String Methods, etc.)
    * Chap 4 - if/else
    * Chap 5 - loops
    * Chap 6 - Functios
    * Chap 7 - Classes
* Unary operators are like `i++`. Binary operators require two operands like `1 + 1`. Ternary operators (SVP p. 76) require 3 operands like ` age<18  ?  console.log("denied") :  console.log("admitted");`    
* SVP p. 76. Remember-- *condition* **?** *statement associated with true* *:** *statement associated with false*
	* aka if *operand1 is true*, then *execute operand 2*. Otherwise, *execute operand3*. 
