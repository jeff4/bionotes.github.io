---
title: Javascript
permalink: /javascript/
---

## 2022 Log

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

# 2024 Log

### 6/19/2024
#### setting up authentication
* See dialog in ChatGPT with suggested Astro code.
* From [this DevTo post](https://dev.to/itsabdessalam/password-protect-your-site-with-netlify-and-github-actions-1aah), I found these options for securing a site via Netlify--possibly with minimal or zero code changes to GitHub itself. [Main Netlify article](https://docs.netlify.com/security/secure-access-to-sites/)
	1. [Authenticate with Netlify Identity](https://docs.netlify.com/security/secure-access-to-sites/identity/)
	1. [Basic authentication with custom headers](https://docs.netlify.com/security/secure-access-to-sites/basic-authentication-with-custom-http-headers/) 
	1. [Use OAuth provider tokens on site](https://docs.netlify.com/security/secure-access-to-sites/oauth-provider-tokens/) 
	1. [Basic password protection vs. team login protection](https://docs.netlify.com/security/secure-access-to-sites/site-protection/#basic-password-protection-versus-team-login-protection) 
	1. [Protect your site with a single shared password](https://docs.netlify.com/security/secure-access-to-sites/site-protection/#protect-your-site-with-a-basic-password) 
* Also, this is an interesting [Oct 2023 post](https://github.com/lucia-auth/lucia/discussions/1231) by the creator of the Lucia auth library. Found at 1:33 of this [YouTube video](https://www.youtube.com/watch?v=S37uRvBr65k)

### 6/20/2024
* Created dev.to account and found this April, 2024 [article](https://dev.to/snikidev/astrojs-as-an-alternative-to-nextjs-pushing-the-limits-30ga) by Nikita Kakuev on how the Astro approach (if not necessarily the Astro framework) is the future. "The future is simple, vanilla JS because simplicity always wins."
* Found this 2022 piece by Stas Klymenko with a [Node.js Roadmap for Beginners](https://dev.to/hellnar/nodejs-roadmap-for-beginners-25ml). Starts with theory/fundamentals before building CRUD / MERN servers. Also covers authentication of JWT vs. Sessions.
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
* Out of curiosity, began looking at Maps, Chapter 11, p. 485

### 6/23/2024
* Got Flanagan's histogram program working (Example 1-1, p. 56). See proj-2.
* Completed miles --> km program in SVP p. 43 (end of Chap 2).
* Next step: continue with SVP chapter 3.
* Up to p. 53 in SVP chapter 3; about to begin using Array methods.
    * Note also there are good reasons why a javascript does not have a simple equivalent to this Objective C method `NSStringFromSelector`. Need to do something like `let arrayName = Object.keys({arr})[0]`. and then reference `arrayName` later in console.log(), per [this answer](https://stackoverflow.com/a/52598270). For byVal and byRef discussion see [this answer](https://stackoverflow.com/a/51005683)

```javascript
let arr = [1, 2, 3];
let arrayName = Object.keys({arr})[0];
console.log(arrayName);
```

### 6/24/2024
* splice() on SVP p.54. First argument indicates which index location the splice will begin. Second argument indicates how many existing entries (starting at the point of splicing--will be deleted). Note that if you accidentally delete more entries than exist in the original array, splice() will *not* throw an error; it will just delete all the elements available to the end of the array (going to the right edge).
* Completed practice exercise 3.2, shopping list, SVP p. 59.
* completed multi-dimensional arrays, see `7array-multidimensional.js`
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
* finished Chapter 4. Got stuck a little bit in standard input / standard output and ability to define scope of variables. And => arrow functions. Will be able to resolve this after I finish Chapter 6.
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

***

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
* p. 147-148 -- Flanagan 4.6: Creating Objects with the *constructor function* `new`. Eg., `new Point(2,3);`.
* p. 149 -151 -- Table 4.1 Javascript operators.
	* Unary operator `typeof` returns what type the input operand is.

***

### Chapter 5: Statements p. 197
* Up to Flanagan p. 210, Section 5.4 on loops. 

#### Flanagan 5.4.4 for/of loops p. 215
* Introduced in ES6 in 2015 works for *iterable* objects like arrays. See Flanagan Chapter 12 for more.
* p. 216-217 `for/of` in the context of objects
    * Objects by default are *not* iterable. If you try to use the `for/of` construct with objects out of the box, you will receive a TypeError at runtime.
* See p. 218-219 for info on using `for/of` with strings, Sets, and Maps.
* Finally, see p. 219-220 and Chapters 12-13 for the asynchronous `for/of` loops, aka the `for/await` construct used in node.js etc.
    * However, you can use the `for/of` loop construct *or* you can combine `for/of` with the `Object.keys()` method.
* Mostly can ignore `for/in` loops now. Only shows up in legacy code because the `for/of` construct is more modern and mostly does everything we need to better, esp. in combination with the `Object.keys()` and `Object.entries()` methods.


## 7/01/2024
* *JS Definitive Guide* **Section 5.5 Jumps** (Flanagan p. 222)
* Mostly completed Flanagan Chapter 5. Onto other chapters in Flanagan.
* SVP p. 96 - nested loops. Handy method to show an array in "table" format. Instead of `console.log(jhArray);`, try `console.table(jhArray);`
* Next is SVP p. 104 "looping over objects by converting the object into an array". Use the Object.keys() built-in function.

## 7/02/2024
* Completed all loops in SVP Chapter 5. Need to go back and review `break` and `continue` in the context of nested loops and labelled blocks.
* Began SVP Chapter 7 on Classes p. 149. Note also that Flanagan covers Classes in Chapter 9 p. 403.

***

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
	1. **6.2.2 Creating with `new` keyword**. This uses the *constructor function* of JS objects. The way it works is you declare a new object, use the `=` sign for invocation, use the `new` keyword, and then invoke the constructor function. Examples:
		* `let jh-obj = new Object()`;
		* `let arr = new Array();`
		* `let jh-date = new Date();` // Create a Date object representing the current time.
	1. **6.2.3 Using Object.create()**. e.g., `let obj1 = Object.create( {x:1, y:2} );` means that `obj1` inherits properties x and y. thus. `obj1.x + obj1.y` evaluates to `3`.

#### More on Object.create() section 6.2.3
* You can pass null as an argument into `Object.create()` like so, but this means that the newly created object will *not* inherit anything. Not even basic methods like `toString()` and ability to work with operators like `+`.
	* `let obj2 = Object.create(null);`
* If you want to create an 'ordinary' empty object, the one created by `let o1 = {};` or by `let o2 = new Object();`, you need to pass in `Object.prototype` as an argument into the create() method like so:
	`let obj3 = Object.create( Object.prototype );`
* The ability to create a new object with an arbitrary prototype is very powerful; we'll show more about this later in Chapter 6.
* One use for `Object.create()` is when one want to guard against unintended modification of an object by a library function that one doesn't have control over. Instead of passing the object directly into that library function, you can pass an object that inherits from it. If the function reads properties of the passed-in object, the function will see the *inherited* values. However, if the function tries to set the properties, those writes will not affect the properties of the original object.

	```javascript
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
* On the other hand, when one access the property of an object using the `[]` notation, the name of the property is expressed as a string.
* Strings *are* JS datatypes; so as strings, they can be manipulated and created while the program is running.
* Example, p. 259-260:

	```javascript
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
	* If the prototype of `obj` does not possess an own property by the name of `x`, *but* has a prototype itself, the query is performed on the prototype of the prototype.
	* This process along the prototype chain continues until a property `x` can be found. *Or* until an object with a `null` prototype is found.
	* Next, suppose you assign the property `x` to object `obj`. If `obj` already has an *own* (aka non-inherited) property named `x`, then the assignment simply changes the value of this existing `x` property.
	* Otherwise, the assignment creates a *new property* named `x` on the object `obj`.
	* If `obj` previously inherited the property `x`, that inherited property is now hidden by the newly created own property of the same name.
* p. 263 Property assignment examines the prototype chain only to determine whether the assignment is allowed.
	* However, if `obj` inherits a *read-only* property named `x`, then the assignment is **not** allowed.
* **Key point** If the assignment of this property *is* allowed, it always creates the property for the original `obj` object; **not** for the prototype or indeed any other prototypes in the prototype chain.
	* This fact is a key feature of JS which means that we can selectively override the properties of various child objects with precision.
* p. 263-264 exception to general rule that a property assignment either works on `obj` *or* fails re: setter methods.

#### Flanagan 6.3.3 Property Access Errors p. 264
* When trying to access a property, expressions do not always succeed in setting a value or returning a value.
* If an object exists but the queried property does *not*, JS will simply evaluate your request to `undefined`. However, if the sought after object does not exist at all, we will receive a `TypeError`. p. 264
* Deleting properties (Flanagan 6.4 p. 266-268)

#### Section 6.5 Testing Properties p. 268
* Ways of checking if an object has various properties, and enumerating them systematically: (1) using the `in` operator; (2) the `hasOwnProperty()` method; (3) the `propertyIsEnumerable()` method; and (4) basic querying properties directly via `.` and `[]`.
* **`in`** operator. Returns `true` if the object has an *own* property or an *inherited* property by that name. Ex.

	```javascript
	let obj = { x:1 };
	"x" in obj;  // Evaluates to 'true' b/c obj.x is an own property
	"y" in obj; // Evaluates to 'false' b/c obj does not have an 'y' property
	"toString" in obj; // Evaluates to 'true' b/c obj inherits the toString property from Object
	```

* Regarding the `hasOwnProperty()` method, this method tests whether the object has an own property with that name. If that property exists but is an *inherited* property, the method will return `false`.
* the `propertyIsEnumerable()` refines the `hasOwnProperty()` test. It returns `true` only if the property is an own property and the *enumerable* attribute is true.
* don't always need to use the `in` operator. Instead, you can do an equality test like so:

	```javascript
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

	```javascript
	let target = { x:1 }, source = { y:2, z:3 };
	for (let key of Object.keys(source)) {
		target[key] = source[key];
	}

	console.table(target) 
	```
* However, since this is a common operation, many JS frameworks have defined utility functions, often called `extend()` to perform the above copying operation.
* Furthermore, ES6 adds `Object.assign()` which provides this capability into the core JS language.
	* `Object.assign()` expects two or more objects as its input arguments.
	* It modifies and returns the first argument (the target object), but does not alter the second or any subsequent arguments (which are all source objects).
	* for more, see p. 273 - 274.
* Per Section 6.10.4, we can see how to use the `...` spread operator to copy-and-override objects.

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
* The `toString()` methods takes no arguments; it returns a string that somehow represents the value of the object on which it was invoked.
* JS invokes this method whenever it needs to convert the object to a string.
* This occurs when you use the `+` operator to concat a string with an object or when you pass an object to a method that expects a string.
* the default `toString()` method is not very informative, often outputting something like `[object Object]`.
* As a result, many classes define their own versions of `toString()`. e.g., when an array is converted to a string, one obtains a list of the array elements, each element of which has been converted into a string.
* As another example, when you convert a function to a string, you obtain the source code of the function.
* Example of defining a custom `jhToString()` method:

	```javascript
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
* The `valueOf()` method is called when JS needs to convert an object to a primitive type *other* than String.
* The base `valueOf()` method is pretty vanilla, but classes that inherit and modify it are more interesting. For example, let's look at Date objects. `Date.valueOf()` converts dates into numbers; this allows Date objects to be chronologically compared using the `<` and `>` operators.
* Let's show how we might write a custom `valueOf()` method for our usual `point` object.

	```javascript
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
* In which case the return value is serialized instead of the original object.
* For example, the Date class defines a `toJSON()` method that returns a serializable string representation of the date.
* Let's see what it would be like to define a `toJSON()` method for our usual Point object:

	```javascript
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

    ```javascript
	let x = 1, y = 2, z = 3;
	let obj = {
		x: x,
		y: y,
		z: z,
	};
	```

* Same thing but with more concise syntax, from ES6 onwards:

	```javascript
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

	```javascript
	const PROPERTY_NAME = "p1";
	function computePropertyName() {
		return "p" + 2;
	}

	let obj = {};
	obj[PROPERTY_NAME] = 1;
	obj[computePropertyName()]: 2;
	```
* In contrast, here is the more concise syntax after ES6:

	```javascript
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

	```javascript
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
	```javascript
	let square = {
		area: function() {
			return this.side * this.side;
		},
		side: 10
	};

	square.area() // => outputs '100'
	```
* ES6 and later. Note the omission of `function` keyword and colon `:`... 
	```javascript
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
* When a program *queries the value of an accessor property*, JS invokes the **getter method** (passing no arguments).
	* The return value of this method becomes the value of the property access expression.
* When a program *sets the value* of an accessor property, JS invokes the **setter method**, passing the value of the righthand side of the assignment.
	* This method is responsible for 'setting', in some sense, the property value.
	* The return value of the setter method is ignored.
* If a property has both a getter() *and* a setter() method, the property is a read/write property.
	* If a property only has a getter() method, it is a read-only property.
	* If a property only has a setter() method, it is a write-only property. This is *not* possible with data properties. Furthermore, attempts to read this write-only property, the return always evaluates to `undefined`.
* p. 288 Accessor properties can be defined with an extension to the *object literal* syntax. e.g., 

	```javascript
	let obj = {

		//An ordinary data property
		dataProp: someValue,

		// An accessor property defined as a pair of functions
		get accessorProp() { return this.dataProp; },
		set accessorProp(value) { return this.dataProp = value; }
	}
	```
* Accessor properties are defined as one or two methods whose name is the same as the property name.
* They 'look' like the **ES6 function shorthand**, with the exception that these getter/setter definitions are prefixed with the `get` and `set` keywords respectively.
* p. 289 Consider this slightly more interesting example with a 2d Cartesian point:

	```javascript
	let point = {

		// x and y are regular read/write data properties
		x: 1.0,
		y: 1.0,

		// r is a read/write accessor property with a getter() and a setter()

		get r() { return Math.hypot( this.x, this.y ); },

		set r(newvalue) {
			let oldValue = Math.hypot ( this.x, this.y );
			let ratio = newValue / oldValue;
			this.x *= ratio;
			this.y *= ratio;
		},

		// angleTheta is a read-only accessor property with a getter() only
		get angleTheta() { 
			return Math.atan2( this.y,  this.x ); 
		}
	};


	point.r     // => Math.SQRT2
	point.angleTheta // =>  Math.PI / 4

	```

##### Getter() / Setter() inheritance p. 290
* Accessor properties are inherited, just as data properties are.
* Therefore, one can use the object `point` above as a prototype for other points.
* One can also give new objects their own, distinct, `x` and `y` properties. And these new objects will then inherit the r and angleTheta properties, e.g.:

	```javascript
	let q = Object.create(point); // A new object that inherits getter()/setter()
	q.x = 3; // Create a point q with it's own x/y properties
	q.y = 4; 
	q.r;     // => 5 aka the inherited accessor properties work
	q.angleTheta; // => Math.atan( 4, 3)
	```
* The code above uses accessor properties to define an API that provides two representations--Cartesian coordinates and polar coordinates from a single set of data.


#### 6.11 Summary p. 291
* Flanagan Chapter 6 on Objects is completed!


## 7/04/2024
### From MDN
* Via Vue.js [tutorial](https://vuejs.org/guide/introduction.html). Began poking around MDN and found [article](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) on Inheritance and the Prototype Chain.
* Other good MDN resources:
    * [JS language overview](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_overview)
    * [Data Types and Data Structures in JS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
    * [Concurrency and the Event Loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Event_loop)
* MDN [Overview and links to CSS resources](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps)

*** 

### Flanagan Chapter 9: Classes p. 403
* p. 404. Note again that JS inheritance is based on prototypes which is quite different than the classical OO inheritance seen in C++/Java.


#### Flanagan 9.1: Classes and Prototypes p. 404
* In JavaScript, a class is a set of objects that inherit properties from the same prototype object. The prototype object, therefore, is the central feature of a class. 

### Example 9-1 p. 404

```javascript	
//This is a factory function that returns a new 'RANGE object'
function range(from, to) {

	// Use Object.create() to create an object that inherits from the prototype object defined below
	// the prototype object is stored as a property of this function, and defines the shared
	// methods (behavior) of all following 'range' objects.

	let r = Object.create(range.methods);


	// Store the start and end points (state) of this new range object. These are non-inherited
	// properties
	r.from = from;
	r.to = to;

	// Finally, return the new object
	return r;
}

//The below prototype object defines methods inherited by all RANGE objects
range.methods = {

	// returns true if x is in the range,
	// returns false if x is not in the range
	// This method works for text and Date ranges as well as numeric

	includes(x) {
		return this.from <= x 
			&&
			x <= this.to
	},

	// A generator function that makes instances of the RANGE class iterable
	// note that this only works for numeric ranges

	*[Symbol.iterator]() {
		
		for ( let x = Math.ceil(this.from); x <= this.to; x++) {
			yield x;
		}

	},

	// Return a string representation of the range
	toString() { return "(" + this.from + "..." + this.to + ")"; }

};
```
* See below for examples of calling and using the `range` object.

	```javascript	
	let r = range(1,3);  // create a range object
	r.includes(2);   // => true b/c 2 is in the range
	r.toString();    // outputs "(1...3)"
	[...r]           // converts to an array via iterator: [1, 2, 3] 
	```
	
* A few things worth noting in above example:
	1. This code defines a *factory function* `range()` for creating new Range objects.
	1. It uses the `methods` property of this `range()` function as a convenient place to store the prototype object that defines the class. There is nothing special or idiomatic about putting the prototype object here.
	1. The `range()` function defines `from` and `to` properties on each Range object.
		* These are unshared, non-inherited properties that define the unique state of each individual Range object.	1. The `range.methods` object uses the ES6 shorthand syntax for defining methods, which is why you don't see the `function` keyword anywhere. (Recall shorthand for method declaration in an object per Section 6.10.5)
	1. One of the methods of the prototype has the computed name `Symbol.iterator`. This means that it is defining an iterator for Range objects.
		* The name of this method is prefixed with a `*`, which indicates that it is a *generator function* instead of a regular function.
		* Iterators and generators are covered in detail in Chapter 12.
		* For now, the upshot is that instances of this Range class can be used with the `for/of` loop and with the `...` spread operator.
	1. The shared, inherited methods defined in `range.methods` all use the `from` the `to` properties that were initialized in the `range()` factory function.
		* In order to refer to them, they use the `this` keyword to refer to the object through which they were invoked. 
		* The use of `this` is a fundamental characteristic of the methods of any class.

#### Section 9.2 Classes and Constructors
* The previous example is a simple way to define a JS class. But it is *not* the idiomatic way to do so, b/c it doesn't use a **constructor function**.
* A Constructor is a function that is designed for the initialization of newly created objects.
* Constructors are invoked using the `new` keyword as described in Section 8.2.3.
* Constructor invocations using `new` automatically create the new object, so the constructor itself only needs to initialize the state of that new object.
* The critical feature of constructor invocations is the the constructor's `prototype` property is used as the prototype for the new object (See Section 6.2.3.).
* Finally, we can clarify this: **it is function objects that have a `prototype` property.**
* This means that all objects created with the same constructor function inherit from the same object and are therefore members of the same class.
* See below example for how we can rewrite the declaration of a RANGE class with an idiomatic constructor function rather than a simpler factory function. Note that this next example is not the *most* modern way b/c it doesn't use the `class` keyword from ES6.
* So this is the sequence: (1) Example 9-1 uses factory function; (2) Example 9-2 uses a constructor function but *not* with the most modern ES6 `class` keyword; (3) Example 9-3 builds the Range class in the most modern `class` way (p. 416-417)
* So let's see what Example 9-2 looks like (p. 408-409)

## 7/05/2024
* Decided to run a local http server. Two options from this [Stack Overflow question](https://stackoverflow.com/q/32332485):
	1. Use [http-server](https://stackoverflow.com/a/32336922). Install in desired directory (or parent directory) by running `npm install -g http-server`. Run server with `http-server ./ -p 80`. Or whatever desired port.
	1. Specific for macOS, use [live server](https://stackoverflow.com/a/51009471), which has nice benefit of auto-reloading when files change. Install with `npm install -g live-server`. Run with `live-server --port=80` or whichever preferred port.
* Used Firefox Developer Tools `cmd-option-I` to test scripts. Works.

### Example 9-2 p. 408
```javascript
// This is a Constructor Function that initializes new Range Objects
// Note that it does not create or return the object. It just initializes it.

function Range(from, to) {

	// Store the start and end points (state) of this new Range object
	// These are non-inherited properties that are unique to this object

	this.from = from;
	this.to = to;
}
	

// All Range objects inherit from this object.
// Note that the property name must be a 'prototype' for this to work.

Range.prototype = {

	// returns true if x is in the Range,
	// returns false if x is not in the Range
	// This method works for text and Date Ranges as well as numeric

	includes: function(x) {
		return this.from <= x
		&&
			x <= this.to;
	},

	// A generator function that makes this class iterable.
	// Note that it only works for numeric Ranges.
	
	[Symbol.iterator]: function*() {
		for (let x = Math.ceil(this.from); x <= this.to; x++) 
			yield x;
	},

	// Return a string representation of the Range
	
	toString: function() {
		return "(" + this.from + "..." + this.to + ")";
	}
};

// Below statements construct a new Range instance named 'r'
// And use some of r's methods.
let r = new Range(1,19);
let bool = r.includes(2);   // => true b/c 2 is in the range
console.log(bool);

console.log(r.toString());    // outputs "(1...3)"
```
##### Notes on Example 9-2
* Capitalized from object `range` to Class `Range`.
* Now that we have a constructor function, must use the keyword `new` when creating a new Range instance. This bug caused me problems for a while.
* Another critical difference between Examples 9-1 and 9-2 is the way the prototype object is named. In Example 9-1, the prototype was `range.methods`. This was a convenient and descriptive name, but it was arbitrary.
	* In Example 9-2, the prototype is `Range.prototype` and this name is *mandatory*.
	* An invocation of the `Range()` constructor automatically uses `Range.prototype` as the prototype of the new Range objects.
* Note some things that did *not* change between Ex 9-1 and 9-2:
	1. The range methods are defined and invoked in the same way between both examples.
	1. B/c Ex 9-2 demonstrates the idiomatic way to create classes in versions of JS *before* ES6, it does *not* use the ES6 shorthand method syntax in the prototype object; it explicitly spells out the methods with the **`function`** keyword.
	1. Note also that neither Ex 9-1 and 9-2 use the arrow notation when defining constructors or methods. 
		* Recall from Section 8.1.3 that functions defined in this way do *not* have a `prototype` property and so cannot be used as constructors.
		* Also, arrow functions inherit the `this` keyword from the context in which they are defined rather than setting it based on the object through which they are invoked, and this makes them useless for methods.
		* B/c the defining characteristic of methods is that they use `this` to refer the instance on which they were invoked.
* Fortunately, the new ES6 class syntax doesn't allow the option of defining methods with arrow functions. So this is not a mistake you can actually make when using that syntax.

#### Section 9.2.1 Constructors, Class Identity, and instanceof p. 412
* As we've seen, the prototype object is fundamental to the identity of a class: two objects are instances of the same class if and only if they inherit from the same prototype object.
* The constructor function that initializes the sate of a new object is not fundamental.
	* Two constructor functions may have `prototype` properties that point to the same prototype object.
* Even though constructors are *not* as fundamental as prototypes, the constructor serves as **"the public face of the class"**.
* e.g., the `Range()` constructor creates Range objects.
* More fundamentally, however, constructors are used as the righthand operand of the `instanceof` operator when testing objects for membership in a class. 
* e.g., if we have an object `r` and want to know if it is a Range object, we can write:

	```javascript
	r instanceof Range // => true b/c 'r' inherits from the Range.prototype
	```

* The instanceof operator was described in Section 4.9.4. The lefthand operand should be the object being tested (`r`). The righthand operand would be the *constructor function that names the class*.
* The expression `o instanceof C` evaluates to `true` if `o` inherits from `C.prototype`.
	* The inheritance need not be direct: if `o` inherits from an object that inherits from an object that inherits from `C.prototype`, the expression will still evaluate to `true`.
* See p.413 to explain the usage of the `isPrototypeOf()` method.

#### 9.2.2 The constructor Property p. 413
* Even though we created an object in Example 9-2 to contain the methods for our Range class, this is not necessary.
* Any regular JS function can be used as a constructor. Constructor invocations need a `prototype` property.
* Therefore, every regular JS function automatically has a prototype` property.
* The value of this property is an object that has a single, non-enumerable `constructor` property.
* The value of the `constructor` property is the function object.

	```javascript
	let F = function() {}; // This is a function object
	let p = F.prototype; // This is the prototype object associated with F.
	let c = p.constructor; // This is the function associated with the prototype
	c === F;    // => true b/c F.prototype.constructor === F for any F
	```
* The existence of this predefined prototype object with its `constructor` property means that objects typically inherit a `constructor` property that refers to their constructor function.
* Since constructors serve as the public identity of a class, this constructor property gives the class of an object:
	```javascript
	let o = new F();   // Create an object o of class F
	o.constructor === F // => true b/c the constructor property specifies the class
	```
* See Fig 9-1 on p. 415 to see relationship between Constructor, Prototype, and Instances.
* Another common technique seen in older JS code is the using the predefined prototype object with its `constructor` property and adding methods to it one at a time with code like this:
	```javascript
	// older code
	// Extend the predefined Range.prototype object so we don't overwrite
	// the automatically created Range.prototype.constructor property

	Range.prototype.includes = function(x) {
		return this.from <= x && x <= this.to;
	};

	Range.prototype.toString = function() {
		return "(" + this.from + "..." + this.to + ")";
	};
    ```

#### Section 9.3 Classes with the class Keyword p. 416
* Classes have been part of JS since it was first released. But Classes finally get their own syntax in ES6.
* Just tested Example 9-3 and it works! See `./_df9/13-ex-9-3.js` for JS code. Called from `./t2.html`.
* Note that invocation of classes after they are defined in Examples 9-2 and 9-3 work *exactly the same way*. With a constructor function and a `new` keyword.
* The introduction in ES6 of the `class` keyword *does not alter the fundamental nature of JS' prototype-based classes*. 
* Although Ex 9-3 uses the `class` keyword, the resulting Range object is a constructor function, just like the version defined in Ex 9-2.
* The new `class` syntax is clean and convenient. 
* **But it Ex 9-3 is best thought of as *syntactic sugar* for the more fundamental class definition mechanism in Ex 9-2.** 

### Example 9-3 p. 416-417

```javascript
class Range {
	constructor(from, to) {

		// Store the start and end points (state) of this new Range object
		// These are non-inherited properties that are unique to this object
	
		this.from = from;
		this.to = to;
	}
	
	// returns true if x is in the Range,
	// returns false if x is not in the Range
	// This method works for text and Date Ranges as well as numeric

	includes(x) {
		return this.from <= x
		&&
			x <= this.to;
	}

	// A generator function that makes instances of this class iterable.
	// Note that it only works for numeric Ranges.
	
	*[Symbol.iterator]() {
		for (let x = Math.ceil(this.from); x <= this.to; x++) 
			yield x;
	}

	// Return a string representation of the Range
	
	toString() {
		return `(${this.from}...${this.to})`;
	}
}
```

#### More notes about the syntax shown in Ex 9-3 p. 417-418
1. The class declared with the `class` keyword, which is followed by the name of the class and a class body in curly braces.
1. The class body includes method definitions that use *object literal method shorthand*; this was also used in Ex 9-1--where the `function` keyword is omitted.
    * Unlike object literals, however, **no commas are used to separate each method**.
    * Although class bodies are superficially similar to object literals, they are *not* the same thing.
    * In particular, class bodies do not support the definition of properties with name/value pairs.
1. The keyword `constructor` is used to define the constructor function for the class.
    * The function defined is not actually *named* 'constructor', however!
    * The `class` declaration statement defines a new variable `Range` and assigns the value of this special constructor function to that variable.
1. If your class does not need to do any initialization, you can omit the `constructor` keyword and associated class body. In that case, an empty constructor function will be implicitly created by JS for you.
1. If one wants to define a class that subclasses (aka *inherits from*) another class, you can use the `extends` keyword with the `class` keyword.
    * In the below example, a `span` is like a range. But instead of initializing with a start and end, we initialize it with `start` and `length variables.

    ```javascript
    class Span extends Range {
        constructor(start, length) {
            if (length >=0) {
                super(start, start + length);
            } else {
                super(start + length, start);
            }
        }
    }
    ```
1. More on `extends` and `super` in section 9.5.

#### alternate versions of class declaration p. 419
* Just as a function declaration has statement and expression forms, so too with class declarations. e.g., 

```javascript
// function declaration -- statement
let square  = function(x) {
    return x * x; 
};

// function declaration -- expression
square(3)   // evaluates to 9


// class declaration -- statement
let Square = class {
    constructor(x) {
        this.area = x * x;
    }
};

// class declaration -- expression
new Square(3).area   // evals to 9
```
* As with function definition expressions, class definition expressions can include an optional class name. If you provide such a class name, that name is only defined within the class body itself.

## 7/07/2024
### JH thoughts on Ex 9-1, 9-2, 9-3
* Spent some time on Saturday 7/06 writing up notecards to break down how the factory function vs. constructor function syntax works in older and post-ES6 syntax, as well as associated prototype.method definition, and how to call/create instances of these objects.
* 9-1 and 9-2 are similar in that they require two different `{}` blocks: (1) One for their respective prototype definitions and (2) Another block for definition of their factory/constructor functions.
	* In contrast, 9-3's post-ES6 syntax is nice in that a single `{}` block handles class definition all in a single block that *combines* the `Constructor function` *and* the `Prototype method definitions` within one pair of curly braces.
* 9-2 and 9-3 and deeply similar despite surface differences in syntactic sugar. 

#### Prototype syntax comparison
* 9-2 uses `Range.prototype = { (1) includes:,  (2) [Symbol.iterator]:,  (3) toString:  };`.
* 9-3 uses *no* explicit keyword to indicate that prototype methods are being defined. It's **implicit** in ES6. And the first method occurring early in the same expression of the Constructor function is method 1. So these are methods 2-4 equivalent to (1) includes  (2) [Symbol]   (3) toStrong in 9-2.

	```javascript
	(2) includes(x) { return this.from<= && <=this.to; } // no comma at end of method!
	(3) *[Symbol.iterator]() { for(x=Math; x<=this; x++)  yield x;  } // no comma at end of method!
	(4) toString() {  return `(${this.from}...${this.to})`;   } // no comma at end of method!
	```

* Note again that only 9-2 uses the `function` keyword to explicitly indicate that methods are being defined for the prototype object *and* the constructor/factory functions. ie., *both* 9-1 and 9-3 simply declare `toString()`    instead of 9-2's `toString: function()`.
* 9-1 and 9-2 are similar in that there is a distinct `{}` expression holding the prototype definition; again 9-3 just includes the prototype methods in the `class {}` 
* 9-1 and 9-2 are also similar in that they use the *Object Name* when defining the prototype. Again, 9-3 doesn't need that b/c prototype definition is implicit within the `class Range {}` block:
	* 9-1 `range.methods = {};`
	* 9-2 `Range.prototype = {};`

#### Comparison of factory / constructor function
* 9-2 and 9-3 very similar. main difference is use of *function* vs. *class* keywords. Also, 9-3 ES6 syntax has explicit `constructor` keyword:
	* 9-2: `function Range(from, to) {}` plus no explicit *constructor* keyword.
	* 9-3: `class Range(from, to) { constructor(from, to)  }`
* 9-1 is most different from 9-2 and 9-3. 
	* 9-1 needs to use the `let r = Object.create(range.methods)` where **range.methods** is the prototype object.
	* It's also more complicated b/c 9-1 uses `r.from = from;` rather than 9-2 and 9-3's clearer syntax `this.from = from;`.

### Final notes on Section 9.3 p. 419-420
* A few more important things about the	**Class** syntax:
	1. All code within the body of the `class` declaration is implicitly in **strict mode**.
		* This is true even when the `use strict` directive is not explicitly used.
		* This means one can't use octal integer literals within Class bodies.
		* This means one can't use the `with` statement within Class bodies.
		* Syntax errors are more likely to be reported if one declares a variable before using it.
	1. **Class** declarations like in 9-3 are *not hoisted*, **unlike in function declarations such as in 9-1**. 
		* Recall from section 8.1.1 that function definitions behave as if they had been moved to the top of the enclosing file or enclosing function.
		* Although *class declarations* are quite similar to function to *function declarations*, *Class Definitions* do **not** share this hoisting behavior. 
		* One *cannot* instantiate a class before you declare it.


#### 9.3.1 Static Methods p. 420
* One can define a static method within a Class body by prefixing the method declaration with a **static** keyword.
* Static methods are defined as *properties* of the constructor function rather than the properties of the Prototype object.
* For example, let's add the below static **parse** method to Example 9-3:

	```javascript
	static parse(str) {

		let matches = str.match(/^\((\d+)\.\.\.(\d+)\)$/);

		if (!matches) {
			throw new TypeError(`Cannot parse Range from "${str}".`)
		}
		return new Range( parseInt(matches[1]), parseInt(matches[2]) );
	}
	```
* The method defined by this code is **Range.parse()**; it is **not** *Range.prototype.parse()*. Thus, it must be invoked through a *constructor*, **not** just an instance.
	1. This will cause an TypeError: *r.parse is not a function*
		```javascript
		r.parse( '(1...10)'  );
		```
	1. Whereas this usage of a calling a constructor will work and create a brand-new Range object:
		```javascript
		let r = Range.parse( '(1...10)' );
		```
* We will sometimes hear *static methods* referred to as **class methods** b/c they are invoked using the name of the class/constructor.
	* When this term is used, we are contrasting *class methods* with the regular **instance methods** that are invoked on instances of a class.
	* B/c static methods are invoked on the constructor rather than any particular instance, it almost never makes sense to use the **this** keyword in a static method.
	* For more, see Example 9-4 below.


#### 9.3.2 Getters, Setters, and other Method Forms. p. 421
* Within a *class* body, one an define getter and setter methods, just like one can within object literals.
	* The only difference is that in *class bodies*, one does not put a comma after a getter or setter. See Ex 9-4 below.
* In general all the shorthand method definition syntaxes allowed for object literals are also allowed in class bodies.
	* This also includes generator methods (marked with an initial `*`) and methods whose names are the value of an expression in square brackets.


## 7/08/2024 
#### 9.3.3 Public, Private, and Static Fields p. 422
* In the discussion of classes defined like in Example 9-3 (aka defined by the **class** keyword), we have only described methods within the class body.
* The ES6 Standard only allows creation of *methods* and *static methods.*
* ES6 does *not* include syntax for defining fields. (For update and correction, see notes on ES2022 below).
* In ES6, if one wants to define a field on a class instance, it must be done *inside the **constructor** function* or within one of the class methods.
	* If one wants to define a *static field* for a class, ES6 only lets that be done *outside the class body*--**after** the class has already been defined.
	* Example 9-4 includes examples of both kinds of fields.
* To see discussion circa early 2020 on syntax standardization, see p. 422-425.

### Example 9-4: A Class for Complex Numbers p. 425-427
#### A1: Class declaration using old ES6 syntax
* Exactly the same as B1 below except it does *not* include as static fields `ZERO`, `ONE`, etc.

```javascript
class Complex {
	constructor(real, imaginary) {

		this.r = real; // holds the real part
		this.i = imaginary; // holds the imaginary part
	}
	

	plus(that) {
		return new Complex(this.r + that.r, this.i + that.i);
	}

	times(that) {
		return new Complex( 
			this.r * that.r - this.i * that.i, 
			this.r * that.i + this.i * that.r
		)
	}

	static sum( c, d ) { return c.plus(d); }
	static product( c, d ) { return c.times(d); }


	get real() {
		return this.r;
	}

	get imaginary() {
		return this.i;
	}

	get magnitude() {
		return Math.hypot( this.r, this.i );
	}

	toString() {
		return `{ ${this.r}, ${this.i}}`; 
	}

	equals(that) {
		return that instanceof Complex &&
			this.r === that.r &&
			this.i === that.i;
	}
}
```

#### A2: Using old ES6 syntax -- calling a few common classes
```javascript
Complex.ZERO = new Complex( 0,0 );
Complex.ONE = new Complex( 1,0 );
Complex.I = new Complex( 0,1 );
```

#### B1 + B2: New ES6 syntax -- Class declaration and creating a few common classes as static fields within Class body
```javascript

class Complex {
	constructor(real, imaginary) {

		this.r = real; // holds the real part
		this.i = imaginary; // holds the imaginary part
	}
	

	plus(that) {
		return new Complex(this.r + that.r, this.i + that.i);
	}

	times(that) {
		return new Complex( 
			this.r * that.r - this.i * that.i, 
			this.r * that.i + this.i * that.r
		)
	}

	static sum( c, d ) { return c.plus(d); }
	static product( c, d ) { return c.times(d); }


	get real() {
		return this.r;
	}

	get imaginary() {
		return this.i;
	}

	get magnitude() {
		return Math.hypot( this.r, this.i );
	}

	toString() {
		return `{ ${this.r}, ${this.i}}`; 
	}

	equals(that) {
		return that instanceof Complex &&
			this.r === that.r &&
			this.i === that.i;
	}

	static ZERO = new Complex( 0,0 );
	static ONE = new Complex( 1,0 );
	static I = new Complex( 0,1 );
}
```
#### 3: Same syntax for both A and B -- creating new Complex objects and using them

```javascript
let c = new Complex( 6, 10);
let d = new Complex( c.i, c.r);

console.log(c.magnitude);
console.log(Complex.product( c, d));
console.log(c.plus(d).toString());
console.log(Complex.ZERO.toString());
```

### JH notes on ES6 vs. ES2022 syntax for field/property declaration in Classes
* Post ES6, the syntax for declaring fields in classes has evolved. I *think* the final standardization happened in [ES2022](https://www.w3schools.com/js/js_2022.asp), under [Class Field Declarations](https://www.w3schools.com/js/js_2022.asp#mark_class_fields) and [JS Private Methods and Fields](https://www.w3schools.com/js/js_2022.asp#mark_class_fields).
* See also this Dev.To [article on ES 20222](https://dev.to/digitalpollution/embracing-modern-javascript-features-in-es13-es2022-3dde):
	1. [Section 1 - Class Field Declarations](https://dev.to/digitalpollution/embracing-modern-javascript-features-in-es13-es2022-3dde#classFields)
	1. [Section 2 - Private Methods and Fields](https://dev.to/digitalpollution/embracing-modern-javascript-features-in-es13-es2022-3dde#privateMethodsFields) where they introduce the `#` hashtag as a way of setting private methods and fields.
* Read more from Mozilla Dev Network > References > [Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) > [Private properties](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Private_properties).
	* Probably good to read through entire MDN Reference for classes: [Class Overview linked above](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes), [constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor), [extends](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends), [Public Class fields](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Public_class_fields), [static](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static), and [Static Initialization Blocks](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Static_initialization_blocks).

### Section 9.4 Adding Methods to Existing Classes p. 428
* JS's prototype-based inheritance mechanism is dynamic: an object inherits properties from its prototype, even if the properties of the prototype change *after* the object is created.
* This means we can augment JS classes simply by adding new methods to their prototype objects.
* For example, one can add this new method to the Complex object so that users can calculate the complex conjugate using Complex:
```javascript
Complex.prototype.conj = function () {
    return new Complex( this.r, -this.i );
};
```
* The prototype object of built-in JS classes is also open to changes.
* This means that we can add new methods to JS strings, arrays, functions, numbers, etc.
* This is useful for implementing new language features in older versions of JS.
* For example, if we want to invoke a function `f` this many times, passing the iteration number

```javascript
Number.prototype.times = function(f, context) {
    let n = this.valueOf();
    for ( let i = 0;  i < n;  i++ )
        f.call( context, i );
};


let n = 3
n.times ( 
    i => { 
        console.log( `hello ${i}`); 
    } 
);
```
* p. 429 -- Adding methods to prototypes of built-in types like Number in the example above is generally a bad idea b/c it will cause confusion and break compatibility if a future version of JS defines a method with the same name.

### 9.5 Subclasses p. 429
* In traditional OO programming, a class B can *extend* aka *subclass* a class A.
* We say that A is a **superclass** of B; alternately, B is a **subclass** of A.
* The class B can define its own methods, some of which may *override* the methods of the same name defined by superclass A.
* If a method of B overrides a method of A, the overriding B method often needs to invoke the overridden method in A.
* Similarly, the constructor for subclass B *constructor `B()`* must typically invoke the superclass A's *constructor `A()`* in order to ensure that instances are properly initialized.
* Section 9.5.1 demonstrates how to subclass using the old pre-ES6 way.
* Section 9.5.2  then shows how to subclass using modern ES6 syntax using `class` and `extends` keywords.
* Then, Section 9.5.3 talks about using using object composition (aka **delegation**) instead of inheritance; this avoids subclasses entirely.
* Section 9.5.4 (p. 440) discusses **Class Hierarchies and Abstract Classes**.


***

## 7/10/2024 - Flanagan Chapter 10: Modules p. 450
### Three types of modules
1. Do-it-yourself modules using JS classes, objects, and closures
2. Pre-ES6 `require()` and `module.exports = someValue` functions exemplified by Node. **Aka [CommonJS](https://en.wikipedia.org/wiki/CommonJS) (CJS).**
3. Introduced in 2015, native modularity through `import()`, `import`, and `export`. Per this [w3schools summary of ES6](https://www.w3schools.com/js/js_es6.asp#mark_modules), this built-in functionality was only introduced to JS in ES6. **aka [ESM](https://hacks1.wpenginepowered.com/2018/03/es-modules-a-cartoon-deep-dive/) aka ES Modules.**


## 7/12/2024

### Other info
* See here for an [Oct 2023 LinkedIn article](https://www.linkedin.com/pulse/what-commonjs-esm-format-manoj-shrestha/) discussing the difference between Approach #2 (Node / CJS) vs. Approach #3 (ESM, modern `import/export`).
* See also this [2023 history of JS modules](https://8thlight.com/insights/a-history-of-javascript-modules-and-bundling-for-the-post-es6-developer) by Devlin Glasman.
	* Might be a *fourth* approach from the the Glasman article involving AMD (Asynchronous Module Definition), which is used by the package [RequireJS](https://www.tutorialspoint.com/requirejs/requirejs_quick_guide.htm). RequireJS was created in 2009 by David Mark.

### Big picture and next steps
* To better understand the various module systems (esp Node-style CJS and ES6-style ESM), should re-implement Example 9-8. That's the foundation for going through the examples in Chapter 10 on modules.
* After we are satisfied with Chapter 10 on Modules, jump to Flanagan Chapter 15 on modern Web Programming with JS. 
* Note also from p. 715 (text box) : 'there is no longer any need for this book [as of early 2020] to document [legacy web APIs]  or for you to learn about them. **The web platform has matured and stabilized, and if you are a seasoned web developer who remembers the fourth or fifth edition of this book, then you may have as much outdated knowledge to forget as you have new material to learn.**'

## 7/14/2024
* Got Example 9-8 (Flanagan p. 441) fully built `Sets.js` Class hierarchy of new sets working.
	* See `_df9/18-ex-9-8.js` for uncommented version.
* Created fully commented version of `Sets.js` Class hierarchy of new sets. Verified that it's still working.
	* See `_df9/19-ex-9-8-commented.js` for commented version.

## 7/15/2024 - Back to Chapter 10
## 10.1 Modules for Classes and Closures
* p. 450
* Consider Example 9-8, (Flanagan p. 441), which defined several classes, all of which had a *has()* method. 
* One would have no problem writing JS that uses the several classes and subclasses of Set from 9-8.
	* ...because e.g., there is no danger that the `SingletonSet` class's *has()* method will overwrite the `BitSet` class's *has()* method.
* The reason that methods of one class are independent of the methods of other, unrelated classes, is that the methods of each class are defined as **properties** of *independent prototype objects*. 
* The reason that classes are modular is that *objects are modular*.
* Defining a property in a JS object is a lot like declaring a variable. But adding properties to objects does not affect the global namespace of a program; nor doe sit affect the properties of other objects.
* JS defines many math functions and constants. But instead of defining all of them globally, they are logically grouped as properties of the single global `Math` JS object.
* We could have used the same strategy with *Example 9-8* (p. 441). 
	* Instead of defining global classes with names like SingletonSet and BitSet, we could have simply defined *one* global `Sets` class with *properties* for **SingletonSet** and **BitSet**.
	* If we had done that, then users of the `Sets` library would access them via syntax like `Sets.Singleton` and `Sets.Bit`.

### Examples of private functions and variables
* p. 451
* As seen in Section 8.6 on Closures (p. 376), local variables and nested functions--declared inside another function-- are private to that function.
* This means we can use IIFE (immediately invoked function expressions) to achieve a kind of modularity.
* At the same time, we can make the public API of our module return the value of functions.
* Consider the BitSet class. We could structure the module like so:

```javascript
const BitSet = ( 
	function() {
	
		// Private implementation details here
		
		function isValid(set, n) { ... }
		function has( set, byte, bit ) { ...}
		
		const BITS = new Uint8Array( [ 1, 2, 4, 8, 16, 32, 64, 128] );
	
		const MASKS = new Uint8Array( [ ~1, ~2, ~4, ~8, ~16, ~32, ~64, ~128] );
	
		return class BitSet extends AbstractWritableSet {
			// implementation omitted
	
			...
		};
	} () 
);
```

* In the above code (p. 451-452), the public API of the module is in the `return class BitSet extends...` part at the very end. The class can use the private functions and constants defined earlier, but will be hidden from users of the class.
* This approach to modularity becomes more interesting when we have more than one item in it.

#### Stats Module example p. 452

```javascript
const stats = ( 
	function() {
		
		// Utility functions private to the Stats module
		const sum = (x, y) => x + y;
		const square = x => x * x;

		// A public function that will be exported
		function mean(data) {
			return data.reduce(sum) / data.length;
		}

		// A public function that we will export
		function stddev( data ) {
			let m = mean(data);
			return Math.sqrt(
				data.map( x=> x-m ).map(square).reduce(sum) / (data.length-1)
			);
		}

		// We export the public function as properties of an object
		return {
			mean, stddev
		};
	}()
);
```

* And here is a test of how we might use the Stats module

```javascript
let x = stats.mean([1, 3, 5, 7, 9]);
let y = stats.stddev([1, 3, 5, 7, 9]);

console.log(x);
console.log(y);
```

* Tested code above in `live-server`, and it works.

### Section 10.1.1 Automating Closure-Based Modularity
* p. 453. It's a fairly mechanical process to transform a file of JS into this kind of module by inserting some text at the beginning and the end of the file.
* All that is needed is some convention for the file of JS code to indicate which values are to be exported and which are not.
* Imagine a tool that takes a set of files, wraps the content of each of those files within an IIFE (immediately invoked function expression), keeps track of the return value of each function, and concats everything into one giant file.
* The result might look something like the below.

#### Bundle of Sets.js and Stats.js

```javascript
const jhModules = {};

function require( moduleName) {
	return jhModules[moduleName];
}

jhModules["sets.js"] = ( 
	function() {
		const exports = {};
	
		// contents of the sets.js file go here:
		exports.BitSet = class BitSet {...};
	
		return exports;
	} ()
);

jhModules["stats.js"] = (
	function() {
		const exports = {};

		// contents of the stats.js file go here:
		const sum = (x, y) => x + y;
		const square = x => x * x;

		exports.mean = function( data ) { ... };
		exports.stddev = function( data ) { ... };
	
		return exports;
	} ()
);
```

* With the `sets.js` and `stats.js` modules bundled into a single file as above, we could write code like below to use those modules.

```javascript

// Get references to the modules that we need
const statsObj = require("stats.js");
const bitSetObj = require("sets.js");

// Now create objects since those modules are now available
// aka, sets.js and stats.js have been imported

let b = new bitSetObj(100);

b.insert(10);
b.insert(20);
b.insert(30);

let average = statsObj.mean([...b]); // average = 20
```

* The code above is a rough sketch about how code-bundling tools such as `webpack` and `Parcel` for web browsers work.
* It's also a nice intro to the **require()** function used in Node.


## Section 10.2 Modules in Node
* p. 454
* In Node programming, it is normal to split programs into as many small files as seem natural.
* These files of JS code are assumed to all live on a fast filesystem.
* Unlike web browsers, which have to read JS files over a slow / unstable network connection, there is no need or benefit to bundling a Node program into a single JS file.
* In Node, each file is an independent module with a private namespace.
* In Node, constants, variables, functions, and classes defined in one file are **private to that file** *unless* the file explicitly exports them.
* Values exported by one Node module are only visible to another module if the target module *explicitly* imports them.
* Node modules import other modules with the **require()** function and export their public API by: (1) setting properties of the Exports object or (2) replacing the `module.exports` object entirely.


### Section 10.2.1 Node Exports p. 455
* Node defines a global `exports` object that is always available.
* If one is writing a Node module that exports multiple values, one can simply assign them to the properties of this object:

```javascript
const sum  = ( x, y ) => x + y;
const square = x => x * x;

exports.mean = data => data.reduce(sum) / data.length;
exports.stddev = function(d) {
    let m = exports.mean(d);
    return Math.sqrt(
        d.map( x => x - m).reduce(sum) / (d.length-1)
    );
};
```

* Often, however, you want to define a module that exports only a *single* function or class rather than an object full of functions or classes.
* To do this, you simply assign the single value you want to export to **module.exports** like so:

```javascript
module.exports = class BitSet extends AbstractWritableSet {
    // implementation omitted...
};
```

* The default value of `module.exports` is the same object that `exports` refers to.
* In the previous stats module, we could have assigned the mean function to `module.exports.mean` instead of `exports.mean`.
* Another approach with modules like the stats module is to export a single object at *the end of the module*, rather than exporting functions one by one as you go:

```javascript 
// Define all functions, public and private
const sum
const square
const mean = data => data.reduce
const stddev = d => {
};

// Now export only the public ones
module.exports = { mean, stddev };
```

## 7/16/2024
### Experimenting with simple node module loading
* From [W3Schools](https://www.w3schools.com/nodejs/nodejs_modules.asp), how to create and import node modules.
* See `k1-node/3b` which loads `jhModule.js`.



### Section 10.2.2 Node Imports p. 456
* A Node module imports any other module by calling the **require()** function.
* The argument to this function is the mae of the module to be imported. 
* The return value of `require()` is whatever that module exports--typically, this is a function, a class, or an object.
* If one wants to import a system module that is built into Node *or* a module that one has installed via *npm* or a similar package mgr, then one can simply used the **unqualified name** of the module. 
	* i.e., no `/` characters are needed to turn it into a filesystem path.
* Example. The filesystem module **fs** is built into Node. The express web server framework **express** is *not* built into Node. But since Express was installed via NPM on the local filesystem, it is invoked in the same way:

```javascript

// Create a local fsObject by importing the "fs" module
const fsObject = require( "fs" ); 

// Create a local expressObject by importing the "Express" module
const expressObject = require( "express" ); 

```

* When one imports a module of one's own code, the module name should be the path to the file that contains that code, relative to the current module's directory.
	* It is legal to use absolute paths with a `/` character.
	* However, it is more typical to begin with `./` or `../` to indicate that they are in the current directory or relative to somewhere in the parent directory.
* When a module exports just a single function or class, one just needs the `require()` command.
* **However, when you are importing an object with multiple properties**, you have a choice: 
	1. Import the entire object with all it's functions
	1. Import the specific properties only (using the destructuring assignment)

```javascript

/* Approach 1a: import entire object
 */
const statsObject = require('./stats.js');

/* Approach 1b: import entire Stats object but specify that we 
 * that we *only* want the 'mean' property to calcuate avgs
 */
let meanObject = statsObject.mean(data);

/* Approach 2: Use idiomatic destructing assignment
 * to import precisely the exact functions we want
 * directly from the local namespace
 */
const { stddev } = require( './stats.js');

// The below is pretty succinct but loses the context provided
// by the 'stats' prefix to the stddev() function.
let sdObject = stddev( data );
```

### Section 10.2.3 Node-style modules for the web browser
* Exports with an Exports object and a **require()** function are built into Node. 
* But if we are willing ot process our files with bundling tools like *webpack*, then it is possible to to use node-style modules (aka CJS aka [CommonJS](https://en.wikipedia.org/wiki/CommonJS)) for code targeted at web browsers.
* This used to be quite common before ES6. However, now that JS has its own native import/export module syntax, that might become less common.


### 10.3 Native modules in ES6
* ES6 Modules aka ES Modules (aka [ESM](https://nodejs.org/api/esm.html#introduction)), differ from CommonJS in two ways: (1) the syntax for importing and exporting; and (2) how modules are defined in web brosers.

#### Other differences between ESM 'old-fashioned JS scripts for the web'
1. Most obvious difference is the modularity. Aka, in regular scripts, top-level declarations of variables, functions, classes, all go into the smae global context shared by all the scripts.
	* In contrast, whether using CommonJS or ESM, modules create their own private context.
1. Code inside a ESM module is always in **strict mode**. In fact, ESM modules are by default in a sort of 'super-strict mode' more than even Node modules. See p. 459 Flanagan for more.


### Section 10.3.1 ESM Exports
* Under ES6, ESM modules simply add the `export` keyword before the declaration. 
* Approach 1, scatter `export`keywords all over your code

```javascript
export constant numberPi = Math.PI;

export function degreesToRadians(d) {
	return d * numberPi / 180;
}

export class Circle {
	constructor(r) { this.r = r; }
	area() {
		return numberPi * this.r * this.r;
	}
}
```

* Approach 2: Define constants, variables, functions, classes as normal with *no* export keywords. And then, only at the end, write a single export statement that declares what will be exported all in a single block.

```javascript

constant numberPi = Math.PI;

function degreesToRadians(d) {
	return d * numberPi / 180;
}

class Circle {
	constructor(r) { this.r = r; }
	area() {
		return numberPi * this.r * this.r;
	}
}

// NEW consolidated export statment 
export {
	Circle,
	degreesToRadians,
	numberPi
};
```

#### Default exports p. 461
* When a module only exports a single value (typically a function or a class), we tend to use `export default` rather than just vanilla *default*. e.g, `export default class BitSet {   //implementation omitted }`.
* Default exports are a little easier for the target module to import.
* Regular exports with the **export** keyword can only be done on declarations that have a name.
* In contrast, **default exports** can export *any* expression, including anonymous functions.
* This means that if one uses `export default`, one can export object literals. Thus, unlike in regular *export* syntax, when one sees `{}` after a `export default` expression, it really is referring to an object literal.

#### Final notes on exports p. 462
* One may only export at the main level of your JS file. i.e., you *cannot* export a value from inside any lower scope, aka within a class, loop, function, or conditional.

### Section 10.3.2 ESM Imports p. 462
* Simple example of import: `import BitSet from './sets.js';`
* By universal convention, imports are placed at the beginning of a module, although *hoisting* means it's not strictly necessary.
* Here is the syntax if you are importing multiple classes from the same module:

```javascript
import { mean, stddev } from "./stats.js";
```

* You can even import all classes, functions, etc. from a module with `*`: `import * as statsObject from "./stats.js";`.

#### What happens if you try to import from a module that has _not_ defined any exports?
* You just use this syntax `import "./analytics.js";`.
* A module like this runs the first time it is imported. (And subsequent imports do nothing.) 
	* A module that just defines functions is only useful if it exports at least one of those functions. But if a module runs some code, then it can be useful to import even without symbols. 
	* An analytics module for a web application might run code to register various event handlers and then use those event handlers to send telemetry data back to the server at appropriate times. 
	* The module is self-contained and does not need to export anything, but we still need import it so that it does actually run as part of our program.

### Section 10.3.3 ESM import/export renaming p. 466
* If 2 different modules export 2 different values that share the same name, we have to rename one of the imported values to use them. This is accomplished with the `as` keyword, e.g.:

```javascript
import { render as renderImage } from "./imageutils.js";
import { render as renderUI } from "./ui.js";
```

### Section 10.3.4 ESM Re-exports p. 468
* When there are intermediate files that import and export immediately. Sort of a "hello/goodbye" scenario.

### 10.3.5, 10.3.6, 10.3.7 -- JS modules on the Web
* p. 470 - 477
* Probably best to read these after we finish Flanagan Chapter 15 on Web Programming

***

## 7/16/2024
## Flanagan Chapter 15 Web Programming p. 713
* aka front-end or client-side JS

### 15.1.1 JS inside HTML `<script>` tags
* Although one can place JS code directly in-line within an HTML page, it's far more common now to use the **src** attribute of the `<script>` tag like so: 

```html
<script src="client-scripts/digitalClock.js"></script>
```

* Important note: HTML does *not* support this concise syntax `<script/>`. One must *always* have an opening and closing script tag like so: `<script> </script>`.
* p. 718-719. When importing JS modules, one must load the top-level module with the **type="module"** of the `<script>` tag. See section 10.3.5 for complete detials.

#### No languages supported other than JS p. 719
* Back in the 90s, there was a thought that non-JS languages would be supported, leading to the **langauge="javascript"** and **type="application/javascript"** attributes of the `<script>` tag. 
* Turns out that is not needed b/c JS is the only language of the web. So basically can ignore the `language=` and `type=` attributes of script with the possible exception of embedding live data in a web page.

#### 'defer' and 'async' attributes of the <script> tag
* In the 90s before formalization of the DOM, JS modified HTML page content using the **document.write()** method.
* Back then, `document.write()` tag would execute wherever it is in the HTML page. One hack people used to do was to place all the documents.write() statements at the bottom of the page. 
	* This way, JS would only execute after the other HTML content had first loaded in the client browser.
* That style is now deprecated, esp. since a `<script>` with a **document.write()** statement placed in *the middle* of an HTML page would **blocking** aka **synchronous**. (see p. 720.)
* Solution: introducing the **async** and **defer** attributes as part of the `<script>` tag.
	* Getting conflicting (possibly wrong) answers from ChatGPT about when **async** and **defer** were introduced. 
	* For now, let's assume that browsers started supporting them around 2009, was formally supported as a 'W3C Recommendation' in October 2014.
* Syntax:

```html
<script defer src="deferred.js"></script>
<script async src="async.js"></script>
```

* Note, per this [phind.com answer](https://www.phind.com/search?cache=j3l4x7oq4j2f8ktvtyqibe8w), one can place the **defer** and **async** attributes after the **src=** attribute. Like so:

```html
<script src="deferred.js" defer ></script>
<script src="async.js" async ></script>
```
* Both defer and async are ways of telling the browser that the linked script does not use `document.write()` to generate HTML output.
	* Therefore, the browser can continue to parse and render the document while simultaneously downloading the script.
* **The defer attribute** of the `<script>` tag causes the browser to defer execution of the script until after the document has been fully loaded and is ready to be manipulated.
* **The async attribute** of the `<script>` tag causes the browser to run the script as soon as possible but *does not block document parsing while the JS is being downloaded* to the client browser.
* If a `<script>` tag has both attributes, the **async** attribute takes precedence.
* Scripts with the **type="module"** attribute are automatically executed after the document has been downloaded to the client; as if it had the **defer** attribute. This can be overridden by paring type=module with an **async** attribute in the same `<script>` tag.
## 7/17/2024
### 15.1.2 Brief intro to the DOM p. 722
* Short intro; there is much more detail on the DOM in Section 15.3 (p. 760).
* The DOM API mirrors the tree structure of an HTML document. 
* For every HTML tag in the document, there is a corresponding JS *Element* object.
* For every run of text in the HTML document, there is a corresponding JS *Text* object.
* The *Element*,*Text*, and *Document* classes are all subclasses of the **Node** superclass.
* *Node* objects are organized into a tree structure that JS can query and traverse using the DOM API.
* The DOM API includes methods for creating new **Element** and **Text** nodes, inserting them into the document as children of other **Element** objects, moving them around the document, and for deleting them from the document.
* There is a JS class that corresponds to every single HTML tag type.
* Each occurrence of a tag in a document is represented by an instance of the class. Examples:
* The HTML `<body>` tag is represented by an instance of the JS **HTMLBodyElement** class.
* The HTML `<table>` tag is represented by an instance of the JS **HTMLTableElement** class.
* The HTML `<img>` tag is represented by an instance of the JS **HTMLImageElement** class. Note also that HTMLImage has a JS `src` property that corresponds to the *src* attribute of the HTML `<img>` tag.

### 15.1.3 The Global Object in Client Browsers
* There is one global object per browser or tab.
* All the JS code running in that window shares that same global object.
* This is true regardless of how many scripts or modules in the document. Furthermore, that means that any property is visible to all other scripts.
* The global object is where the JS standard library is defined, including the **parse()** function, the `Math` object, the `Set` class, etc.
* The **document** JS property of the window's global object represents the currently displayed document.
* The global object's **fetch()** method makes http network requests.
* The global object's **Audio()** constructor allows JS programs to play sounds.
* In web browsers, the global object does double duty. In addition to defining built-in types and functions, the global object also represnts the current web browser window.
* The global object defines properties like **history** (represent the window's browsing history, see Section 15.10.2), **innerWidth** (window's current width in pixels).
* A critical property of the global object is named **window**, and the value is the global object itself.
	* This means you can simply type `window` to refer to the global object in your client-side code.
	* When using window-specific features, it is often good to include the `window.`- prefix. eg, `window.innerWidth` is clearer than just `innerWidth`.

### 15.1.4 Scripts all share a namespace p. 727
* Module-based scripts are clean b/c functions, classes, variabless, etc are private to their module. (Unless one of those items are explicitly exported with the `export` or `object.export` keywords.)
* In contrast, non-module scripts all share the same global namespace of a document.
	* This can be convenient for small JS programs, but once you include 3rd-party libraries, it all becomes a mess.
* This is one reason to use `let`, `class`, and `const` from ES6. 
	* Unlike the legacy `var` and `function` declarations which create properties on the shared global object, modern keywords do not create properties on the global object.
	* **Note:** however `let`, `class`, and `const` *still* live in the shared namespace.

### 15.1.5 Execution of JS programs p. 728
* There is no formal definition of a 'program' in client-side JS.
* But in general, a JS program consists of all the bits of JS code within or referenced from a single HTML document.
* All of these separate bits of code share a single global **Window* object; they all have access to the same underlying **Document** object.
* Scripts that are not modules also share a top-level namespace.

#### iFrames p. 728-729
* If a webpage includes an embedded frame (i.e., using the `<iframe`> element), the JS code in the embedded document has a *different global object* than the enclosing window.
	* Thus, the iframe also has a distinct Document object and global object from the enclosing window.
* However, if the container document and the contained document are both loaded from the same server, the code in one document can interact with the code in the other document.
* See Section 15.13.6 (p. 957) for more info on how to send messages can be passed between JS in the containing window and the JS in the contained iframe.

#### Sequence p. 729
* One can think of JS program execution as occurring in two phases.
* **Phase 1:** the document content is loaded, and the code from the `<script>` elements is run.
	1. Scripts generally run in the order in they are placed in the doc (modulo **defer** and **async** attributes of the `<script>` tag).
	1. The JS code within any single script is run from top to bottom, subject to standard JS control-flow.
	1. Some non-obvious things might happen like the creation/loading of various classes and objects so they are available for Phase 2.
* **Phase 2:** After the document is loaded and all scripts have run, then the asynch and event-driven part of JS execution starts.
	1. If a script is going to be active in Phase 2, then one of the things it must have done during Phase 1 is to register at least *one* event handler or callback function that will be invoked async.
	1. During the event-driven Phase 2, the browser invokes event handler functions and other callbacks in response to things that happen asynch.
	1. Event handlers are most commonly invoked in response to user input (mouse clicks, keystrokes, etc.) but also by network activity, resource loading, elapsed time, or errors in JS
	1. For more on events and event handlers, see Section 15.2.

#### More on Phase 2 events p. 730
* Some of the first events to happen in Phase 2 are the **DOMContentLoaded** and **load** events.
	* *DOMContentLoaded* is triggered when the HTML document has been completely loaded and parsed.
	* The *load* event is triggered when all the document's external resources (e.g., images) are also fully loadd.
* JS programs often use one of the above events as a trigger or starting signal.
* It is common to see programs whose scripts define functions but take no action other than registering and event handler function to be triggered by the *load* event at the beginning of Phase 2.
	* This *load* event handler than manipulates teh document and does whatever it is that the program is supposed to do.
* Note: it is common in JS programming for an event handler function such as *load* to register yet other event handler functions.
* Phase 1 is relatively short, and should ideally be less than 1 second.
* Once a document is loaded, Phase 2 lasts as long as the document is displayed in the web browser.

### Client-Side JS Threading Model p. 731
* JS is a single threaded language. Single-threaded execution makes for simpler programming.
* One can assume that two event handlers will *never* run at the same time.
* One can manipulate the document knowing that no other thread is attempting to modify it at the same time.
* One never need worry about race conditions etc. when writing JS code.
* Single-threaded execution means that web browsers stop responding to user input while scripts and event handlers are executing.
* However, this means that JS programmers have to be careful to keep their execution times short b/c they don't want the user to be waiting while their page hangs.
	* If an event handler performs a computationally intensive task, the browser may become nonresponsive, possibly causing the user to think that it has crashed.

#### Web workers p. 731
* The web platform defines a controlled form of concurrency called a **web worker**.
* A web worker is a background thread for performing computationally intensive tasks without freeing the UI.
* The code that runs in a web worker thread does not have access ot document content. 
	* Web worker JS does not share any state with the main thread or with other workers.    
	* Web worker JS can only communicate with the main thread and other workers through asynch message events so that concurrency is not detctable in the main thread.
* Thus, **web workers do *not* change the single-threaded execution model** of JS.
* See Section 15.13 for more on safe threading and web workers.

#### Client-Side JS Timeline p.732
##### More detailed breakdown of the steps in a client-side web page live, more granular than the *Phase 1* and *Phase 2* distinction from above.
1. The web browser creates a **Document object** and begins parsing the web page, adding **Element objects** and **Text nodes** to the document as it parses HTML elements and their textual content. The `document.readyState` property has the value *loading* at this stage. 
1. When the HTML parser encounters a **`<script>`** tag that does not have any of the *async*, *defer*, or *type="module"* attributes, it adds that script tag to the document and then executes the script. 
	* The script is executed synchronously, and the HTML parser pauses while the script downloads (if necessary) and runs. 
	* A script like this can use **document.write()** to insert text into the input stream, and that text will become part of the document when the parser resumes. 
	* A script like this often simply defines functions and registers event handlers for later use, but it can traverse and manipulate the document tree as it exists at that time. 
	* That is, non-module scripts that do not have an *async* or *defer* attribute can see their own `<script>` tag and document content that comes before it.
1. When the parser encounters a `<script>` element that has the async attribute set, it begins downloading the script text (and if the script is a module, it also recursively downloads all of the script’s dependencies) and continues parsing the document. 
	* The script will be executed as soon as possible after it has downloaded. 
	* But the parser does not stop and wait for it to download. 
	* Asynchronous scripts must *not* use the **document.write()** method. They can see their own `<script>` tag and all document content that comes before it, and may or may not have access to additional document content.
1. When the document is completely parsed, the **document.readyState** property changes its value to *interactive*.
1. Any scripts that had the *defer* attribute set--along with any module scripts that do *not* have the *async* attribute--are executed in the order in which they appear in the document.
	* Async scripts may also be executed at this time.
	* Deferred scripts now have access to the complete document and they must *not* use the **document.write()** method.
1. The browser fires a **DOMContentLoaded** event on the **Document** object.
	* This marks the transition from Phase 1 to Phase 2.
	* Note, however, that there may still be *async* scripts that have not yet executed at this point.
1. This marks the transition from Phase 1 to Phase 2.
	* Note, however, that there may still be *async* scripts that have not yet executed at this point.
1. Phase 2 is in full swing. The document is fully parsed at this point.
	* But the client browser may still be waiting for additional content, such as images, to load.
	* When all such content finishes loading, and when all *async* scripts have loaded and executed, the **document.readyState** property changes state to *complete* and the browser now fires the *load* event on the **Window** object.
1. From this point on, event handlers are invoked asynchronously in reponse to user input events, network events, timer expirations, etc.

### 15.1.6 Program Input/Output p. 734
* Like any program, client-side JS programs process input data and then produce output data. Here are some types of input:
	1. The content of the document itslef, which the JS code can access via the DOM API.
	1. User input in the form of events. The HTML **`<button>`** element may respond to mouse clicks or touchscreen taps. Or, the HTML **`<textarea>`** element may accept text input. See Section 15.2 for more.
	1. The URL of the document being displayed is available to client-side JS as the **document.URL**. If one passes this string to the **URL()** constructor (Section 11.9), one can easily access the path, query-string, and other sections of the URL.
	1. The content of the http *Cookie* request header is available to the client-side code as **document.cookie**.
		* Cookies are usually used by server-side code to maintain user ssessions but client-side code can also use them when needed.
		* See Section 15.12.2 (p. 932) for more.
	1. The global **navigator** property provides access to info about the web browser, the OS it's running on, and the capabilities of each. For example:
		* **navigator.userAgent** is a string that identifies the web browser.
		* **navigator.language** is the user's preferred language.
		* **navigator.hardwareConcurrency** returns the number of logical CPUs available to the web browser
		* the global **screen** property provides access to the user's display size via the **screen.width** and **screen.height** properties.
		* In a sense, the **navigator** and **screen** objects are to web browsers as environment variables are to Node programs.

#### JS client-side output p. 735
* Client-side JS typically provides output by manipulating the DOM api; or by using a framework like React, Angular, Vue, Next.JS to manipulate the document.
* Client-side code can also use **console.log()** and related methods to produce output. 
	* **Note:** *console.log()* output can only be viewed in the developer tools console. So this is useful for debugging that is hidden from end-users.

### JS Program Errors p. 735
* Unlike Node applications and other apps running directly on the OS, a JS program in a web browser can't really 'crash'.
* If an exception occurs while your client-side JS is running and you do not have a **try/catch** statement to handle it, an error message will be displayed to the dev tools console.
	* **But**, any event handlers that have ben registered keep running and responding to events. 
* To define an error handler of last resort, set the **onError** property of the *Window* object to an error handler function.o
* for more on handling of Promises and managing the call stack, view p. 735-736.

### 15.1.8 The Web Security Model p. 737
* There are two competing goals that browser-makers try to balance:
	1. Preventing malicious code from running that can read or alter user data, compromise user privacy, etc.
	1. Make client-side APIs powerful and effective for building web apps.

#### What JS Can't Do p. 737
* The first line of defense is that some web browsers simply don't support certain capabilities. 
* E.g., client-side JS does not provide any way to write or delete arbitrary files or list arbitrary directories on the client computer.
* This means that the vanilla JS cannot simply delete data or plant viruses.
* Furthermore, client-side JS does not have general networking capabilities. Although there APIs like the below, general-purpose internet clients and servers cannot be written with client-side JS. 
	* A client-side JS program can make (only?) make http requests. (Section 15.11.1 for more.)
	* The WebSockets API defines a socket-like affordance for communicating with specialized servers (Section 15.11.3)

#### Same-Origin Policy p. 738
* The *same-origin policy* is a sweeping security restriction of what web content JS code can interact with.
* It typically comes into play when a web page includes `<iframe>` elements.
* In this case, the same-origin policy governs the interactions of JS code in one frame with the content in other iframes.
* The origin of a document is defined as the protocol, the host, and the port of the URL from which the document was loaded.
* Documents loaded from different web servers have different origins; documents loaded via different ports on the same host also have different origins.
* A document loaded with the `http:` protocol has a different origin than the `https:` protocol even if they come from the same web server.
* Browsers typically treat every **file:URL** as a separate origin.
* **Note:** the origin of the script is not relevant to the same-origin policy. What matters is the orign of the **document** in which the script is embedded. (see p. 738-739 for more.)
* The same-origin policy poses problems for large websites with multiple subdomains like *www.example.com* and *store.example.com*. Two solutions:
	1. Alter their origin by setting the **document.domain** to the domain suffix.
	1. **CORS** aka Cross-Origin Resource Sharing 

***

## 7/18/2024
* Tested xss scripting example below on localhost with `live-server` and it worked.

#### Cross-Site Scripting p. 740
* **XSS** aka **cross-site scripting** is a term for a category of security issues in which an attacker injects HTML tags or scripts into a target website.
* Front-end devs must guard against XSS.
* A web page is vulnerable to XSS if it dynamically generates document content and bases that content on user-submitted data without first *sanitizing* that data by removing any embedded HTML tags from it.
* As a trivial example, consider the following HTML page that uses JS to greet users by name:

`<script>`

```javascript
let userName = new URL(document.URL).searchParams.get("userName");
document.querySelector('h1').innerHTML = "Hello " + userName;

```

`</script>`
* The 2-line script extracts input from the "userName" query parameter of the document URL.
* It then uses the DOM API to inject an HTML string inot the first `<h1>` tag in the document.
* The page is intended to be invoked with an URL like this: `http://www.example.com/greet.html?userName=Jeff`.
* When used likje this, it displays the text "Hello Jeff". 
* **But**, consider what happens when it is invoked with this query parameter `userName=%3Cimg%20src=%22x.png%22%20onload=%22alert(%27hacked%27)%22/%3E`. When the URL-escaped parameters are deoded, the URL causes this HTML to be injected into the document: `Hello <img src="x.png" onload="alert('hacked')"/>`.
	* After the image loads, the string of JS in the **onload** attribute is executed and the global **alert()** function displays a modal dialogue window to appear.
	* Of course, a single dialog box is relatively benign, but demonstrates that arbitrary code execution is possible on this site b/c it allows unsanitized HTML.
* XSS is called this b/c more than one site is involved.
	* Site B includes a specially created link to Site A.
	* If Site B can convince users that that it is a legit site and they can click the Site B lin, they will be taken to Site A--**but now Site A will be running code from Site B**!
	* Exploit 1: deface the page or cause other malfuctions on Site A.
	* Exploit 2: Even worse, can read account info and other stuff from cookies stored by Site A, sending that data back to Site B.
	* Exploit 3: Injected code could even track user keystrokes and send that data back to Site B.
* **Solution I:** replace special HTML characters in untrusted input string with their equivalent HTML entities. (see example on p. 741-742.
* **Solution II:** Structure web app so that untrusted content is always displayed in an `<iframe>` with the **sandbox** HTML attribute set to disable scripting and other capabilities.

### 15.2 Events p. 742
* Client-side JS use an async, event-driven programming model. This means that the browser generates an **event** every time something interesting happens to the document, browser, or associated element/object.
* In client-side JS, events can occur on any element within an HTML document. This means that web browsers are *more complicated than Node programming*.

#### Definitions related to events p. 743 - 745
1. **Event Type** aka **Event Name**
	* This string specifies what kind of event occurred. 
	* For example, *type* **mousemove** means that the user has moved the mouse. 
	* The *type* **keydown** means that the user has pressed a key on the keyboard down.  
	* The *type* **load** means that a document or some other resource has finished loading on the client from the network.
	* B/c the type of an event is just a string, it's sometimes called an *event name*.
1. **Event Target**
	* This is the object upon which the event occurred or with which an event is associated.
	* When we speak of an event, we must specify both the type and the target
	* A **load** event *on* a `Window`, for example, or a **click** event *on* a `<button>` element.
	* The most common event targets are Window, Document, and Element objects.
	* Other targets include **Worker objects** (see Section 15.13 on threads). Workers are targeted by *message* events when a worker thread sends a message to the main thread.
1. **Event Handler** aka **Event Listener**
	* This function handles or responds to an event. Applications register their event handler functions with the web browser, specifying *event types* and *event targets*. 
	* When an event of the specified type occurs on the specified target, the browser invokes the handler function.
	* When event handlers are invoked for an object, we say that the browser has 'fired', 'triggered', or 'dispatched' the event.
	* There are a number of ways to register event handlers; see Sections 15.2.2 and 15.2.3 for more.
1. **Event Object**
	* Event objects are associated with a particular event and contains details about that event.
	* Event objects are passed as arguments to the event handler function.
	* All event objects have a **type property** that specifies the event type and a **target property** specifying the event target.
	* Each event type defines a set of properties for its associated event objects.
	* e.g., a *mouse event object* includes coordinates of the mouse pointer.
	* e.g., a *keyboard event object* includes key pressed and associated modifier keys that were also pressed.
1. **Event Propagation**
	* Event propagation is the process by which a browser decides which objects to trigger event handlers on.
	* For events that are specific to a single object--such as the **load** event on the *Window* object or a **message** event on a *Worker* object--no propagation is required.
	* But when certain kinds of events occur on elements within the HTML document, they propagate up the document tree.
		* If the user moves the mouse over a hyperlink, the **mousemove** event is first fired on the `<a>` element that defines the linke. 
		* *Then*, the event is fired on the containing elements: perhaps a `<p>` element, a `<section>` element, or the Document object itself.
	* It is sometimes more convenient to register a single event handler on a Document or some other container element than to register handlers on each individual element you're interested in.
	* An event handler can stop the propagation of an event so that it will not continue to bubble and will not trigger handlers on containing elements.
	* Handlers do this by invoking a a method of the event object.
	* In another form of event propagation, known as **event capturing**, handlers specially registered on container elements have the opportunity to intercept (aka *capture*( events before they are delivered to their actual target. See Section 15.2.4 for more.
1. **Default Actions**
* Some events have default actions associated with them. 
* e.g., when a click event occurs on a hyper link, the default action is for the browser to follow the link and load a new page. Event handlers can prevent the default action by invoking a method for the event object.
	* This is called **cancelling** the event. See Section 15.2.5

## 7/19/2024
### 15.2.1 Event Categories
* Client-side JS suppports so many *event types* that this chapter will not cover them all.
* However, this book will group events into a few common categories.
	1. **Device-dependent input events** Examples: mousedown, mousemove, mouseup, touchstart, touchmove, touchend, keydown, keyup
	1. **Device-independent input events** Events that are device agnostic. e.g., 
		* The *click* event indicates that a link or button (or other document element has been activated. This activation can come from a mouse click, a keyboard, or with a tap on a touch screen.
		* The *input* event is a device-independent superclass of keydown which supports keyboard input, as well as cut-and-paste, and methods used for ideogram based scripts like Chinese.
		* The *pointerdown*, *pointermove*, and *pointerup* event types are device-independent alternatives to mouse and touch events, which respond to pointers, touch-screens, pen- and stylus- inputs.
	1. **User Interface events** aka UI events are higher-level events. Often on HTML form elements.
		* *Focus* event is when a text input field gains keyboard focus.
		* *Change* event is when a user changes the value displayed by a form element.
		* *Submit* event is when a user clicks a **Submit** button in a form.
	1. **State-change events**
	1. **API-specific events**


## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.

`<script>`
