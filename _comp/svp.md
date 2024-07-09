---
title: SVP JS
permalink: /svp/
---

## Notes on Laurence Lars Svekis, Maaike van Putten, Rob Percival
* JS from Beginner to Professional
* Published 2021, Pakt Publishing

## 7/08/2024
## Chapter 10: Classes
* See proj2 *.js files to see Dog implementations from p. 151.
* p. 152

### Constructors p. 152
* A *constructor method* is a special method that we use to initialize objects with our `class` blueprint. 
* *There can only be **one** constructor per Class.*
* The constructor method contains properties that will be set when initiating the class. e.g.
```javascript
class Person {
	constructor (firstName, lastName) {
		this.firstName = firstName;
		this.lastName = lastName;
	}
}
```
* Under the hood, JS creates a special function based on this contructor method.
* This function gets a class name and it will create an object with the given properties.
* With this special function, one can create instances (aka objects) of that class. Here is the syntax:
```javascript
let p = new Person("Joe", "Black");
```
* The **new** kewyord tells JS to look for the special constructor function in the `Person` class and create a new *Person* object.
* In most other languages, if you try to invoke a Class's `constructor` function to create an instance of that class *without* putting in the correct number & type of input arguments, the program crashes.
* *However*, in JS, it fails gracefully by leaving the missing parameters as `undefined`. So in the above example, if we called the Person constructor function like so:
```javascript
let p2 = new Person("Alice");
console.log(p2);
```
* The output is `Person { firstName: 'Alice', lastName: undefined }`
