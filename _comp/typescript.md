---
title: TypeScript Notes
permalink: /typescript/
sitemap: false
---

# Learning TypeScript
* Josh Goldberg
* O'Reilly Media, 2022
## 8/02/2024
### Conceptual overview of various chapters to follow.
* Chapters in *Learing TypeScript* organized into 3 main sections with one extra section:
	* **Part I: Concepts**
	* **Part II: Features**
	* **Part III: Usage**
	* **Part IV: Extra Credit**
* **Section I: Concepts**
	1. Chapter 2: Type System overview
	1. Chapter 3: **Unions** to expand type possibilities and **Narrowing** to reduce type possibilities. Also *literal types* are a more advanced, specific version of *primitive types* like strings, arrays, etc.
	1. Chapter 4: **Objects**
* **Section II: Features**
	1. Chapter 5: Functions
	1. Chapter 5: Arrays
	1. Chapter 5: Interfaces
	1. Chapter 8: Classes
	1. Chapter 9: Type Modifiers
	1. Chapter 10: Generics
* **Section III: Usage**
	1. Chapter 11: Declaration Files
	1. Chapter 12: Using IDE Features
	1. Chapter 13: Configuration Options
* **Section IV: Extra Credit**
	1. Chapter 14: Syntax Extensions
	1. Chapter 15: Type Operations


## 8/04/2024
### Chapter 2: The Type System p. 37
* Syntax Errors vs Type Errors
* Assignability p. 42
	* It's ok to change the value as long as it is the same type within a strongly typed system
	* However, if one tries to reassign from  `str1 = 'Adam'` to `str1 = [1,2,3]`, TypeScript will throw a type error.

### Type Annotations p. 44
* Concept of the *evolving any*
* Unnecessary Type Annotations. The following **: string** type annotation is redundant because TS could already infer that `firstName` is of type *string*:

```javascript
let firstName: string = "Tina";
// Does not change the type system
```

* If one does add a *type annotation* to a variable with an initial type, TS will check wthat it matches the type of the variable's value. 
* The following `firstName` is declared to be of type *string* but its initializer is the *number* `42` which TS notes is an incompatibility:

```javascript
let firstName: string = 42;
// Error: Type 'number' is not assignable to type 'string'.
```

## 8/06/2024
### Trying to get vim to automatically report TS errors
* Let's test error-checking using lsp on champ24. Hm. things are compiling and running, but auto error checking is not happening. weird.
* Did all testing on champ24.
* Error messages etc are showing up properly in `proj-2/_df9/` for c files. But in `proj-3`, although tsc compiles and reports proper compile-time errors. But errors not showing up despite properly invoking `LspInstallServer` and yes.

### More on Type Annotations
* Many developers--myself included-- generally prfer not to add type annotations on variables where those annotations wouldn't change anything. p. 46
* Having to manually type out annotations can be cumbersome. Esp. when types change; Goldberg will illustrate some examples of this later in the book. 

### Type Shapes p. 46



***


## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.

`<script>`
