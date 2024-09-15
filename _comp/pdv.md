---
title: PDV notes on Vue Design Practices
permalink: /pdv/
sitemap: false
---

***

## 9/10/2024

* Pablo David Garuso [Vue.js 3 Design Patterns and Best Practices: Develop scalable and robust applications with Vite, Pinia, and Vue Router](https://www.amazon.com/Vue-js-Design-Patterns-Best-Practices/dp/1803238070), published May 2023.
* pdv = Pablo David Vue book.
* Note down Hello World example to see how Options API syntax and Composition API syntax are different. Both have export(). But Options API goes with export(...data) whereas Composition does import i think.

***

# PDV Chapter 1: The Vue 3 Framework
## 1.1 Introduction

## 1.2 The Progressive Framework
* Difference between **library** and **framework**
* Examples of React/Next.js and Vue/Nuxt
* Concept of **reactivity**

## 1.3 Using Vue in your web application
* Introducing the concept of **SFC** (Single File Components)
### 1.3.1 The Bundler Way, a Better Way
* Official Vite3 bundler, addressed more in Chapter 3.

## 1.4 Understanding SFC (Single File Components)
* In depth discussion in Chapter 4 on UI Composition with Components

## 1.5 Different stroks: difference between Options and Composition APIs
### 1.5.1 Introduction
* data, methods, components, computed, props/emits, lifecycle hooks, mixins

### 1.5.2 Options API
* Hello world example
```html
<script>
export default {
  data() {
    return {_hello: "Hello World" }
  }
}
</script>
```

***

### 1.5.3 Composition API
* Hello world example
```html
<script>
import {ref} from "vue"
export default {
  setup() {
    const _hello = ref("Hello World")
    return {_hello}
  }
}
</script>
```

***

* Composition is a bit verbose compared to Options API. Here is a more concise version using `script setup`
```html
<script setup>
  import {ref} from "vue"
  const _hello = ref("Hello World")
</script>
```

***

## 1.6 Exploring built-in directives in Vue 3
* v-bind **`<img v-bind:src="my_profile_pic">`**
  * abbreviated `":"` so abbreviated version is  **`<img :src="my_profile_pic">`**
* v-show
* v-if, v-else, v-else-if
* v-for (aka `:key`)
* v-model
* v-on: e.g., **`<button v-on:click="printPage()">Print</button>`**
  * abbreviation `@` so abbreviated version looks like this: **`<button @click="printPage()">Print</button>`**

***

## 1.7 Built-in Components
* Vue also provides several built-in components that can be used without *explicit import* at the top of a SFC vue file.
* See complete documentation on [built-ins here](https://vuejs.org/api/built-in-components.html).

### 1.7.1 Transition and Transition Group
### 1.7.2 KeepAlive
### 1.7.3 Teleport
### 1.7.4 Suspense
### 1.7.5 Component-is

***

## 1.8 Code conventions used in this book
### 1.8.1 Variables and props
### 1.8.2 Constants
### 1.8.3 Classes and component names
### 1.8.4 Functions, methods, events, and filenames
### 1.8.5 Instances

***

# Chapter 2: Software Design Principles and Patterns
## 2.1 Introduction
* **Principles:** Separation of concerns, Composition over inheritance, Single responsbility, Encapsulation, KIC - keep it clean, DRY - don't repeat yourself, KISS - keep it simple stupid, Code for the next
* **Patterns:** Singleton, Dependency injectio, Observer, Command, Proxy, Decorator, Facade, Callbacks, Promises

## 2.2 What are the principles of software design?

## 2.3 List of design principles

### 2.3.1 Separation of concerns
### 2.3.2 Composition over inheritance
### 2.3.3 Single responsibilty principle
### 2.3.4 Encapsulation
### 2.3.5 KIC - keep it clean
### 2.3.7 DRY - don't repeat yourself
### 2.3.8 KISS - keep it simple and short
### 2.3.9 Code for the next

## 2.4 What is a software design pattern?

## 2.5 A Quick Reference List of Patterns
### 2.5.1 The singleton pattern
### 2.5.2 The dependency injection pattern
* This pattern simply states that the dependencies for a class or function are provided as input.
* For example, as parameters, properties, or other types of implementations.
* This simple statment opens a very wide range of possibilities.

#### 2.5.2.1 First example of DepInj
* Let's take, for example, a class that works with the browser's **Indexed DB API** through an abstraction class.
	* We will learn more about the IndexedDB API in *Chapter 7: Data Flow Mgt*.
	* For now, let's concentrate on the dependency part.
	* Consider that the **dbManager.js** file xposes an object that handles the operations with the database.
	* The **projects** object deals with CRUD operations for the projects table (or projects table).
	*Without using dependency injection, you will have something like this:
```javascript
import dbManager from "dbManager"
const projects = {
  getAllProjects() {
    return dbManager.getAll("projects")
  }
}
export default projects;
```
* The preceding code shows a 'normal' approahc, where we import the dependencies at the beginning of the file, then use them in our code.
* In contrast, let's see the **dependency ihjection** approach**:

```javascript
const projects = {
  getAllProjects( dbManager ){
    return dbManager.getAll("projects")
  }
}
export default projects;
```
* the main difference between the two approahces above is the DepInj approach means that **dbManager** is now passed as **a parameter to the function**.
* That's what we call an injection.
* This opens up many new ways to manage dependencies.
* Also, DepInj pushes the hardcoding of dependencies up the implementation tree.
* This makes the class signficantly more reusable.
#### 2.5.2.2 Another way of doing DepInj
* We could also assign it to a property for the object's internal use.
* For example, if the **projects.js** file was implemented using the property approach it might look like

```javascript
const projects = {
  dbManager,
  getAllProjects() {
    return this.dbManager.getAll( "projects" ) 
  }
}

export default projects;
```
* In this case, the invoker of the objct (a singleton, by the way), neeeds to be aware of the property *and* assign it before calling on any of its functions.
* For example, this approach is **NOT recommended**:

```javascript

import projects from "projects.js"
import dbManager from "dbManager.js"

projects.dbManager = dbManager;
projects.getAllProjects();

```

* This approach is **NOT recommended** b/c it clearly breaks the principle of encapsulation; we are directly assigning a property for the object.
* Also, it doesn't feel like clean code even if it validates.
* So what is the better approach? It depends on the implmentation.
	* In a class, it is convenient to require the dependencies in the constructor (and if not found, throw an Error).
	* IN a plain JSON object, it is convenient to provide a function to set the dependency explicitly and let the object decide how to use internally.
* This Last approach is recommended for passing a dependency **after** the instantiation of an object; when the dependencty at the time of implementation. 
* Example

```javascript
class Projects {
  constructor ( dbManager= null )  {
    if(
```

## 9/14/2024

### 2.5.3 The factory pattern
### 2.5.4 The observer pattern
### 2.5.5 The command pattern
### 2.5.6 The proxy pattern
### 2.5.7 The decorator pattern
### 2.5.8 The facade pattern
### 2.5.9 The callback pattern
### 2.5.10 The promise pattern

***

# Chapter 3: Setting up a working project
## 3.1 Introduction
## 3.x The To Do app

***

# Chapter 4: UI Composition with Components
## 4.1 Introduction
## 4.2 Technical requirements
## 4.3 Page composition with components
### 4.3.1 Step 1
### 4.3.2 Step 2
### 4.3.3 Step 3
### 4.3.4 Step 4

***

## 4.4 Components in depth
### 4.4.1 Local and global components
### 4.4.2 Static, asynchronous, and dynamic imports
### 4.4.3 Props, events, and the v-model directive
### 4.4.4 Custom input controllers
### 4.4.5 Dependency injection with 'Provide' and 'Inject'

***

## 4.5 Special components
### 4.5.1 Slots, slots, slots
### 4.5.2 Composables and mixins
### 4.5.3 Dynamic component with 'component:is'

***

## 4.6 A real-world example - a modals plugin
### 4.6.1 Setting up our dev environment
### 4.6.2 The design
### 4.6.3 The implementation

***

## 4.7 Implementing our new To-Do application
## 4.8 A small critique of our to-do app

***

Chapter 5: SPA - Single Page Applications
