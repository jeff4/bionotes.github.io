---
title: SVP JS
permalink: /svp/
---

## Notes on Laurence Lars Svekis, Maaike van Putten, Rob Percival
* JS from Beginner to Professional
* Published 2021, Pakt Publishing
* SVP = Svekis, van Putten, Percival

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

### Inheritance p. 159
* Example of `Vehicle` that has a `Motorcycle` subclass. See `/proj-2/_ch7-classes/4a-vehicles.js`. 
* In the `Motorcycle` constructor, we see the **super** keyword. This is calling the constructor function from the parent class `Vehicle`, which means that all the **fields** from superclass Vehicle are also populated; plus all the Vehicle's superclass **methods** are available for free.
* *Calling **super** is NOT optional.* If you are ever calling a class that is a child of another class, *you must always call `super`.* p. 160


### Prototypes p. 161
* A prototype is the JS mechanism by which it makes possible to create objects. When nothing is specified when creating a class, the objects inherit from the **Object.prototype** prototype.
* This is a rather complex built-in JS class that we can use.
* We don't need to look at how the `Object.prototype` is implemented in JS; we just need to know that it is the base object that is always at the very top of the inheritance tree. `Object.prototype` is always present in every JS object.
* There is a prototype **property** available to all classes, and it always named *prototype*. It can be accessed by typing `ClassName.prototype`.
* Let's use an example with the Person class p. 161. See `4b-prototype-person.js`.
* Finished with Chapter 7. 

***

## 7/22/2024

# SVP Chapter 9: The DOM
### HTML Crash Course
* p. 206 HTML elements
* We open every element with a `<elementName>` and close every element with a `</elementName>`.
* p. 208 The html `<Head>` element contains a lot of things meant for the browser and not the end user. This incluces:
	* CSS
	* JS scripts
	* metadata e.g., info for search engines
* Example

```html
<head>

	<title> Title that appears in browser tab </title>
	<meta name="page description in Google" content="This is the preview that appears in Google." >
	<script src="externalJavaScript.js"></script>

</head>
```
* See p. 209 for an example of common HTML tags

### HTML Attributes p. 210

| **Attribute name** | **Description**                                                                 | **Can be used on which element?**                       |
|--------------------|---------------------------------------------------------------------------------|---------------------------------------------------------|
| `id`               | Gives an element a unique ID, such as age.                                      | All of them                                             |
| `name`             | Used to give a custom name to an element.                                       | `input`, `button`, `form`, and quite a few we haven't seen yet |
| `class`            | Special metadata that can be added to an element. This can result in a certain layout or JavaScript manipulation. | Almost all of them inside body                          |
| `value`            | Sets the initial value of the element it is added to.                           | `button`, `input`, `li`, and a few we haven't seen yet  |
| `style`            | Gives a specified layout to the HTML element it is added to.                    | All of them                                             |

### BOM - Browser Object Model p. 211
* The BOM, aka the **window browser object** is the amazing 'magic' element that makes it possible to communicate with the browser.
* The window object contains all the properties required to represent the window of the browser.
* Each browser has its own implementation of the BOM.
* For more on relationship between BOM and DOM, see ChatGPT from 7/22/2024.

### Excerpt from ChatGPT (7/22)
#### What is BOM?
The **Browser Object Model (BOM)** is a representation of the browser's environment. It provides the objects through which you can interact with the browser itself, outside the context of the page content. This includes objects like `window`, `navigator`, `location`, `history`, and `screen`.

#### Key Features of BOM:
- **Browser Interaction**: Allows interaction with browser properties and methods, such as manipulating the browser window, accessing browser history, and retrieving information about the user's screen.
- **Independent of HTML**: Unlike the DOM, the BOM is not related to the document's structure but rather to the browser environment itself.
- **Window Object**: The `window` object is the global object in a browser environment, and all other BOM objects (like `navigator`, `location`, etc.) are its properties.

#### How BOM Relates to HTML and Front-end Development:
- **Browser Control**: BOM allows developers to control browser behaviors, which is crucial for tasks like redirection, detecting browser capabilities, or working with browser storage.
- **Supplementing DOM**: While the DOM handles document structure, the BOM provides the ability to interact with the broader environment, offering additional functionality beyond just document manipulation.

#### Relationship Between DOM and BOM

While the **DOM** and **BOM** serve different purposes, they often work together in front-end development to create dynamic, interactive web applications.

- **`window` as a Bridge**: In the browser, the `window` object acts as a bridge between the DOM and BOM. The `document` object is a property of the `window`, and it represents the DOM. Therefore, when you interact with `document`, you're accessing the DOM through the BOM's `window` object.
- **Complementary Roles**: While DOM manipulations change the content and structure of a web page, BOM provides the ability to interact with the browser itself, offering a complete suite for building rich web applications.
- **JavaScript Integration**: Both the DOM and BOM are integral to JavaScript in the browser. JavaScript relies on the DOM for document manipulation and the BOM for browser-level operations, making it a powerful language for front-end development.
- **User Experience**: Together, the DOM and BOM enable developers to create highly interactive and user-friendly experiences. For example, dynamically updating the content of a page (DOM) and managing browser sessions or detecting user settings (BOM) can lead to a seamless user experience.


***

## 7/23/2024

### More in SVP Chapter 9 
* p. 212. Can inspect tree within Dev Tools > Console by typing `console.dir(window)`.  
* p. 213 `window.history.length` outputs length of history object.
* p. 214. `console.dir(<OBJECT>)` shows all properties of whatever JS object listed in <OBJECT>.
* p. 214 allows browser to see how many previously visited pages in the length of the stack that is returned by the `console.dir(history)` command.
	* To go 1 page back, type `window.history.go(-1)`
	* To go 2 pages back, type `window.history.go(-2)`
* p. 216 The URL of the current webpage is found in the JS property **window.property**. Thus within Dev Tools > Console, type `console.dir(window.location)` or equivalently, `console.dir(location)` .
* I quite like the Safari Dev Tools. Just like FireFox on macOS, both are accessible via **cmd+option+I**.
	* In Safari, to access JS console, **cmd+option+C**
	* In FireFox, to access JS console, **shift+option+J**. This doesn't work the way I want. 
* From ChatGPT, the Safari Dev Tools Console, the **O** icon = *Objects*, the **F** icon = *Function*, the **S** icon = *String*, 
* Completed Practice Exercise 9.2 on p. 217

### SVP's treatment of the DOM p. 217
* Exercise on p. 220 - 221. HTML is entered into `t11.html`. Then tried this in the FireFox Dev Tools Console successfully.


```javascript
const ele1 = document.querySelector("h1");
console.dir(ele1);
```

* And output is as expected: the properties of the **h1** JS object. Now let's try to select all elements with the HTML class name `< ELEMENT class="output">`

```javascript
const eles = document.querySelectorAll(".output");
console.dir(eles);
```
* Completed everything in Chapter 9. Except might be worthwile to do Practice Exercise 9.3, Chapter Project (Manipulating HTML elements with JS), and Self-Check Quiz (p. 221 - 223)

### Chapter 10: Dynamic Element Manipulation Using the DOM p. 225
* Topics: basic DOM travseral, DOM element access, Element click handler, `this` keyword in the DOM, changing the class of an element, event listeners

#### Basic DOM traversal p. 226
* had some success and some failure in trying to implement commands from p. 225 - 229. 
* Sample HTML page

```html
<!DOCTYPE html>
<html lang="en">
	<body>
		<h1> Let's find the treasure! </h1>
		<div id="forest">
			<div id="tree1">
				<div id="squirrel"></div>
				<div id="flower"></div>
			</div>
			<div id="tree2">
				<div id="shrubbery">
					<div id="treasure"></div>
				</div>
				<div id="mushroom">
					<div id="bug"></div>
				</div>
			</div>
		</div>
	</body>
</html>
```

* Sample commands in Dev Tools Console:

```javascript
document.body.children.forest.children.tree2.parentElement;
document.body.children.forest.children.tree2;
document.body.children.forest.children.tree2.previousElementSibling;
document.body.children.forest.children.tree1.nextElementSibling;
```

### Selecting elements as objects p. 229

* Sample HTML page

```html
<!DOCTYPE html>
<html lang="en">
	<body>
		<h1> Welcome page </h1>
		<p id="greeting">
			Hi!
		</p>
	</body>
</html>
```

* Let's traverse to the `<p>` element with this JS command in the browser's Dev Tools console: **document.body.children.greeting**.
	* Output: `<p id="greeting">`

#### Changing innerText p. 230
* We can then assign a new value using the `innerText` property with this command:

```javascript
document.body.children.greeting.innerText = "Goodbye, my friend! 👋" 
```

* Which changes *`<p id="greeting">Hi</p>`* into **`<p id="greeting">Goodbye, my friend! 👋</p>`**


#### Changing innerHTML p. 231
* If we want to change not just the plain text but also the HTML tags, we use edit the **innerHTML** property. 

### Accessing elements in the DOM p. 231 - 233
* Now let's use this new HTML

```html
<!DOCTYPE html>
<html lang="en">

	<body>
		<h1> Just an example</h1>
		<div id="one" class="example">Hi!</div>
		<div id="two" class="example">Hi!</div>
		<div id="three" class="something">Hi!</div>
	</body>

</html>
```

* Let's access the elements by ID.
