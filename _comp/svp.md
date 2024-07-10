---
title: SVP JS
permalink: /svp/
---

## Notes on Laurence Lars Svekis, Maaike van Putten, Rob Percival
* JS from Beginner to Professional
* Published 2021, Pakt Publishing

## 7/08/2024
## Chapter 7: Classes
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
let p2 = new Person("Jane");
console.log(p2);
```
* The output is `Person { firstName: 'Jane', lastName: undefined }`

### Default values for Class Fields p. 153
* One can specify default values in the constructor function. (See ES2022 notes on private fields but SVP was published in 2021).
* Let's rewrite the Person Class like so:
```javascript

class Person {
	constructor(firstName, lastName = "Doe") {
		this.firstName = firstName;
		this.lastName = lastName;
	}
}
```
* Which would now return `Jane Doe` if we invoke the Person constructor like so:
```
let p3 = new Person("Jane");
console.log( p3.firstName + " " + p3.lastName);
```

### Methods p. 154
* In a class, we an specify functions.
* This means that our object can start doing things using the object's own properties--for example, printing a name.
* Functions on a class are called methods. 
* When defining these methods, we don't use the `function` keyword; instead we just use the name followed by `()`.
```javascript

class Person {
	constructor (firstName, lastName = "Doe") {
		this.firstName = firstName;
		this.lastName = lastName;
	}

	invite() {
		console.log( "Hey, please come in! My name is " + this.firstName + ".");
	}
}

let p1 = new Person("John", "Smith");
p1.invite();
```
* Outputs: `Hey, please come in! My name is John.`.


### Properties p. 156
* Properties aka fields, hold the Class's data. We've already seen some properties already: `firstName` and `lastName`. 
* Often it is not desirable to provide direct access to properties. (Ah, they use the `#` hashtag standard from ES2022 for private fields!)
* See `_ch7/3b-private-field-validation.js` for working example version of SVP example on p. 157.


## Accessors -- Getters and Setters p. 157
* Although **accessors** -- like **getters** and **setters** -- *look* like functions b/c they have a `()`. They are in fact *not*. They are **properties** aka data fields.
* Very important point: if you try to call an object's properties *as if* it were a function (aka using **()**), you will get an error. So for example,
```javascript
class Cat{
    #name
    #color

    // Appropriate getters and setters for #name and #color

}


let c = new Cat("Mittens", "Black");
```
* If one tries to access the cat's name with `c.name()`, **this will cause an error**. But `c.name` will work.
* Accessors are declared with the `get` and `set` keywords.
* Properties cannot be set from the outside *without* the special access method provided by a Class and its instances. In other words, the object is always in control. This principle is called **encapsulation**.

