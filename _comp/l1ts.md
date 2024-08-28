---
title: TypeScript Notes
permalink: /typescript/
sitemap: false
---

# Learning TypeScript
* Josh Goldberg
* O'Reilly Media, 2022
* LTS = Learning TypeScript by Josh Goldberg

## 8/02/2024
### Conceptual overview of various chapters to follow.
* Chapters in *Learning TypeScript* organized into 3 main sections with one extra section:
	* **Part I: Concepts**
	* **Part II: Features**
	* **Part III: Usage**
	* **Part IV: Extra Credit**
* **Part I: Concepts**
	1. Chapter 2: Type System overview
	1. Chapter 3: **Unions** to expand type possibilities and **Narrowing** to reduce type possibilities. Also *literal types* are a more advanced, specific version of *primitive types* like strings, arrays, etc.
	1. Chapter 4: **Objects**
* **Part II: Features**
	1. Chapter 5: Functions
	1. Chapter 6: Arrays
	1. Chapter 7: Interfaces
	1. Chapter 8: Classes
	1. Chapter 9: Type Modifiers
	1. Chapter 10: Generics
* **Part III: Usage**
	1. Chapter 11: Declaration Files
	1. Chapter 12: Using IDE Features
	1. Chapter 13: Configuration Options
* **Part IV: Extra Credit**
	1. Chapter 14: Syntax Extensions
	1. Chapter 15: Type Operations

***
## 8/04/2024

# Part I: Concepts
# Chapter 2: The Type System p. 37
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

***
# Chapter 3: Unions and Literals p. 51
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
* For more on configuring the TypeScript compiler, see Chapter 13 'Configuration Options', which include the option **strictNullCheck**. By default, strictNullCheck is on. When it is turned off, every variable in your code adds `... | null | undefined` as additional types. 
* When *strictNullCheck* is turned off, the following code is considered totally type safe--even though it really isn't. That's why you should keep it on!

```typescript
let nameMaybe = Math.random() > 0.5
	? "Tony Hoare"
	: undefined;
```
* When strictNullCheck is turned off, the command `nameMaybe.toLowerCase();` gets a *Potential runtime error: cannot read property 'toLowercase' of undefined.*
* When strictNullCheck is turned on, the TS sees the potential crash at compile time. So `nameMaybe.toLowerCase();` reports *Error: Object is possibly 'undefined'.*

## 8/11/2024
### Truthiness Narrowing p. 61
* Review of concept of *truthiness* for values that would evaluate to `true` in a Boolean context.
* TS can narrow a variable's type from a truthiness check if only *some* of its potential values may be truthy.

```typescript
let geneticist = Math.random() > 0.5
	? "Barbara McClintock"
	: undefined;

if (geneticist) {
	geneticist.toUpperCase(); // Ok b/c it's a string
}

// But!!! the below gets an 'Error: Object is possibly undefined'
geneticist.toUpperCase();
```

* Logical operators that perform truthiness checks work also, specifically **&&** and **?.** such as:

```typescript
geneticist && geneticist.toUpperCase(); // ok b/c string *or* undefined
geneticist?.toUpperCase(); // ok b/c string *or* undefined
```

* However, truthiness checking does not go the other way; if all we know about a value is that it is `string | undefined` and falsy, that does not tell us whether it is an empty string or *undefined*.

### Variable Without Initial Values p. 62
* Variables declared without an initial value default to *undefined* in JS. 
* TS is smart enough to understand that the variable is *undefined* until a value is defined. TS will report a specialized error message if you then try to use that variable (e.g., by trying to access its properties) before assigning a vlaue. 

```typescript
let mathematician: string;
mathematician?.length; // Error: variable 'mathematician' is used before it is assigned a value.

mathematician = "Euler";
mathematician.length; // OK
```

* Note that this reporting does not apply if the variable's type includes *undefined*. Adding `| undefined` to a variable's type indicates to TS that it doesn't need to be defined before use b/c `undefined` is a valid type for its value.

### Type Aliases p. 63
* Most union types one sees in code will usually only have two or three constituents.
* However, sometimes we see longer union types that are a pain to type out repeatedly.
* Each of these examples has four possible types:

```typescript
let rawDataFirst: boolean | number | string | null | undefined;
let rawDataSecond: boolean | number | string | null | undefined;
let rawDataThird: boolean | number | string | null | undefined;
```

* The concept of **type aliases** makes it easier to assign names to reused types. So the above code could be written this way using type aliases:


```typescript
type RawDataAlias = boolean | number | string | null | undefined;

let rawDataFirst: RawDataAlias;
let rawDataSecond: RawDataAlias;
let rawDataThird: RawDataAlias;
```

* **Note: Type Aliases are *not* javascript.** Both type aliases and type annotations are *not* compiled to output JS; they exist *purely* in the TS type system.
* So be careful you don't try to access type aliases or type annotations during runtime. See p. 64.


### Combining Type Aliases p. 64-65
* Type aliases may reference other type aliases. 

```typescript
type Id = number | string;

// Below is equivalent to: number | string | undefined | null
type IdMaybe = Id | undefined | null;
```

* Type aliases don't have to be declared in order of usage. 
* The previous code snippet could be rewritten to have *IdMaybe* come before *Id*

```typescript
type IdMaybe = Id | undefined | null; // ok even though declared first
type Id = number | string;
```

***

# Chapter 4: Objects p. 67
* This chapter examines how TS has a sophisticated way of handling very complex object shapes

### Object Types
* When one creates an object literal with the {...} syntax, TS will consider it to be a new *object type* (aka a new **type shape**) based on its properties.
* That object type will have the same property names and primitive types as the object's values.
* Accessing properties of the value can be done using either the `value.member` or equivalent `value['member']` syntax.
* TS understands that the **poet** varible's type is that of an object with two properties:
	1. **born** of type *number*
	1. **name** of type *string*
* Accessing these members would be allowed, but attempting to access any other member name would cause a type error for that name not existing:

```typescript
const poet = {
	born: 1935,
	name: "Mary Oliver",
};

poet['born']; // type: number
poet.name; // type: string

// Below reports an error
// Error: Property 'died' does not exist on
// type '{ name: string; start: number; }'
poet.died;
```

* Object types are a *core concept* for how TS understands JS code. 
* *Every value* other than `null` or `undefined` has a set of members in tis backing type shape; therefore, TS must understand the object type for every value in order to type check it.

### Declaring Object Types p. 68
* Inferring types directly from existing objects is nice and all--but we also want to be able to explicitly declare the type of an object.
* Thus, it's nice to declare an *object shape* separately from the *object* that satisfies it.
* Object types may be described using a syntax that that looks similar to object literals but with *types* instead of *values* for fields. It's the same syntax that TS shows in error messages about type assignability.

```typescript
let poetLater: {
	born: number;
	name: string; 
};

// this is ok...
poetLater = {
	born: 1935,
	name: "Mary Oliver",
};

// this reports an error
// Error: Type 'string' is not assignable to 
// type '{ name: string; start: number; }'
poetLater = "Sappho";
```

### Aliased Object Types p. 69
* Constantly writing out object types like `{ name: string; start: number; }` gets repetitive and tiresome. It's more common to use *type aliases* to assign a *name* to each type shape. 
* The previous code can be written like this:


```typescript

type Poet = {
	born: number;
	name: string;
};

let poetLater: Poet;

// below is OK

poetLater = {
	born: 1935,
	name: "Sara Teasdale",
};

// Below is an error
// Error: Type 'string' is not assignable to 'Poet'.
poetLater = "Emily Dickinson";

```

* Note, most TS code prefers to use **interfaces** instead of aliased object types. Interfaces are covered in LTS Chpter 7. But most of the material here in Chapter 4 using object types applies to interfaces as well.

### Structural Typing p. 69
* TS's typing system is *structurally typed*, *aka* any value that happens to satisfy a type is allowed to be used as a value of that type.
* i.e., when one declares that a parameter or variable is of a particular object type, one is telling TS that whatever objects one uses, they *need* to have those properties.
* The following `WithFirstName` and `WithLastName` aliased object types both only declare a single member of type *string*. p. 70.
 
```typescript
type WithFirstName = {
	firstName: string;
};

type WithLastName = {
	lastName: string;
};

const hasBoth = {
	firstName: "Lucille",
	lastName: "Clifton",
};

// OK b/c 'hasBoth' contains a firstName property of type *string*
let withFirstName: WithFirstName = hasBoth;

// OK b/c 'hasBoth' contains a lastName property of type *string*
let withLastName: WithLastName = hasBoth;

```

* The *hasBoth* variable just so happens to have both firstName and lastName properties, so it can be provided to variables that are declared as *either* type **WithFirstName** *or* type **WithLastName**.
* **Note:** Structural typing is *not* the same as **duck typing**, whereby *If it looks like a duck, walks like a duck, and quacks like a duck, it's probably a duck*.
	1. Structural typing is when there is a *static* system checking the type--in TS's case, the type checker.
	1. Duck Typing is when *nothing* checks object types until they are used at runtime.
* In summary, JS is *duck typed* whereas TypeScript is *structurally typed*.


### Usage Checking
* When providing a value to a location annotated with an object type, TS will check that the value is assignable to that object type.
* To start, the value must have the object type's required properties.
* If any member required on the object type is missing in the object, TS will issue a type error.
* The following **FirstAndLastNames** aliased object type requires that both the *first* and *last* properties exist.
* An object containing both of those is allowed to be used in a variable declared to be of type **FirstAndLastNames**, but an object without them is not:

```typescript
type FirstAndLastNames = {
	first: string;
	last: string;
};


// OK
const hasBoth: FirstAndLastNames = {
	first: "Sarojini",
	last: "Naidu", 
};


const hasOnlyOne: FirstAndLastNames = {
	first: "Sappho"
};
// Property 'last' is missing in type '{ first: string; }'
// but required in type 'FirstAndLastNames'.
```

* Mismatched types between the two are not allowed either.
* Object types specify both the names of required properties and the types those properties are expected to be .
* If an object's property doesn't match, TS will report a type error.
* The following **TimeRange** type expects the *start* member to be of type **Date**. 
* The *hasStartString* object is causing a type error because its *start* is type *string* instead.

```typescript
type TimeRange = {
	start: Date;
};

const hasStartDate: TimeRange = {
	start: "1879-02-13",
	// error: type 'string' is not assignable to type 'Date'.
};
```

### Excess Property Checking p. 72

* TS will report a type error if a variable is declared with an object type and its initial value has *only* fields than its type describes.
* Therefore, declaring a variable to be of an object type is a way of getting the type checker to make sure it has *only* the expected fields on that type. 
* This makes sure that *a type has **no** extra fields*.

```typescript

type Poet = {
	born: number;
	name: string;
}

// below is ok
// because all fields match what's expected in Poet

const poetMatch: Poet = {
	born: 1928,
	name: "Maya Angelou",
};

// Below throws an error
// b/c there is an extra property called 'activity'

const extraProperty: Poet = {
	born: 1935,
	name: "Mary Oliver",
	activity: "walking",
};


// Error: Type '{ activity: string; born: number; name: string; }'
// is not assignable to type 'Poet'.
//   Object literal may only specify known properties,
//   and 'activity' does not exist in type 'Poet'.
```

* **Note:** excess property checks (JH what i would call 'extra property checks') *only* trigger for object literals being created in locations that are declared to be an object type.
* Providing an existing object literal *bypasses* extra property checs.

```typescript
const existingObj = {
	born: 1935,
	name: "Mary Oliver",
	activity: "walking",
};

const extraPropertyButOk: Poet = existingObject;
// will *not* throw an error b/c the *initial value*
// matched the correct number of properties (2)
// expected for a Poet object
```

### Nested Object Types p. 73
* Just as JS objects can be nested as members within other objects, TS's object types must also be able to represent nested object types in the type system.
* The syntax to do this is the same as before--but with a `{...}` object type instead of just a primitive name.

```typescript
type Poem = {

	author: {
		firstName: string;
		lastName: string;
	};

	name: string;
};


// below is ok

const poemMatch: Poem = {
	
	author: {
		firstName: "Sylvia";
		lastName: "Plath";
	};

	name: "Lady Lazarus",
};

const poemMismatch: Poem = {
	author: {
		name: "Sylvia Plath",
	},

	// Reports error b/c there is no fName or lName 


	name: "Tulips",

}
```

* Object *poemMismatch* is not assignable b/c its *author* property includes *name* instead of *firstName* and *lastName* as expected by type **Poem**.
* Alternate method of defining the **Poem** object, by extracting an **Author** aliased object type.
	* This way, TS will provide a more informative error message referring to *Author* rather than the more generic error message `{ firstName: string; lastName: string; }`

```typescript
type Author = {
	firstName: string;
	lastName: string;
};

type Poem = {
	author: Author;
	name: string;
};

const poemMismatch: Poem = {
	author: {
		name: "Sylvia Plath",
	},

// Error: Type '{ name: string; }' is not assignable 
// to type 'Author'.
// Object literal may only specify known properties,
// and 'name' does not exist in type 'Author'.
```

* It's generally a good idea to move nested objects into their own type names like this b/c it makes for more readable code and more readable error messages.


### Optional Properties p. 75
* Object type properties don't all have to be required in the object.
* You can include a `?` before the `:` in a type property's type annotation to indicate that this is an *optional property* of that object.
* This **Book** type requires only a *pages* property and optionally allows an *author*.

```typescript
type Book = {
	author?: string;
	pages: number;
};

//OK
const ok: Book = {
	author: "Rita Dove",
	pages: 80,
};

const missing: Book = {
	author: "Rita Dove",
};

// Error: Property 'pages' is missing in type
// '{ author: string; }' but required in type 'Book'.
```

* Keep in mind there is a difference between optional properties and properties whose type happens to include *undefined* in a type union.
	* A property declared as optional with `?` is allowed to not exist.
	* A property declared as *required* and `| undefined` must exist, even if the value is *undefined*.
* The *editor* property in the following `Writers` type may be skipped in declaring variables bcause it has a `?` in its declaration.

```typescript

type Writers = {
	author: string | undefined;
	editor?: string;
};

// OK: author is provided as undefined
const hasRequired: Writers = {
	author: undefined,
};

//Error below
const missingRequired: Writers = {};

// Error: Property 'author' is missing in type 
// '{}' but required in type 'Writers'.
```

* Chapter 7 covers other properties (Interfaces) while Chapter 13 Configuration Options describes strictness options.

## 8/14/2024
### Unions of Objects Types p. 76
* It is reasonable in TS code to want to be able to describe a type that can be *two or more* different object types that have slightly different properties.
* Furthermore, your code might want to be able to type narrow between those object types based on the value of a property.

#### Inferred Object-Type Unions p. 76
* If a variable is given an initial value that could be one of multiple object types, TS will infer the variable's type to be a **union** of the various possible option types.
* That union type will have a *constituent* for each of the possible object shapes.
* Each of the possible properties on the type will be present in each of those constitutents. *However*, there will be `?` optional types on any type that does not have any initial value for them.

```typescript
const poem = Math.random() > 0.5
	? { name: "The Double Image", pages: 7 }
	: { name: "Her Kind", rhymes: true };

	// Type:
	// {
	// name: string;
	// pages: number;
	// rhymes?: undefined;
	// }
	// 	|
	// {
	// 	name: string;
	// 	pages?: undefined;
	// 	rhymes: boolean;
	// }
	// 	

poem.name;  // outputs string
poem.pages;  // number | undefined
poem.rhymes;  // booleans | undefined
```

* In the above code, the *poem* value always has a *name* property (type: *string*), but the *poem* may or may not have *pages* or *rhymes* properties.

#### Explicit Object-Type Unions p. 77
* Alternately, one can be *explicit* about one's object types by being explicit with declaring a union of object types.
* Doing so requires writing a bunch more code but comes with the benefit of having more control.
* See explicit version of **poem** code here:

```typescript
type PoemWithPages = {
	name: string;
	pages: number;
};

type PoemWithRhymes = {
	name: string;
	rhymes: boolean;
};

type Poem = PoemWithPages | PoemWithRhymes;

const poem: Poem = Math.random() > -.5
	? { name: "The Double Image", pages: 7 }
	: { name: "Her Kind", rhymes: true };

poem.name; // ok

// Error for below
// Property 'pages' does not exist on type 'Poem'.
// Property'pages'doesnotexistontype'PoemWithRhymes'.
poem.pages;


// Error for below
// Property 'rhymes' does not exist on type 'Poem'.
// Property'rhymes'doesnotexistontype'PoemWithPages'.
poem.rhymes;
```

* Restricting access to potentially nonexistent members of objects can be a good thing for code safety.
* If a value might be one of multiple types, properties that don't exist on all of those types aren't guaranteed to exist on the object.


#### Narrowing Object Type  p. 78-79
* If the type checker sees that an area of code can only be run if a union typed value contains a certain property, it will narrow the value's type to only the constituents that contain that property.
* In other words, TS's type narrowing will apply to objects if you check their shape in code.
* Continuing the explicitly typed **poem** example from above, check whether *pages* in **poem** acts as a type guard for TS to indicate that it is a **PoemWithPages**.

```typescript
if ("pages" in poem) {
	poem.pages; // OK: poem is narrowed to PoemWithPages
} else {
	poem.rhymes; // OK: poem is narrowed to PoemWithRhymes
}
```

* Note that TypeScript won't allow truthiness existence checks like `if(poem.pages) { /*...*/ }`.
* Attempting to access a property of an object that *might not exist* is a **type error**, even if used in a way that seems to behave like a type guard:

```
Error: Property 'pages' does not exist on type 'PoemWithPages | PoemWithRhymes'. 
Property 'pages' does not exist on type 'PoemWithRhymes'.
```

#### Discriminated Unions p. 78-79
* Another popular form of union typed objects in JS / TS is to have a property on the object indicate what shape the object is.
* This kind of type shape is called a **discriminated union**.
	* The associated property whose value indicates the object's type is called a *discriminant*.
* TS is able to perform type narrowing for code that type guards on *discriminant* properties.
* Example p. 80: 

```typescript
type PoemWithPages = {
	name: string;
	pages: number;
	type: 'pages';
};

type PoemWithRhymes = {
	name: string;
	rhymes: boolean;
	type: 'rhymes';
};
type Poem = PoemWithPages | PoemWithPages;

const poem: Poem = Math.random() > 0.5
	? { name: "The Double Image", pages: 7, type: "pages" }
	: { name: "Her Kind", rhymes: true, type: "rhymes" };

if (poem.type == "pages") {
	console.log(`It's got pages: ${poem.pages}`); // Ok
} else {
	console.log(`It rhymes: ${poem.rhymes}`);
}

poem.types; // Type: 'pages' | 'rhymes'

poem.pages:
//   ~~~~~
// Error: Property 'pages' does not exist on type 'Poem'.
// Property 'pages' does not exist on type 'PoemWithRhymes'.
```

* *Discriminated unions are my **favorite** feature in TS*. B/c they beautifully combine a common elegant JS pattern with TS' type narrowing.
* *Chapter 10: Generics* willshow more around discriminated unions for generic data operations.

### Intersection Types p. 81
* TypeScript's `|` union types represent the type of a value that coukld be one of two or more different types.
* In contrast, TS can also represent an *intersection* type using **&**.
* Intersection types are typically used with aliaased object types to creat a new type that combines multiple existing object types.
* Example:

```typescript
type Artwork = {
	genre: string;
	name: string;
};

type Writing = {
	page: number;
	name: string;
};

type Written Art = Artwork & Writing;
// Equivalent to:
// {
//   genre:string;
//   name:string; 
//   pages:number;
// }
```

* Intersection types can be combined with union types, which is sometimes useful to describe discriminated unions in one type. 
* Consider the following example on p. 81-82. The **ShortPoem** type always has an *author* property; the type is alos a discriminated union on a *type* property.

```typescript
/* --------------------------------------------------------------------- */
type ShortPoem = { author: string } & (
	| { kigo: string; type: "haiku"; }
	| { meter: number; type: "villanelle"; }
);

/* --------------------------------------------------------------------- */
const morningGlory: ShortPoem = {
	author: "Fukuda Chiyo-ni",
	kigo: "Morning Glory",
	type: "haiku",
};
// above variable declaration is OK

/* --------------------------------------------------------------------- */
const oneArt: ShortPoem = {
	author: "Elizabeth Bishop",
	type: "villanelle",
};

// Above 'oneArt' declaration generates error
// Error: Type '{ author: string; type: "villanelle"; }'
// is not assignable to type 'ShortPoem'.
//   Type '{ author: string; type: "villanelle"; }' is not assignable to 
//   type '{ author: string; } & { meter: number; type: "villanelle"; }'.
//       Property 'meter' is missing type '{ author: string; type: "villanelle"; }'
//       but required in type '{ meter: number; type: "villanelle"; }'.
/* --------------------------------------------------------------------- */
```
### Dangers of Intersection Types p. 83
* Intersection types are very useful. But it's very easy to use them in ways that confuse yourself, other programmers, or the TS compiler.
* When using intersection types, **please keep things as simple as possible**.
* Kinds of problems:
    1. Long assignability errors p. 83
    1. `never` p. 84

### Summary of Chapter 4 p. 84-85

***


# Part II Features p. 86

# Chapter 5: Functions p. 87
* This chapter describes how to annotate the input *parameters* and output *return values* for functions, similar to how Chapter 2 show how one can use type annotations to annotate values of variables.

### Function Parameters p. 87
* Consider the following `sing()` function that takes an input *song* parameters and logs it:

```typescript
function sing(song) {
	console.log( `Singing: ${song}!`);
}
```

* There's no information about what type *song* is; it could be a string, a number, a boolean, whatever.
* In this case, TS will consider *song* to be of type: **any**.
* As with variables, TS allows one to declare the type of function parameters using annotations. Here is the improved version with a required type:

```typescript
function sing(song: string) {
	console.log( `Singing: ${song}!`);
}
```
* Require Parameters p. 88
* Unlike JS, which allows functions to be called with any number of arguments, TS assumes that *all parameters declared on a function are **required**.*
* Providing the wrong number of input arguments will raise TS errors. See example p. 88: 

```typescript
function singTwo( first: string, second: string ) {
	console.log( `${first} / ${second}` );
}

// Logs: "Ball and Chain / undefined"
// Error: expected 2 arguments, but only got 1 input argument
singTwo("Ball and Chain");

// this is ok
// Logs: "I Will Survive / Higher Love"
singTwo("I Will Survive", "Higher Love");


// Logs: "Go Your Own Way / The Chain"
// Error: expected 2 arguments, but got 3 input argument
singTwo("Go Your Own Way", "The Chain", "Dreams");
```

* **Important Note: *Parameter* refers to a function's declaration of what it expects as input. *Argument* refers to the *value* provided to a parameter in when calling a function.**
* In the previous example, **first** and **second** are parameters. `I Will Survive` and `Higher Love` and other strings are arguments; the values passed in for required input 'slots' for a function.

***

## 8/17/2024

### Optional Parameters p. 89
* Recall that in JS, if a function parameter is not provicded, its argument value inside the function defaults to `undefined`. 
* Sometimes function parameters are not necessary to provide, and the intended use of the function is for that 'undefined' value. 
* We would not want TS to report type errors for failing to provide arguments to those optional parameers. 
* That is the purpose of **optional parameters**--this is similar to *optional object type properties*.
* Optional params don't need to be provided to function calls. Their types therefore always have a `| undefined` added as a union type by default.
* Example on p. 89-90:

```typescript

function announceSong( song: string, singer?: string ) {
	console.log( `Song: ${song}` );

	if (singer) {
		console.log( `Singer: ${singer}` );
	}
}

announceSong("Greensleeves"); // ok
announceSong("Greensleeves", undefined); // also ok
announceSong("Chandelier", "Sia"); // ok
```

* In the above example, the *singer* parameter for the **announceSong()** function is marked **optional**. 
	* The type is `string | undefined`, and the *singer* parameter does not need to be provided by callers of the funciton.
	* If *singer* argument is provided to announceSong(), it may be of type *string* or just *undefined*.
* Above optional parameters are always implicitly able to be *undefined*.
* In the above example, **singer** starts off as being of type `string | undefined` and then it is narrowed to just `string` by the **if statement**.
* Optional parameters are not thes ame as parameters that have union types that happen to include `| undefined`. 
* Parameters that are *not* marked as optional with a **`?`** must *always* be provided, even if the value is explicitly *undefined*.
* Example p. 90:

```typescript
function announceSongBy( song: string, singer: string | undefined) {
/* ... */
}

announceSongBy("Greensleeves");
//Error: Expected 2 arguments, got 1

announceSongBy("Greensleeves", undefined); // ok
announceSongBy("Chandelier", "Sia"); // ok
```

* Any optional parameters for a function must be the *last parameters in sequence*.
* **Placing an optional parameter before a required parameter triggers a TypeScript syntax error.

***
## 8/18/2024
### Default Parameters p. 90
* Optional parameters in JS may be given a default value with the `=` operator and a value in their declaration.
* TS's type inference works similarly for for **default function parameter** values, just as it does for initial variable values.
* If a parameter has a default value and does *not* have a type anotation, TS will infer that the parameter's type based on that default value.

### Rest Parameters p. 91
* Some functions in JS are made to be called with any number of arguments.
* The `...` spread operator may be placed in the position of the last parameter of a function declaration. 
	* This indicates that any **rest** arguments passed to the function starting at that parameter should all be stored in a single array.
* TS allows declaring the types of these rest parameters similarly to regular parameters.
* **Except** with a `[]` bracket syntax added at the end to indicate that it is an array of arguments.
* Example on p. 91-92:

```typescript
function singAllTheSongs( singer: string, ...songs: string[] ) {
	for (const song of songs) {
		console.log( `${song}, by ${singer}`);
	}
}

singAllTheSongs("Alicia Keys"); // ok
singAllTheSongs("Lady Gaga", "Bad Romance", "Telephone", "Poker Face"); // ok

// Error!
// Argument of type 'number' is not assignable
// to parameter of type 'string'.
singAllTheSongs("Ella Fitzgerald", 2000); 
```

* In the above example, the **singAllTheSongs()** function is allowed to take zero or more arguments of type *string*, but raises and error when a *number* like `2000` is input.

### Return Types p. 92
* TypeScript is smart--if it understands all the possible values returned by a function, TS will generally understand what *type* the function returns.
* Example on p. 92:

```typescript

// Type: (songs: string[]) ==> number

function singSongs( songs: string[] ) {
	for ( const song of songs) {
		console.log(`${song}`);
	}
	return songs.length;

}
```

* the function **singSongs()** is understood by TS to return a *number*.
* If a function contains multiple *return* statements that each have different values, TS will infer the return type to be a **union* of all the possible returned types.
* Example:

```typescript

function getSongAt( songs: string[], index: number ) {
	return index < songs.length
		? songs[index]
		: undefined;
}
```

* Above **getSongAt()** function would be inferred to return the union `string | undefined` because its two possible returned values are type *string* or *undefined*.

### Explicit Return Values p. 93
* As with variables, LTS recommends not bothering to explicitly declare return types of functions using annotations.
* However, there are a few cases where it can be helpful. See p. 93-94

### Function Types p. 94
* JavaScript allows us to pass functions around as values. This means we need a way to declare the type of a parameter or variable meant to hold a function.
* **Function type** syntax looks similar to an *arrow function*but using a *type* instead of a body.
* This **nothingInGivesString** variable has a type which describes a function with zero parameters and returns a *string* value:

```typescript
let nothingInGivesString: () => string;
```

* Next


```typescript
let inputAndOutput: ( songs: string[], count?: number ) => number;
```

* Function types are frequently used to describe **callback parameters** (aka *parameters meant to be called as functions*).
* Example on p. 94-95

```typescript
const songs = ["Juice", "Shake It Off", "What's Up"];

/* ------------------------------------- */

function runOnSongs( getSongAt: ( index: number ) => string ) {
	for ( let i = 0; i < songs.length; i += 1 ) {
		console.log( getSongAt(i) );
	}
}

function getSongAt( index: number ) {
	return `${ songs[index] }`;
}

runOnSongs(getSongAt); // ok

/* ------------------------------------- */

function logSong( song: string ) {
	return `${ song }`;
}

// Error: Argument of type '(song: string) => string' 
// is not assignable to parameter of type 
// '(index: number) => string'. 
// Types of parameters 'song' and 'index' are incompatible. 
// Type 'number' is not assignable to type 'string'.
runOnSongs(logSong);
           ^^^^^^^
```
* Consider the above code example. the **runOnSongs** snippet declares the type of its **getSongAt()** parameter to be a fucntion that accepts as input an *index: number* and returns as output a *string*.
* Passing a **getSongAt** matches that type, but *logSong* fails for taking in a *string* as its parameter instead of a *number*.
* The error message for **runOnSongs( *logSong()* )** is an example of an assignability error that includes a few levels of details.
* When complaining that two function types aren't assignable to each other, TS will typically give 3 levels of detail with increasing levels of specificity (see p. 95).

### Function Type Parentheses p. 96

### Parameter Type Inferences p. 96
* TS can infer the types of parameters in a function provided by to a location with a declared type.
* This is nice b/c it allows us to avoid the cumbersome chore of declaring parameter types for every function we write.
* Example p. 96 - 97:

```typescript
let singer: (song: string) => string;

singer = function (song) {
	// Type of song: string
	return `Singing: ${ song.toUpperCase() }!` ; // ok
};
```

* The above **singer** variable is known to be a function that takes in as a parameter that takes in an parameter of type *string*.
* So the *song* parameter in the function later assigned to *singer()* is known to be a *string*.
* Functions passed as arguments to parameters with function parameters types will have their parameter types inferred as well.

```typescript
const songs = ["Call Me", "Jolene", "The Chain"];

// song: string
// index: number
songs.forEach( (song, index) => {
	console.log( `${song} is at index ${index}` );
});
```

### Function Type Aliases p. 97
* Remember type aliases from Chapter 3 on Unions and Literals? They can be used for function types as well.
* Example p. 97

```typescript
type StringToNumber = (input: string) => number;
let stringToNumber: StringToNumber;
stringToNumber = (input) => input.length; // ok

// Error: type 'string' is not assignable to
// type 'number
stringtoNumber = (input) => input.toUpperCase();
                                  ^^^^^^^^^^^^^
```

* Similarly, function parameters can be themselves be typed with aliases that refer to a function type. See Example p. 98. 

```typescript
type NumberToString = (input: number) => string;
function usesNumberToString( numberToString: NumberToString ) {
	console.log( `The string is: ${numberToString(1234)}`);
}

useNumberToString( (input) => `${input}! Hooray!` ); // ok

// error
// Type 'number' is not assignable to type 'string'.
useNumberToString( (input) => input * 2 );
                              ^^^^^^^^
```
***
## More Return Types p. 98

### Void Returns p. 98

### Never Returns p. 100

***
## 8/19/2024

### Function Overloads p. 101
* Some JS functions are able to be called with drastically different sets of parameters that can't be represented just by optional and/or rest parameters.
* These functions can be described in TS by **overload signatures**.
* Example p. 101:

```typescript

function createDate( timestamp: number): Date;

function createDate( month: number, day: number, year: number): Date;

function createDate( monthOrTimestamp: number, day?: number, year?: number ) {
	return day === undefined || year === undefined
		? new Date( monthOrTimestamp )
		: new Date( year, monthOrTimestamp, day );
}

createDate(554356800); // ok
createDate( 7, 27, 1987); // ok

// Error: No overload expects exactly 2 arguments
// but overloads *do* exist that expect 1 or 3 arguments.
createDate( 4, 1);
```

* Pretty intesting. notes on p. 101
* Overload signatures are erased when transpiling TypeScript to output vanilla JS. The above code snippet would be output to roughly this vanilla JS:

```javascript
function createDate ( monthOrTimestamp, day, year ) {
	return day === undefined || year === undefined
		? new Date( monthOrTimestamp )
		: new Date( year, monthOrTimestamp, day );
}
```

* **WARNING: Function overloads are generally used as a last resort for complex, difficult-to-describe function types. It’s generally better to keep functions simple and avoid using function overloads when possible.**

### Call-Signature Compatibility p. 102
* The implementation signature used for an overloaded function's implementation is what the function's implementation uses for parameter types and return type.
* Thus, the return type and each parameter in a function's overload singature must be assignable to the parameter at the same index in its implementation signature.
* i.e., the implementation signature has to be compatible with all the overload signatures.

```typesccript
function format( data: string) : string; // ok
function format( data: string, needle: string, haystack: string ): string; // ok

function format( getData: () => string ): string;
         ^^^^^^
// Error this overload signature is *not* compatible with its
// implementation signature.

function format( data: string, needle?: string, haystack?: string ) {
	return needle && haystack ? data.replace( needle, haystack ): data;
}
```

***
## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.

`<script>`
