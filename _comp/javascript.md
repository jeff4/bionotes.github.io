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
    * Chap 6 - Functions
    * Chap 7 - Classes
* Unary operators are like `i++`. Binary operators require two operands like `1 + 1`. Ternary operators (SVP p. 76) require 3 operands like ` age<18  ?  console.log("denied") :  console.log("admitted");`    
* SVP p. 76. Remember-- *condition* **?** *statement associated with true* **:** *statement associated with false*
	* aka if *operand1 is true*, then *execute operand 2*. Otherwise, *execute operand3*. 
	* aka if **op1 CONDITION is true**, then **EXECUTE op2**. Otherwise, **EXECUTE op2**.
* finished Chapter 4. Got stuck a little bit in standard input / standard output and ability to define scope of variables. And => arrow functions. Will be able to resovle this afteer I finishe Chapter 6.
* for now, on to Chapter 5, loops.
* Chapter 6, p. 119: "Variables *are* something but they don't *do* anything."
	* "In contrast, functions are actions. They are bundles of statements that can be executed when called."
	* "For more on this, see the anonymous functions section on p. 142."
* Completed up to Practice Exercise 6.3 on p. 122


### 6/26/2024
* SVP Chapter 6. Interesting exceptions and JS handling of weird parameters p. 122 - 123. **Default or unsuitable parameters**.
	* p. 125 - spread operator
	* p. 127 - rest to stuff extra parameters into a function into an array.

#### Scope
* p. 131 "it can be confusing to combine local variables and `return`. Right now, we're telling you the local variables declared inside a function are not available outside of the function, **but with `return` you can make their values available *outside* the function**. So if you need their values outside a function, you can return the values. The key word here is **values**!"
* p. 132. Declaring a variable with `var x = "foo"` means that foo is available anywhere throughout the function; even if `var x` is declared at the very end of the function.
	* In contrast, declaring `let y = "bar"` means that `bar` is *only* available within the statement block in `{...}`.
* p. 134 - Global variables. **Variables are accessible in the scope--either *function* or *block*--where they are defined...*plus* any smaller / "lower" scopes within them.**
    * A variable defined at the top level of the program is available everywhere in the program-- aka a *global variable*.
    * A variable defined outside of a function will be available *inside* that function.
* up to p.137. Partway through IIFEs.

## 6/29/2024
* Completed Chapter 6 but need to do end of chapter exercises. Back to SVP Chapter 5 on loops.
* Went back to Flanagan and completed Chapter 2: "Lexical Structure". Including reserved words, literals, semi-colons, line breaks, whitespaces, Unicode UTF-16, etc.

### Flanagan Chapter 3: Types, Values, Variables. p. 71
* p. 71 Basic types in JS:
	1. Primitive Types
	1. Object Types
	1. Weird primitive types: `null` and `primitive` and `Symbol`.
* Special kinds of objects: array, Map, Set.
* p. 73 important point: "In JS, **functions** and **classes** are themselves *values* that can be manipulated by JavaScript programs. Like any JavaScript value that is not a primitive value, functions and classes are a specialized kind of object. They are covered in detail in Chapters 8 and 9."
* p, 75, in general, don't use `var` to declare new functions. Almost always use `let` for modern code; if you are declaring a constant, use `const`.

#### Flanagan 3.3: Text p. 86
* p. 86 core type in JS for text is the *string*.
* p. 88 how to handle line breaks. Representing multiple output lines on 1-source code JS line. And also breaking a long line of text into multiple lines of a JS source code.
* p. 90 "Remember that strings are immutable in JavaScript. Methods like `replace()` and `toUpperCase()` return new strings: they do not modify the string on which they are invoked."

#### Flanagan 3.7: Object p. 104
* Note, main chapter on Object is Chapter 6, p. 250.
* p. 104 - "When a JS interpreter starts (or whenever a web browser loads a new page), it creates a new global object and gives it an initial set of properties that define: (1) *Global constants* like `undefined`, `Infinity`, and `NaN`; (2) *Global functions* like `isNaN()`, `parseInt()`, `eval()`; (3) *Constructor functions* like `Date()`, `RegExp()`, `String()`, `Object()`, `Array()`; and (4) *Global objects* like `Math` and `JSON`.
* p. 105 - "In *Node*, the global object has a property named `global` whose value is the global object itself, so you can always refer to the global object by the name `global` in Node programs." 
* p. 105 - "As of ES2020, `globalThis` is the standard way to refer to global object in any context--implemented in all browsers and Node."
* p. 105-106 - "There is a fundamental difference between **primitive values** (strings, numbers, booleans, `undefined`, `null`) and **objects** (e.g., arrays and functions).
* p. 106. Primitives are *immutable* and compare by *value*.
* p. In contrast, Objects are *mutable* and are *not* compared by value. e.g., 2 arrays that have the same elements in the same locations are *not* equal.
	* Objects are compared *by reference*. p. 107

#### Flanagan 3.9: Type Conversions p. 108
* e.g., when JS expects a Boolean value and we supply it with a value of any type, JS will not error; it will convert "truthy" values into `true` and "falsy" values into `false`.
* p. 109-110, Table 3-2: JS type conversions.
* Section 3.9.1: Conversions and Equality p. 111. Just always use `===` to be safe.
* Section 3.9.2: Explicit Conversions p. 112. Simplest way to change type is to use `String()`, `Number()`, `Boolean()`. E.g.:
	*  Convert the boolean value `true` into a string value by typing: `String(true);` or equivalently `true.toString();`. Which both produce output of `"false"` as a String value.

#### Flanagan 3.9.3: Converting between Objects and Primitive Types 
* p. 115 - 122
* Complex and multiple sections. Read more closely later if you find yourself doing this. Skip for now.


#### Flanagan 3.10: Declaring Variables, Initialization, Assignment p. 122
* When to use constants? see Box on p. 123-124.
	> There are two schools of thought about the use of the const keyword. 
	> One approach is to use `const` only for values that are fundamentally unchanging, like the physical constants shown, or program version numbers, or byte sequences used to identify file types, for example. 
	> Another approach recognizes that many of the so-called variables in our program don’t actually ever change as our program runs. In this approach, we declare everything with `const`, and then if we find that we do actually want to allow the value to vary, we switch the declaration to `let`. This may help prevent bugs by ruling out accidental changes to variables that we did not intend.  
	> In one approach, we use const only for values that must not change. In the other, we use const for any value that does not happen to change.
	> Flanagan prefers Approach 1, they physical constants approach.
* p. 125 - Explanation of scope wrt variables, similar to SVP Chapter 6 (p. 131 - 134) on scope. 
* p. 126 - Do *not* declare the same variable in a scope more than once using the `let` or `const` keywords. Syntax error. And also don't do it in a nested scope even though the JS interpreter will allow it--bad practice.

#### Flanagan 4.4: Property Access Expressions p. 140
* Note that there are two ways to access the properties of arrays, maps, and other objects:
	* Bracket syntax, e.g., array[0]; --> more on this in Flanagan, Chapter 7.
	* 'Dot Syntax', e.g., `let object = {name: "jeff");`. The expression `object.name` outputs `jeff`. For more, see Chapter 6 on Objects.

#### Flanagan 4.5: Expressions to invoke functions or methods
* p. 144 - 145
* examples of functions with arguments / input parameters
	* f("hello");
	* Math.max( x, y, z );
* foobar.sort() -- a function with no arguments passed in.
* For more, see Chapter 8 Functions and Chapter 9 Classes.
* p. 147-148 -- Flanagaan 4.6: Creating Objects with the *constructor function* `new`. Eg., `new Point(2,3);`.
* p. 149 -151 -- Table 4.1 Javascript operators.
	* Unary operator `typeof` returns what type the input operand is.

### Chapter 5: Statements p. 197
* Up to Flanagan p. 210, Section 5.4 on loops. 

#### Flanagan 5.4.4 for/of loops p. 215
* Introduced in ES6 in 2015 works for *iterable* objects like arrays. See Flanagan Chapter 12 for more.
* p. 216-217 `for/of` in the context of objects
    * Objects by default are *not* iterable. If you try to use the `for/of` consturect with objects out of the box, you will receive a TypeError at runtime.
* See p. 218-219 for info on using `for/of` with strings, Sets, and Maps.
* Finally, see p. 219-220 and Chapters 12-13 for the asynchronous `for/of` loops, aka the `for/await` construct used in node.js etc.
    * However, you can use the `for/of` loop construct *or* you can combine `for/of` with the `Object.keys()` method.
* Mostly can ignore `for/in` loops now. Only shows up in legacy code because the `for/of` construct is more modern and mostly does everything we need to better, esp. in combination with the `Object.keys()` and `Object.entries()` methods.


## 7/01/2024
* *JS Definitive Guide* **Section 5.5 Jumps** (Flanagan p. 222)
* Mostly completed Flanagan Chapter 5. Onto other chapters in Flanagan.
* SVP p. 96 - nested loops. Handy method to show an array in "table" format. Instead of `console.log(jhArray);`, try `console.table(jhArray);`
* Next is SVP p. 104 "looping over objects by coverting the object into an array". Use the Object.keys() built-in function.

## 7/02/2024
* Completed all loops in SVP Chapter 5. Need to go back and review `break` and `continue` in the context of nested loops and labelled blocks.
* Began SVP Chapter 7 on Classes p. 149. Note also that Flanagan covers Classes in Chapter 9 p. 403.


### Flanagan Chapter 6: Objects p. 251
* All JS objects display prototypical inheritance with the exception of the base JS `Object`.
* JS objects are dynamic, aka, properties can usually be added, deleted, and updated.
	* However, JS objects can also be used to simulate static objects, aka the *structs* of statically typed languages.
	* Furthermore, objects can represent sets of strings (by ignoring the "value" part of *key-value* pairs.)
* Any value in JS that is not a primitive value is an object. However, strings, numbers, and booleans have methods that make them seem to act like objects.
* p. 252. JS uses the `own property` to refer to non-inherited properties.

#### Flanagan 6.2 p. 252
* p. 255, **Section 6.2.3: Prototypes**.
	* Almost every JS object has a second JS object associated with it-- the *prototype*. The first object inherits its properties from its associated prototype.
	* All objects created by object literals (aka method 1 below) share the same prototype: the `Object.prototype`. 
	* In contrast, objects created by the `new` keyword and constructor() invocation (aka method 2 below) use the value of the `prototype` property of the constructor function as their prototype.
		* So for example, the object created by `let obj = new Object();` inherits from the `Object.prototype`, just like `let obj2 = {};` does.
	* **Key point:** Almost all objects have a *prototype*, but only a very small number of objects have a unique/special `prototype property`. It is the rare objects with a `prototype property` that go on to define prototypes for all other objects.
	* `Object.prototype` is one of the rare objects that has no prototype; it does *not* inherit properties from anyone.
	* Most constructor() functions have a prototype that inherits from the `Object.prototype`. e.g., the `Date.prototype` inherits properties from `Object.prototype`. So a Date object created like so: `let jh-date = new Date();` inherits properties from *both* `Date.prototype` *and* `Object.prototype`. 
		* This linked series of prototype objects is known as a **prototype chain**.
* p. 252 of creating objects: (1) using object literals; (2) with the `new` keyword; (3) with the `Object.create()` function.
	1. **6.2.1 Object literals**, e.g., `let point = { x:0, y:0};`
	1. **6.2.2 Creating with `new` keyword**. This uses the *constructor function* of JS objects. The way it works is you declare a new object, use the `=` sign for invokation, use the `new` keyword, and then invoke the constructor function. Examples:
		* `let jh-obj = new Object()`;
		* `let arr = new Array();`
		* `let jh-date = new Date();` // Create a Date object representing the current time.
	1. **6.2.3 Using Object.create()**. e.g., `let obj1 = Object.create( {x:1, y:2} );` means that `obj1` inhreits properties x and y. thus. `obj1.x + obj1.y` evaluates to `3`.

#### More on Object.create() section 6.2.3
* You can pass null as an argument into `Object.create()` like so, but this means that the newly created object will *not* inherit anything. Not even basic methods like `toString()` and ability to work with operators like `+`.
	* `let obj2 = Object.create(null);`
* If you want to create an 'ordinary' empty object, the one created by `let o1 = {};` or by `let o2 = new Object();`, you need to pass in `Object.prototype` as an argument into the create() method like so:
	`let obj3 = Object.create( Object.prototype );`
* The ability to create a new object with an arbitrary prototype is very powerful; we'll show more about this later in Chapter 6.
* One use for `Object.create()` is when one want to guard against unintended modification of an object by a library function that one doesn't have control over. Instead of passing the object directly into that library function, you can pass an object that inherits from it. If the function reads properties of the passed-in object, the function will see the *inherited* values. However, if the function tries to set the properties, those writes will not affect the properties of the original object.

	```
	let o = { x: "don't change this property value" };
	library.function(Object.create(o)); // Guard against accidental modification
	```

#### Flanagan 6.3: Querying and Setting properties
* p. 257 To obtain the value of a property, use the `.` dot or square bracket `[]` operators from Section 4.4. The lefthand side of the equation should be san expression whose value is an object. 
* If using the `.` operator, the righthand side must be a simple identifier that names the property.
* If using `[]`, the value within the brackets must be an expression that evaluates to a string that contains the desired property name.


## 7/03/2024
* Flanagan p. 258 **Section 6.3.1: Objects as Hash Maps *aka* Associative Arrays**
* These two expressions evaluate to the same value:
	* `object.property` -- looks like syntax used in C and Java to access the static property of a C struct or Java object.
	* `object["property"]` -- looks like you are accessing a cell in an array, but instead of using the index number to find the cell, you are matching on a string called "property".
* In other words, JS objects are actually hash-maps (aka *dict* in Python, aka *map* in JS). Key-value pairs.
* In strongly typed languages like C, C++, and Java, an object can only have a fixed number of properties; plus the names of these object properties must be specified in advance.
* In contrast, JS can create any number of properties dynamically.
* Furthermore, when you use the `.` syntax to access an object's properties, that property can only be accessed (and uniquely identified) by it's **name**. 
	* aka, *Identifies must be entered directly into a JS program; since properties are not a datatype, they cannot be manipulated by the JS engine.* p. 259
* On ther other hand, when one access the property of an object using the `[]` notation, the name of the property is expressed as a string.
* Strings *are* JS datatypes; so as strings, they can be manipulated and created while the program is running.
* Example, p. 259-260:

	```
	let addr = "";
	
	for (let i = 0; i < 4; i++)  {
		addr += customer[`address${i}`] + "\n";
	}
	````] + "\n";
	}
	```
* The code above reads and concatenates the `address0`, `address1`, `address2`, and `address3` properties of the `customer` object.
* The example above demonstrates the flexibility of using the array notation to access properties of an object with string expressions.
* The code *could* be rewritten using the `.` notation, but there are cases where only a `[]` array notation will do.
	* Example of tracking a stock portfolio dynamically p. 260 - 261.
* Historically, JS objects have been used as maps *aka* associative arrays. **However, since the introduction of formal `Map` data structures in ES6, the map is usually a better choice than a plain object.**
	* See section 11.1.2 for more on maps.

#### Flanagan 6.3.2 Inheritance p. 261
* JS objects have a set of 'own properties' as well as another set of properties they've inherited from their prototype object.
* p. 262 Example. Assume you have an object `obj` with a property `x`. Let's say you try to access property `x` by using either `obj.x` or `obj["x"]` syntax.
	* If the prototype of `obj` does not possess an own property by the name of `x`, *but* has a prototype itslef, the query is performed on the prototype of the prototype.
	* This process along the prototype chain continues until a property `x` can be found. *Or* until an object with a `null` prototype is found.
	* Next, suppose you assign the property `x` to object `obj`. If `obj` already has an *own* (aka non-inherited) property named `x`, then the assignment simply changes the value of this existing `x` property.
	* Otherwise, the assignment creates a *new property* named `x` on the object `obj`.
	* If `obj` previously inherited the property `x`, that inherited property is now hidden by the newly created own property of the same name.
* p. 263 Property assignment examines the prototype chain only to determine whether the assignment is allowed.
	* However, if `obj` inherits a *read-only* property named `x`, then the assignment is **not** allowed.
* **Key point** If the assignment of this property *is* allowed, it always creates the property for the original `obj` object; **not** for the prototype or indeed any other prototypes in the prototype chain.
	* This fact is a key feature of JS which means that we can selectively override the properties of various child objects with precision.
* p. 263-264 exception to general trule that a property assignment either works on `obj` *or* fails re: setter methods.

#### Flanagan 6.3.3 Property Access Errors p. 264
* When trying to access a property, expressions do not always succeed in setting a value or returning a value.
* If an object exists but the queried property does *not*, JS will simply evaluate your request to `undefined`. However, if the sought after object does not exist at all, we will receive a `TypeError`. p. 264
* Deleting properties (Flanagan 6.4 p. 266-268)

#### Section 6.5 Testing Properties p. 268
* Ways of checking if an object has various properties, and enumerating them systematically: (1) using the `in` operator; (2) the `hasOwnProperty()` method; (3) the `propertyIsEnumerable()` method; and (4) basic querying properties directly via `.` and `[]`.
* **`in`** operator. Returns `true` if the object has an *own* property or an *inherited* property by that name. Ex.

	```
	let obj = { x:1 };
	"x" in obj;  // Evaluates to 'true' b/c obj.x is an own property
	"y" in obj; // Evaluates to 'false' b/c obj does not have an 'y' property
	"toString" in obj; // Evaluates to 'true' b/c obj inherits the toString property from Object
	```

* Regarding the `hasOwnProperty()` method, this method tests whether the object has an own property with that name. If that property exists but is an *inherited* property, the method will return `false`.
* the `propertyIsEnumerable()` refines the `hasOwnProperty()` test. It returns `true` only if the property is an own property and the *enumerable* attribute is true.
* don't always need to use the `in` operator. Instead, you can do an equality test like so:

	```
	let obj = { x:1 };
	obj.x !== undefined // Evals to true b/c obj.x property exists
	obj.y !== undefined // Evals to *false* b/c obj.x does *not* exist
	obj.toString !== undefined // Evals to *true* b/c obj inherited that property.
	```

#### Section 6.6 Enumerating Properties p. 270
* Instead of querying properties one and a time, we can do it systematically.
* p. 270-271 `for/in` for enumeration. As discussed in 6/29/2024 above, can mostly ignore `for/in` nowadays. In almost all cases, just use the more modern `for/of` construct.

#### Four functions related to for/of loops p. 271 - 272
1. `Object.keys()` returns an array with the names of the enumerable own properties of the object. It does *not* included inherited properties, non-enumerable properties, and others.
1. `Object.getOwnPropertyNames()` works similarly to `Object.keys()` but also includes *non-enumerable* own properties as long as the keys are strings.
1. `Object.getOwnPropertySymbols()`
1. `Reflect.ownKeys()` returns pretty much all property names: enumerable and non-enumerable, both string and Symbol. See also section 14.6.
* See also Section 6.6.1 on Property Enumeration Order p. 272-273.

#### Flanagan 6.7 Extending Objects p.273
* Often, we want to copy the properties from one object to another object. Sample code:

	```
	let target = { x:1 }, source = { y:2, z:3 };
	for (let key of Object.keys(source)) {
		target[key] = source[key];
	}

	console.table(target) 
	```
* However, since this is a common operation, many JS frameworks have definied utility functions, often called `extend()` to perform the above copying operation.
* Furthermore, ES6 adds `Object.assign()` which provides this capability into the core JS language.
	* `Object.assign()` expects two or more objects as its input arguments.
	* It modifies and returns the first argument (the target object), but does not alter the second or any subsequent arguments (which are all source objects).
	* for more, see p. 273 - 274.
* Per Section 6.10.4, we can see how to use the `...` spread operator to copy-and-override objedcts.

#### Flanagan 6.8 Serializing Objects p.276
* Object *serialization* is the process of converting an object's state to a string from which it can later be restored.
* `JSON.stringify()` serializes JS objects into a string.
* `JSON.parse()` does the reverse operation; it turns a string back into a JS object.
* Note that JSON syntax is a *subset* of broader JS syntax; it cannot represent *all* JS values.
* things that are supported by `JSON.stringify()` and `JSON.parse()`: JS objects, arrays, strings, finite numbers, and the following primitive types: `true`, `false`, and `null`.

#### Flanagan 6.9 Object Methods p. 277
* Again, all JS objects (except those explicitly created without a prototype) inherit properties from `Object.prototype`. 
* These inherited properties are primarily methods. B/c they are universally available, they are of particular interest to JS programmers.
* See Chapter 9 for defining methods generally for an entire class of objects.

#### 6.9.1 toString()
* The `toString()` methods takes no arguments; it returns a string that somehow represens the value of the object on which it was invoked.
* JS invokes this method whenever it needs to convert the object to a string.
* This occurs when you use the `+` operator to concat a string with an object or when you pass an object to a method that expects a string.
* the default `toString()` method is not very informative, often outputting something like `[object Object]`.
* As a result, many classes define their own versions of `toString()`. e.g., when an array is converted to a string, one obtains a list of the array elements, each element of which has been converted into a string.
* As another example, when you convert a function to a string, you obtain the source code of the function.
* Example of defining a custom `jhToString()` method:

	```
	let point = {
		x: 1,
		y: 2, 
		toString: function() {
			return `(${this.x}, ${this.y})`;
		}
	};

	String(point) // outputs "(1, 2)": toString() is used for string conversions
	```

#### 6.9.2 toLocaleString() Method p. 278
* In addition to the basic `toString()` method, all JS objects have a `toLocaleString()` method.
* This method returns a localized string representation of the object.
* See p. 279 for an example of converting between different kinds of thousands separators.

#### 6.9.3 valueOf() Method p. 279
* The `valueOf()` method is called when JS needs to convert an object to a dprimitive type *other* than String.
* The base `valueOf()` method is pretty vanilla, but classes that inherit and modify it are more interesting. For example, let's look at Date objects. `Date.valueOf()` converts dates into numbers; this allows Date objects to be chronologically compared using the `<` and `>` operators.
* Let's show how we might write a custom `valueOf()` method for our usual `point` object.

	```
	let point = {
		x: 3,
		y: 4, 
		valueOf: function() {
			return Math.hypot(this.x, this.y);
		}
	};

	Number(point); // => 5: valueOf() is used for conversions to numbers

	point > 4; // Evaluates to true
	point > 5; // Evaluates to false
	point < 6; // Evaluates to true
	```

#### 6.9.4 toJSON() Method p. 280
* The `Object.prototype` does not actually define a `toJSON()` method. However, the `JSON.stringify()` method does look for a `toJSON()` method on any object it's asked to serialize.
* If this method exists on the object to be serialized, it is invoked.
* In which case the return value is serialized instead of the original obje ct.
* For example, the Date class defines a `toJSON()` method that returns a serializable string representation of the date.
* Let's see what it would be like to define a `toJSON()` method for our usual Point object:

	```
	let point = {
		x: 1,
		y: 2, 
		toString: function() {
			return `(${this.x}, ${this.y})`;
		},
		toJSON: function() {
			return this.toString();
		}
	};

	JSON.toStringify([point]); // => '["(1, 2)"]'
	```

#### Flanagan 6.10 extended Object Literal Syntax
* p. 281 Recent versions of JS have extended the syntax for object literals in a few useful ways.

#### 6.10.1 Shorthand properties p. 281
* Suppose you have values stored in variables `x` and `y`.
* Next, you want to create an object with properties named `x` and `y` that hold the values from those earlier variables before you defined the object.
* This is what it would like in earlier vanilla JS:

    ```
	let x = 1, y = 2, z = 3;
	let obj = {
		x: x,
		y: y,
		z: z,
	};
	```

* Same thing but with more concise syntax, from ES6 onwards:

	```
	let x = 1, y = 2, z = 3;
	let obj = { x, y, z };
	```

#### 6.10.2 Computed Property Names p. 281
* Sometimes, one needs to create an object with a specific property. But it the name of that property is not a constant at compile-time; thus it cannot be typed into the source code.
* This means one needs to dynamically generate property names.
* i.e., the property name is stored in a variable or is the return value of a function that we invoke.
* You can't use the standard, simple, basic JS object literal for this type of property.
* Instead, we can create an object and then use the desired properties as an extra step.
* This is how one programmed before ES6:

	```
	const PROPERTY_NAME = "p1";
	function computePropertyName() {
		return "p" + 2;
	}

	let obj = {};
	obj[PROPERTY_NAME] = 1;
	obj[computePropertyName()]: 2;
	```
* In contrast, here is the more concise syntax after ES6:

	```
	const PROPERTY_NAME = "p1";
	function computePropertyName() {

	let obj2 = {
		[PROPERTY_NAME]: 1,
		[computePropertyName()]: 2
	};

	obj2.p1 + obj2.p2   // => 3
	```
* With the new ES6 syntax, the `[]` brackets delimit an arbitrary JS expression. That expression is evaluated, and the resulting value (converted to a string, if necessary) is used as the property name.
* One case where one might want to use computed properties is when one has a library of JS code that expects to be passed objects with a particular set of properties.
* And furthermore, the names of those properties are defined as constants in that library.
* If one is writing code to create the objects that will be passed to that library, one *could* **hardcode** the property names. However, that would risk bugs if one types the property names wrong as well as version mismatch if a new version of the library changes the required property names.
* The new ES6 syntax makes one's code more robust.

#### 6.10.3 Symbols as Property Names p. 283
* As explained in Flanagan Section 3.6, Symbols are opaque values that can only be used as property names.
* Since every Symbol is distinct from every other Symbol, it is a great type to use when making unique property names.
* Call the `Symbol()` factory function. For more, see why this helps code reliability with 3rd party libraries but is *not* necessarily a security measure on p. 284.


#### 6.10.4 Spread Operator ... p. 284
* In ES2018 and later, we can use the `...` spread operator.

	```
	let position = { x:0, y:0 };
	let dimensions = { width:100, height:75 };
	let rect = { ...position, ...dimensions };
	rect.x + rect.y + rect.width + rect.height // ==> 75
	```

* In the above code, the properties of the `position` and `dimensions` objects are *spread out* into the `rect` object literal as if they had been laboriously written literally inside the curly braces.
* What happens when the **target object** and the **source object that is being spread into the target** both have properties that have the same name? See p. 285 for the answer.
* Also, note that **the spread operator *only* spreads an object's *own* properties; but does *not* spread any inherited properties**.
* Note the big-O reasons why `...` can be inefficient in loops or recursive functions (p. 285-6).

#### 6.10.5 Shorthand Methods p. 286
* When a function is defined as a property of an object, we all that function a *method*.
* Prior to ES6, one would define a method in an object literal using a function definition expression just like one would define any other property of an object.
* However, as of ES6, the object literal syntax (and class definition syntax as shown in Chapter 9) has been extended to allow a shortcut.
	* In ES6 and later, the `function` keyword and colon `:` are omitted.
* Pre-ES6 code:
	```
	let square = {
		area: function() {
			return this.side * this.side;
		},
		side: 10
	};

	square.area() // => outputs '100'
	```
* ES6 and later. Note the omission of `function` keyword and colon `:`... 
	```
	let square = {
		area() {
			return this.side * this.side;
		},
		side: 10
	};

	square.area() // => outputs '100'
	```
* Both versions of the code are equivalent.

#### 6.10.6 Property Getters and Setters p. 287
* All the object properties discussed so far are called **data properties**.
* JS also supports **accessor properties** which are associated with `getter()` and `setter()` methods.
* More....

#### 6.11 Summary p. 291
