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
* Many developers--myself included--generally prefer not to add type annotations on variables where those annotations wouldn't change anything. p. 46
* Having to manually type out annotations can be cumbersome. Esp. when types change; Goldberg will illustrate some examples of this later in the book. 

### Type Shapes p. 46
* TS does more than check that the values assigned to variables match their original types. 
* TS also knows what **member properties** should exist on objects.
* If one attempts to access a property of some variable, TS will make sure that this property is known to exist as part of that varible's type.
* Went through Queen Latifah example on p. 47 and verified that tsc reports compile-time error when one tries to call the push() property/method on a string. 
* Went through Cher example on p. 47 and verified it works and fails as expected.
* The point is, TS's understanding of object shapes allows TS to report issues with both the *usage* and *assignability* of objeects. See more in Chapter 4 on Objects.

### Modules p. 47-49
* Mostly straightforward

## Chapter 3: Unions and Literals p. 51
* *Unions* expand a value's allowed type to **two or more possible types**
* *Narrowing* reduces a value's allowed type to ** *not* be one ore more possible types**.

### Union Types p. 51

* Consider this code example:

```javascript
let mathematician = Math.random() > 0.5
	? undefined
	: "Mark Goldberg";
```

* What type is the `mathematician` object? Answer: it's neither only *undefined* or *string*--even though `mathematician` could be either of those types. 
* `mathematician` can be *either* undefined or string. 
* This kind of *either-or* type is called a **union**. 
* TS represents union types using the `|` pipe operator in between the potential types aka in between the **constituents**.
* The *mathematician* type is thought of as **type:** `string | undefined`. Try hovering over that expression in a TS-aware code editor and should see a tooltip that looks like Fig 3-1 on p. 52. 

#### Declaring Union Types p. 52
* Union types are an example of a situation when it might be useful to give an *explicit* type annotation for a variable even though that variable has an initial value.
* Consider this new example:

```typescript
let thinker: string | null = null;
if (Math.random() > 0.5) {
	thinker = "Sussane Langer"; // ok
}

```

* In the above example, the **thinker** object starts off with a *null* value but is known to potentially contain a *string* value instead.
* Giving **thinker** an *explicit* `string | null` type annotation means TS will allow that variable to be assigned values of type *string*.
* Union type declarations can be placed anywhere one might declare a type using a type annotation

#### Union Properties p. 53
* When a value is known to be a union type, TS will only allow devs to access member properties that exist in *all possible types* in that union.
* TS will produce a type-checking error if one tries to access a type that doesn't exist on all possible associated types.
* Example:

```typescript
let physicist = Mathh.random() > 0.5
	? "Marie Curie"
	: 84;


// OK-- both "Marie Curie" and "84" can be converted toString
physicist.toString();

// Error here because
// 'toUpperCase()' property only exists for type 'string'
// but **not** for type 'number'
physicist.toString();

// Error here because
// 'toFixed() property only exists for type 'number'
// but **not** for type 'string'
physicist.toFixed();
```

* Restricting access to properties that don't exist on all union types is a safety feature. i.e., If an object is not of a type that is *definitively* contains property, TS will believe it unsafe to try that property. After all, the property might not exist.

### Narrowing p. 54
* Narrowing is when TS infers from your code that a value is of a more specific type than what is defined, declared, or previously inferred as.
* Once TS knows that a value's type is more narrow than previously known, it will allow you to treat the value like that more specific type.
* A logical check that can be used to narrow types is called a *type guard*. 

#### Assignment Narrowing p. 54

#### Conditional Checks p. 55

#### Typeof Checks p. 56

### Literal Types p. 57
* Now that we've discussed union types and narrowing types, let's introduce *literal types* which are sort of 'narrowing' primitive types.
* Example:

```typescript
const philosopher = "Hypatia";
```

* What type is the *philosopher* object?
	* Initial answer is that it is a  *string* type.
* But! `philosopher` is not just any old string. It's specifically the value *Hypatia*. Therefore, the *philosopher* variable's type is technically the more specific *Hypatia*.
* This is the concept fo the *literal* type. 
* The type of a value that is known to be a specific value of a primitive, rather than any of those primitive's values at all.
* The primitive type **string** represents the set of all possible strings that could ever exist; the literal type *Hyaptia* represents just that one string.
* If you declare a variable as *const* and directly assign a literal value, TS will infer that the variable to be that literal value as a type.
* When you are in IDE and hover over a *const* variable with an initial literal value, it will show the variable's type as that literal instead of the more general primitive.
* See Figures 3-2 and Figure 3-3 on p. 57


## 8/10/2024
* One can think of each primitive type as a *union of every possible matching **literal** value*.
	* ie., a primitive type is the set of all possible literal values of that type.
* Other than the *boolean*, *null*, and *undefined* types, all other primitives such as number and string have an infinite number of literal types. 
* The common types one will find in typical TS code are:
	* **boolean**: *true* \| *false*
	* **null** and **undefined**: both hae just one literal value, themselves
	* **number**: (0, 1, 2, ...) or (0.1, 0.2, ...) or similar ...
	* **string**
* Union type annotations can mix and match between literals and primitives. 
* e.g., the representation of a lifespan, for example, might be represented by any number or *one* of a couple known edge cases. Examples:

```typescript

let lifespan: number | "ongoing" | "uncertain";

lifespan = 89; // ok
lifespan = "ongoing"; // ok

lifespan = true; // results in error b/c 'boolean' was not in type annotation

```

#### Literal Assignability p. 58
* We have seen how different primitive types such as **number** and **string** are not assignable to eaach other. 
* Similarly, different literal types within the same primitive types (e.g., `0` and `1`) are **not assignable to each other**.
* Consider this example p. 58-59

```typescript
//Example 1
let specificallyAda: "Ada";
specificallyAda = "Ada"; // ok
specificallyAda = "Byron"; // Error: one cannot assign to type 'Ada'

// Example 2
let someString = ""; // Type: string

specificallyAda = someString;
// another error b/c type 'string' cannot be assigned to 
// type 'Ada'
```

* Literal types *are* allowed to be assigned to their corresponding primitive types.
* Any specific literal string is *still* a **string**.

### Strict Null Checking p. 59
* The Billion Dollar Mistake by Tony Hoare (quoted in 2009) on p. 60.
* There are many type systems in CS that allow null values to be used in places that require a different type. 
* In languages *without* strict null checking, code like this would be allowed:

```javascript
const firstName: string = null;
```

* E.g., C++ or Java would allow the above. Continue on p. 60


***


## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.

`<script>`
