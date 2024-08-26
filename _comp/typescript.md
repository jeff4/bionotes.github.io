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

# Chapter 6: Arrays p. 104
* TypeScript supports the JS best practice of only using one datatype of the values within an array.

```typescript
const warriors = ["Artemisia", "Boudica"];

warriors.push("Zenobia"); // OK bc new input item is a string

// Error b/c input value is type 'boolean'
warriors.push(true);
```

* One can think of TS inference of an array's type from its initial embers as similar to how TS understands variable types from their initial values.

## 6.1 Array Types p. 105
* Variable meant to store arrays do *not* ned to have an initial value.
* The variables can start off as `undefined` and then receive an array value later.

```typescript
let arrayOfNumbers: number[];
arrayOfNumbers = [4, 8, 15, 16, 23, 42];
```
## 8/19/2024
### 6.1.1 Array and Function Types p. 105
* Array types are an example of a syntax container where function types may need parentheses to distinguis what's in the function type or not.
* Parentheses may be used to indicate which part of an annotation is the function return or the surrounding array type.
* The **createStrings** type here--it is a *function* type--is *not* the same as **stringCreators** which is an array type (Ex on p. 105-106):

```typescript

let createStrings: () => string[];

let stringCreators: ( ()=> string )[];
```

### 6.1.2 Union-Type Arrays p. 106
* One can use a union type to indicate that each element in an array can be one of multiple select types.
* When using array types with unions, *parentheses* may need to be used to indicate which part of an annotation is the **contents of the array** or the **surrounding union type**.
* Using parentheses in array 

```typescript
// This means that type is 
// either a *number* or an *array of strings*
let stringOrArrayOfNumbers: string | number[];

// This means that type is an array of elements
// that are *each* either a number or a string
let stringOrArrayOfNumbers: (string | number)[];
```

### 6.1.3 Evolving Any Arrays p. 106
* If one does not include any type annotation on a variable initally set to an empty array, TS will treat this new array as *evolving `any[]`*.
	* Evolving `any[]` means that this array can receive any type of content.
* Just like with evolving *any* variables, this is **not good**.
* The whole point of TS is to have clearly defined static types.o
* There are some times this may be useful--but **be careful**. see p. 107 for brief examples and more.

### 6.1.4 Multi-Dimensional Arrays p. 107
* A 2D array *aka* an *array of arrays* will have two `[]` like so p. 107:

```typescript
let 2dArray: number[][];

2dArray = [
  [1, 2, 3],
  [2, 4, 6],
  [3, 6, 9],
];

// higher dimension arrays

let 3dArray: number[][][];

3dArray = [
  [
    [ 1, 2],
    [ 3, 4],
  ],  [
    [ 2, 4],
    [ 6, 8],
  ],  [
    [ 3, 6],
    [ 9, 12],
  ],
];
```
* See TS example on p. 108:

```typescript
let arrayOfArraysOfNumbers: ( number[] )[];

```

## 8/20/2024
## 6.2 Array Members p. 108
* TS understands typical index-based access for retrieving members of an array to give back an element of that array's type.

### 6.2.1 Caveat: Unsound Members p. 108
* The TypeScript type system is known to be **technically unsound** b/c although TS gets most types right, TS *can* get types of values incorrect.
* In particular, **arrays are a source of unsoundness** in TS's type system.
* See example on p. 108-109

## 6.3 Spreads and Rests p. 109
### 6.3.1 Spreads p. 109
* Arrays can be joined together using the `...` spread operator.
* TypeScript understands the result array will contain values that can be either of the input arrays.
* If the input arrays are the same type, the output array will be that same type.
* If two arrays of *different* types are spread together to create a new array will be understood as an **union type** array of elements that either of the two original types.
* Example p. 110:

```typescript
// Type: string[]
const soldiers = [ "Harriet Tubman", "Joan of Arc", "Khutulun" ];

// Type: number[]
const soldierAges = [ 90, 19, 45 ];

// Type: ( string | number)[]
const conjoined = [...soldiers, ...soldierAges];
```

### 6.3.2 Spreading Rest Parameters p. 110
* TS recognizes and will perform type checking on the JS practie of using the `...` **spreading an array** as a rest parameter.
* Arrays used as arguments for rest parameters must have the same array type as the rest parameter.
* The **logWarriors()** function below takes in only *string* values for its `...names` rest parameter.
* Spreading an array of type **string[]** is allowed, but a **number[]** is *not*.

```typescript
function logWarriors( greeting: string, ...names: string[] ) {
	for ( const name of names ) {
		console.log( `${ greeting }, ${ name }!` );
	}
}

const warriors = [ "Cathay Williams", "Lozen", "Nzinga" ];

logWarriors( "Hello", ...warriors );

const birthYears = [ 1844, 1840, 1583 ];

logWarriors( "Born in", ...birthYears );
//                      ^^^^^^^^^^^^^
// Error: Argument of type 'number' is not assignable
// to parameter of type 'string'.
```

## 6.4 Tuples p. 109
* Although JS arrays can be any size, we can also make JS arrays a fixed size--which is called a **tuple**.
* Tuple arrays have a specific known type at each index that may be more specific than a union type of all possible members of the array.
* The syntax to declare a tuple type looks like an aray literal but with **types** instead of **elements**.
* Example p. 111

```typescript

let yearAndWarrior: [ number, string ];

yearAndWarrior = [ 508, "Tomyris" ]; // ok

yearAndWarrior = [ false, "Tomyris" ]; 
//                 ^^^^^
// Error: Type 'boolean' is not assignable to type 'number'

yearAndWarrior = [ 508 ]; 
//                 ^^^
// Error: Type '[number]' is not assignable to 
// type '[number, string]'. Source has 1 element
// but target requires 2.
```

* Tuples are often used in JS alongside array destructuring to be able to assign multiple values at once, such as setting 2 variables to initial values based on a single condition.
* For example, TS recognizes here that **year** is always going to be a *number* and **warrior** is always going to be a *string*.
* Example p. 111:

```typescript

let [ year, warrior ] = Math.random() > 0.5
	? [340, "Archidamia"]
	: [1828, "Rani of Jhansi"];
```

### 6.4.1 Tuple Assignability p. 111
* **Tuple types** are treated by TS as more specific than variable length array types.
* That means variable length array types aren't assignable to tuple types.
* Example p. 112:

```typescript
// Type: (boolean | number)[]
const pairLoose = [ false, 123 ];

const pairTupleLoose: [ boolean, number ] = pairLoose;
//    ^^^^^^^^^^^^^^
// Error: Type '( number | boolean )[]' is not
// assignable to type '[boolean, number]'
// Target requires 2 elements but source may have fewer
```
* In above example, although we as humans see **pairLoose** as having **[boolean, number]** inside, TS infers it to be the more general **(boolean | number)[]** type.
* If **pairLoose** had been declared as a **[boolean, number]** itself, the assignment of its value to *pairTuple* would have been permitted.
* Tuples of different lengths are also *not* assignable to each other.
* As TS includes knowing how many members are in the tuple in tuple types. 
* Consider this example p. 112:

```typescript
const tupleThree: [boolean, number, string] = [false, 1583, "Nzinga"];

const tupleTwoExact: [boolean, number] = [tupleThree[0], tupleThree[1]];

const tupleTwoExtra: [boolean, number] = tupleThree;
//    ^^^^^^^^^^^^^
// Error: Type '[boolean, number, string]' is not assignable
// to type '[boolean, number]'.
// Source has **3** elements but target only allows 2.
```

#### 6.4.1.1 Tuple as Rest Parameters p. 113
* B/c tuples are seen as arrays with more specific type information on length and element types, they can be particularly useful for storing arguments to be passed to a function.
* TS is able to provide accurate type checking for tuples passed as `...` rest parameters.
* Here, the **logPair** function's parameters are typed string and number.
* Trying to pass in a value of type *( string \| number)[]* as arguments wouldn't be type safe as the contents might not match up: they could both be the same type, or one of each type in the wrong order.
* However, if TS knows the value to be a *[string, number]* tuple, it understands the values match up:

```typescript
function logPair( name: string, value: number) {
	console.log(`${name} has ${value}`);
}

const pairArray = ["Amage", 1];

logPair(...pairArray);
// Error: A spread argument must either have a tuple type
// or be passed to a rest operator.

const pairTupleIncorrect: [number, string] = [1, "Amage"];

logPair(...pairTupleIncorrect);
// Error: Argument of type 'number' is not assignable
// to parameter of type 'string'.

const pairTupleCorrect: [string, number] = ["Amage", 1];

logPair(...pairTupleCorrect); // ok
```

* If you really want to go wild with your rest parameter tuples, you can mix them with arrays to store a *list of arguments* for **multiple function calls**. Example p. 113-114:

```typescript
function logTrio (name: string, value: [number, boolean]) {
	console.log( `${name} has ${value[0]} ${value[1]}` ); 
}

const trios: [ string, [number, boolean] ][] = [
  ["Amanitore", [1, true]],
  ["Aethelflaed", [2, false]],
  ["Ann E. Dunwoody", [3, false]]
];

trios.forEach( trio => logTrio(...trio) ); //ok

// Error -- see p. 114
trios.forEach(logTrio);
```

### 6.4.2 Tuple Inferences p. 114
* TS generally treats created arrays as variable length arrays, not tuples. 
* If TS sees an array being used as a vairable's initial value or the returned value for a function, TS will then assume a *flexible sized* array rather than a fixed-sized tuple.
* Example p. 114:

```typescript
// Return type:  (string | number )[]
function firstCharAndSize( input: string ) {
	return [input[0], input.length);
}

// firstChar type: string | number
// size type: string | number
const [firstChar, size] = firstCharAndSize("Gudit");
```

* There are two common ways in TS to indiciate that a vlaue should be a more specific tuple type instead of a general array type:
	1. using **explicit tuple types**; and
	1. using **const** assertions.

#### 6.4.2.1 Explicit tuple types p. 115
* Tuple types may be used in type annotations such as return type annotation for a function...

#### 6.4.2.2 Const asserted tuples p. 115

***

# Chapter 7: Interfaces p. 118

## 7.1 Type Aliases vs. Interfaces p. 118
* In general, it's better to use **interfaces** versus **aliased object types**.
	* For more on **aliased object types**, see p. 69. More concise syntax than *vanilla object type* which is semantically the same.
	* See initial example of vanilla *object type* declaration on p. 68: `let PoetLater { born:number; name:string }`.
	* Compare with *aliased object type* declaration on p. 69: `type Poet { born:number; name:string }; let poetLater: Poet;`.
* Quick comparison of aliased object type vs. interface

```typescript

// Aliased Object Type
type Poet = {
	born: number;
	name: string;
}

// Equivalent syntax for interface
interface Poet {
	born: number;
	name: string;
}
// Note: that interfaces preferentially do *not* have terminating semicolons
// whereas aliased object types.
```

* TS's assignability checking and error messages for interfaces also work and look just about the same as they do for object types.
* The following assignability errors for assigning to the **valueLater** variable would be roughly the same if *Poet* was an interface or type alias:

```typescript
let valueLater: Poet;

// ok
valueLater = {
	born: 1935,
	name: 'Sara Teasdale',
};

// Error: Type 'string' is not assignable to 'Poet'
valueLater = "Emily Dickinson";

// Error: Type 'boolean' is not assignable to type 'number'
valueLater = {
	born: true,
	name: 'Sappho'
};
```

### 7.1.1 Differences between interfaces and type aliases in this chapter
* Interfaces can *merge* together to be augmented--a feature particularly useful when working with 3rd-party code such as built-in globals or npm packages.
* In Chapter 8, we'll see that interfaces can be used to type check the structure of class declarations while type aliases cannot.
* Interfaces are generally speedier for the TS type checker to work with: they declare a named type that can be cached more easily interally, rather than a dynamic copy-and-paste of a new object literal the way type aliases do.
* B/c interfaces are considered *named objects* rather than an alias for an unnamed object literal, their error messages are more likely to be readable in hard edge cases.
* **In general, it's best to use interfaces whenever possible.** p. 120

***

## 7.2 Types of Properties p. 120
* JS objects can be wild and wacky in real-world usage, (see p. 120 for examples). 
* TS interfaces provide a system of tools that help us model that wackiness.

### 7.2.1 Optional Properties p. 120
* As with object types, interface properties don't all have to be required in the object.
* One can indicate that an interface's property is optional by including a `?` before the `:` in its type annotation.
* This **Book** interface requires only a *required* property and optionally allows an *optional*.
* Objects adhering to it may provide *optional* or leave it out as long as they provide required. Example p. 121:
* The same caveats around optional vs. regular properties when a type happens to include an **undefined** in a type union apply to interfaces and object types. see more on p. 121

```typescript
interface Book {
	author?: string; // '?' indicates that this interface property is optional
	pages: number;
};

// ok
const ok: Book = {
	author: "Rita Dove",
	pages: 80,
};

// Error: Property 'author' is missing in type 
// '{ pages: number; }' but required in type 'Book'.

const missing: Book = {
	pages: 80,
};
```

### 7.2.2 Read-Only Properties p. 121
* You may sometimes wish to block users of your interface from reassigning properties of objects adhering to an interface.
* TypeScript allows you to add a **readonly** modifier before a property name to indicate that once set, that property should not be set to a different value.
* Example p. 121, the **text** property in the below **Page** interface returns a string when accessed.
	* But TS raises a type error if the *text* property is assigned a new value:

```typescript
interface Page {
	readonly text: string;
}

function read( pageObject: Page ) {
	
	// this is ok: just accessing the 'text' property 
	// doesn't try to modify it
	console.log( pageObject.text );

	// this will cause an error b/c are trying to 
	// assign a new value to the 'text' property
	pageObject.text += "!";
}
```
* More on usage of **readonly** modifiers and how they only exist in the type system / interfaces p. 122.

***

### 7.2.3 Functions and Methods p. 122
* It is very common in JS for object members to be functions.
* TS allows declaring interface members to be function types--covered in Chapter 5: Functions.

### Two ways of declaring interface members as functions p.123
1. **Way 1--Method Syntax**: declaring that a member of the interface is a function intended to be called as a member of the object, e.g., **member(): void**.
1. **Way 2--Property Syntax**: declaring that a member of the interface is equal to a *standalone function*, e.g., **member: () => void**.

#### More notes and an example of Way 1 + Way 2  p. 123
* The two declaration forms are an analog for the two ways you can declare a JS object as having a function.

```typescript
// uses both ways to declare interface methods
interface HasBothFunctionTypes {
	property: () => string; // Way 2: Property Syntax
	method(): string;       // Way 1: Method Syntax
}

const hasBoth: HasBothFunctionTypes = {
	property: () => "",
	method() {
		return "";
	}
};

hasBoth.property(); //ok
hasBoth.method(); //ok
```

* Both ways can receive the **? optional modifier** to indicate that a *function is not needed** as part of the interface.
* Example p. 123

```typescript
interface OptionalReadonlyFunctions {
  optionalProperty?: () => string;
  optionalMethod?(): string;
}
```
* Method and property declarations can mostly be used interchangeably. Three main differences
	1. Only **Way 2: properties** can be declared **readonly**. **Way 1: method** cannot be declared readonly.
	1. Interface merging is treated differently between **Way 2** and **Way 1**. 
	1. Some of the operations performed on types treat them differently--see Chapter 15 on Type Operations.
* For now, the general style guide LTS recommends is:
	* Use **Way 1: Method function declaration** if one knows the underlying function may refer to keyword **this** (See Chapter 8 on Classes).
	* Use **Way 2: Property function declaration** otherwise.

***

### 7.2.4 Call Signatures p. 124
* Both interfaces and object types can declare **call signatures**.
* *Call Signatures* are a type system description of how a value may be called like a function.
* Example p. 124-125:

```typescript
type FunctionAlias = ( input: string ) => number;

interface CallSignature {
	( input: string ): number;
}

// Type: ( input: string ) => number
const typedFunctionAlias: FunctionAlias = (input) => input.length; // ok

// Type: ( input: string ) => number
const typedCallSignature: CallSignature = (input) => input.length; // ok
```
* Call signatures can be used to describe functions that additionally have some user-defined property on them.
* TS will recognize a property added to a function declaration as adding to that function declaration's type.
* Example p. 125:

```typescript
interface FunctionWithCount {
	count: number;
	(): void;
}

let hasCallCount: FunctionWithCount;

function keepsTrackOfCalls() {
	keepsTrackOfCalls.count += 1;
	console.log( `I've been called ${ keepsTrackOfCalls.count } times!` );
}

keepsTrackOfCalls.count = 0;

hasCallCount = keepsTrackOfCalls; //ok

function doesNotHaveCount() {
	console.log( "No idea!" );
}

// Error: property 'count' is missing in type
// '() => void' but required in type 'FunctionWithCalls'
hasCallCount = doesNotHaveCount;
```
* The above example has a **keepTrackOfCalls** function declaration which is given a **count** property of type *number*. It's assignable using the FunctionWithCount interface.
* The error on the last line is caused b/c it was *not* given a **count**.

***

### 7.2.5 Index Signatures p. 126
* TS provides a syntax called **index signature** to indicate that an interface's objects are allowed to take in *any* key and return a certain type under that key.
* This makes *"container"* objects practical in JS projects that store values that are referenced using an arbitrary *string* primary key.
* **Index Signatures** are most commonly used with string keys b/c JS object property lookcups convert keys to string implicitly.
* An index signature looks like a regular property definition but with a type after the key like so:
```typescript
{
	[ i: string]: ...
}
```

#### 7.2.5.1 Example 1

* The below **WordCounts** interface example is declared as allowing *any* **string** key with a number value.
* Objects of that type aren't bound to receiving any particular key--as long as the value is a **number** p. 126:

```typescript
interface WordCounts {
  [i: string]: number;
}

const counts: WordCounts = {};

counts.apple = 0; // ok this is a *number*
counts.banana = 1; // ok this is a *number*

counts.cherry = false; // error
// Error: Type 'boolean' is not assignable 
// to type 'number'.
```
* Index signatures are convenient for assigning values to an object but aren't completely type safe.
* Index signatures indicate that an object shoukd give back a value no matter what property is being accessed.

#### 7.2.5.2 Example 2

* Consider this example (p. 126-127). The **publishDates** value safely returns a **Frankenstein** object as a **Date** type--but *tricks* TS into thinking its **Beloved** is defined.
	* Even though **Beloved** is in fact *not* defined.

```typescript
interface DatesByName {
  [i: string]: Date;
}

const publishDates: DatesByName = {
  Frankenstein: new Date( "1 January 1818" ),
};

publishDates.Frankenstein; // Type: Date
console.log( publishDates.Frankenstein.toString() ); // ok

publishDates.Beloved; // Type: Date--but runtime value is undefined!

// OK in the type system, but it causes a runtime error
// Runtime Error: Cannot read property 'toString'
// of undefined (reading publishDates.Beloved)
console.log( publishDates.Beloved.toString() ); 
```
* When possible, if one is looking to store key-value pairs and the keys are *not* known ahead of time, it is generally better to use **Map** instead.
* The **.get()** method of Maps always returns a type with a `| undefined` to indicate that the key might not exist.
* See more in Chapter 9 on working with generic container classes such as **Map** and **Set**.

#### 7.2.5.3 Mixing properties and index signatures p. 127
* Interfaces are able to include explicitly named properties and catchall *string* index signatures...
* ...but there is *one* catch.
* Each named property's type must be assignable to its catchall index signature's type.
* One can think of mixing them as telling TS that named properties give a more specific type, and any other property falls back to the index signature's type.
* Example on p. 127-128, where **HistoricalNovels** declares that all properties are type *number*. Additionally, the *Oroonoko* property must exist to begin with:

```typescript
interface Historical Novels {
  Oroonoko: number;
  [i: string]: number;
}

// Ok
const novels: HistoricalNovels = {
  Outlander: 1991,
  Oroonoko: 1688,
};

// Error: Property 'Oroonoko' is missing in type
// '{ Outlander: number; }' but required in type
// 'HistoricalNovels'.
const missingOroonoko: HistoricalNovels = {
  Outlander: 1991,
};
```
* One common type system trick with mixed properties and index signatures is to use a more specific property type literal for the named property than an index signature's primitive.
* As long as the named property's type is assignble to the index ssignature's--which is true for a literal and a primitive, respectively--TS will allow it.
* Consider this example p. 128. The **ChapterStarts** interface declares that a property under **preface** must be *0* and all other properties have the more general **number**.
* That means any object adhering to **ChapterStarts** must have a *preface* property equal to *0*.

```typescript
interface ChatperStarts {
  preface: 0;
  [i: string]: number;
}

const correctPreface: ChapterStarts = {
  preface: 0,
  night: 1,
  shopping; 5
};

const wrongPreface: ChapterStarts = {
  preface: 1,
  // Error: Type '1' is not assignable to type '0'
};
```

#### 7.2.5.4 Numeric Index Signatures p. 128
* Although JS implicitly converts object property lookup keys to strings, it is sometimes desirable to only allow **numbers as keys**.
* TS index signatures can use a *number* type instead of a *string* but with the same catch as *named properties*--that their types must be assignable to the catchall *string* index signatures.
* Example p. 128-129

```typescript
// Ok
interface MoreNarrowNumbers {
  [i: number]: string;
  [i: string]: string | undefined;
}

//ok
const mixesNumbersAndStrings: MoreNarrowNumbers = {
  0: '',
  key1: '',
  key2: undefined,
}

interface MoreNarrowStrings {
  // Error: 'number' index type 'string | undefined' 
  // is not assignable to 'string' index type 'string'.
  [i: number]: string | undefined;
  
  [i: string]: string;
}
```
***
### 7.2.6 Nested Interfaces p. 129
* Just like object types can be nested as properties of other object types, interface types can also have properties that are themselves interface types (or object types).
#### 7.2.6.1 Example of nested interfaces p. 129-130
* This **Novel** interfae contains an **author** property that must satisfy an inline object type and a **setting** property that must satisfy the **Setting** interface:

```typescript
interface Novel {
  author: {
    name: string;
  };
  setting: Setting;
}

interface Setting {
  place: string;
  year: number;
}

let myNovel: Novel;

// OK
myNovel = {
  author: {
    name: 'Jane Austen',
  },
  setting: {
    place: 'England',
    year: 1812,
  }
};

// Error: Property 'year' is missing in type
// '{ place: string; }' but required in type 'Setting'.
myNovel = {
  author: {
    name: 'Emily Bronte',
  },
  setting: {
    place: 'West Yorkshire',
  },
};
```

***
## 8/23/2024
## 7.3 Interface Extensions p. 130

### 7.3.1 Intro
* Sometimes, you end up with multiple interfaces that look similar.
* Let's reduce keyboard-typing and complexity by using the **extends** keyword to let one interface extend another interface.
* The parent/original interface is called the **base interface**. 
* One may *extend* from the base interface to a child **derived interface**. p. 130
	* A *derived interface* tells TS that all objects adhering to that derivd interface must also have all the same members of the base interface.
* **Interface extensions** are a nifty way to represt that one type of entity in your project is a *superset* of another entity.	* **Interface extensions** allow programmers to avoid having to type out the same code repeatedly across multiple interfaces. p. 131

#### 7.3.1.1 Example p. 130-131
* In this example, the **Novella** interface extends from **Writing**.
* Thus, the **Novella** interface requires objects to have members that belong to both **Novella.pages** and **Writing.title**.

```typescript
interface Writing {
  title: string;
}

interface Novella extends Writing {
  pages: number;
}

// ok
let myNovella: Novella = {
  pages: 195,
  title: "Ethan Frome",
};

let missingPages: Novella = {
  //^^^^^^^^^^^^

  // Error: Property 'pages' is missing in type
  // '{ title: string; }' but required in type 'Novella'
  title: "The Awakening",
}

let extraProperty: Novella = {
  //^^^^^^^^^^^^^

  // Error: Type '{ genre: string; name: string; strategy: string;}'
  // is not assignable to type 'Novella'.
  //   Object literal may only specify known properties,
  //   and 'genre' does not exist in type 'Novella'
  pages: 300,
  strategy: "baseline",
  style: "Naturalism",

};
```
***

### 7.3.2 Overriden Properties p. 131
* Derived interfaces may *override* properties from their base interface by declaring the property again with a different type.
* TS's type checker will enforce that an overridden property must be assignable to its base property.
* Most derived interfaces that redeclare properties do so either to make thos properties a more specific subset of a type union or to make the properties a type that extends from the base interface's type. 

#### 7.3.2.1 Example p. 132
* For example, this **WithNullableName** type is properly made non-nullable in **WithNonNullableName**.
* However, **WithNumericName** is *not* allowed as `number | string` and is not assignable to `string | null`:

```typescript
inteface WithNullableName {
  name: string | null;
}

// ok
interface WithNonNullableName extends WithNullableName {
  name: string;
}

// Error: Interface 'WithNumericName' incorrectly extends
// extends interface 'WithNullableName'.
// Type of property 'name' are incompatible.
// Type 'string | number' is not assignable to type 'string | null'.
// Type 'number' is not assignable to type 'string'.
interface WithNumericName extends WithNullableName {
  name: number | string;
}
```
***

### 7.3.3 Extending Multiple Interfaces p. 132
* An interface in TS is allowed to be declared as extending multiple other interfaces at once.
* Any number of **base interface** names separated by commas may be used after the `extends` keyword following the **derived interface's** name.
* *The derived interface will receive **all** members from every parent/base interface.*
* By marking an interface as extending multiple other base interfaces, one can both reduce code duplications and make it easier for object shapes to be reused across different areas of code. p. 133

#### 7.3.3.1 Example p. 132-133
* Here, the **GivesBothAndEither** has 3 methods:
	1. One on its own
	1. One from **GivesNumber**
	1. One from **GivesString**

```typescript
interface GivesNumber {
  givesNumber(): number;
}

interface GivesString {
  givesString(): string;
}

interface GivesBothAndEither extends GivesNumber, GivesString {
  giveEither(): number | string;
}

function useGivesBoth( instance: GivesBothAndEither ) {
  instance.giveEither(); // Type: number | string
  instance.giveNumber(); // Type: number 
  instance.giveString(); // Type: string
}
```

***

## 7.4 Interface Merging p. 133

* One of the important features of interfaces is their ability to **merge** with each other.
* Interface merging means that if 2 interfaces are declared within the same scope with the *same name*, they will join into one bigger interface under that name using all the fields of both base interfaces.

### 7.4.1 Merged interface examples p. 133-134
* Interface merging is not used a lot in regular TypeScript and LTS recommends avoiding it.
* However, merging interfaces *can* be useful when augmenting interfaces from **external packages**.
* This snippet declares a **Merged** interface with 2 properties: *fromFirst* and *fromSecond*.

```typescript
interface Merged {
  fromFirst: string;
}

interface Merged {
  fromSecond: number;
}
```
* which is equivalent to...

```typescript
interface Merged {
  fromFirst: string;
  fromSecond: number;
}
```

* Example of good use case for merged interface on p. 134. Consider the built-in global JS interface **Window**. You can do this (explained more in Chapter 11 / Chapter 13):

```typescript
interface Window {
  myEnvironmentVariable: string;
}

window.myEnvironmentalVariable; // Type: string 
```


### 7.4.2 Member Naming Conflicts p. 134
* Note that merged interfaces may not declare the same name of a property multiple times with **different types**. i.e., when you use the same property name, it *must be the same type for each occurrence!

#### 7.4.2.1 Examples of naming conflict p. 134-135
* In the below **MergedProperties** interface, the **same** property is allowed because it has the same type in both decclarations.
* But the **different** property raises an error b/c of a difference in type in the 2 declarations.

```typescript

interface MergedProperties {
  same: ( input: boolean ) => string;
  different: ( input: string ) => string;
}

interface MergedProperties {
  same: ( input: boolean ) => string; //ok
  
  different: ( input: number ) => string; //ok
  // Error: subsequent property declarations must have the same type
  // Property 'different' must be of type '(input: string) => string', 
  // but here has type '(input: number) => string'.

}
```
* Merged interfaces may, however, define a method of the same name and a different signature. Doing so creates a function overload for the method.
* The following example p. 135 has a **MergedMethods** interface which creates a *different* method that has 2 overloads:

```typescript

interface MergedMethods {
  different( input: string ): string;
}

interface MergedMethods {
   different( input: number): string; // ok
}
```
## 7.5 Summary
* Next chapter on **classes** will show how to set up multiple objects that have the same properties.

***

# Chapter 8: Classes p. 137
## 8/24/2024
## 8.1 Class Methods p. 137
### 8.1.1 Introduction
* TS generally understands methods the same way it understands standalone functions. 
* Parameter types default to *any* unless given a type or default value; calling a method requires an acceptable number of argumetns; return types can generally be inferred if the function is not recursive.

### 8.1.2 Example p. 137-138
* This code snippet defines a **Greeter** class with a *greet()* class method that takes in a single required parameter of type *number*:

```typescript
class Greeter {
  greet( name: string) {
    console.log( `${name}, do your stuff!`);
  }
}
// Ok
new Greeter().greet("Miss Frisby");

// Error: expected 1 argument, received 0 arguments
new Greeter().greet();

```
* Class Constructors are treated like typical class methods wrt their parameters.
* TS will perform type checking to make sure a correct number of arguments with correct types are provided to method calls.
* This **Greeted** constructor example also expects its *message: string* parameter to be provided (p. 138)

```typescript
class Greeted {
  constructor( message: string ) {
    console.log( `As I always say: ${message}!` );
  }
}

// ok
new Greeted( "take chances, make mistakes, get messy" );

// Error: expected 1 argument, received 0 arguments
new Greeted();
```

***

## 8.2 Class Properties
### 8.2.1 Introduction p. 138
* In TS, to read from or write to a property in a class, one must explicitly declare it in the class.
* Class properties are declared using the same syntax as interfaces: their name followed optionally by a type annotation.
* TS will not attempt to deduce what members may exist on a class from their assignments in a constructor.

#### 8.2.1.1 Examples p. 139
* In this example, **destination** is allowed to be assigned to and accessed on instances of the **FieldTrip** class because it is explicitly declared as a *string*.
* The *this.nonexistent* assignment in the constructor is not allowed because the class does not declare a *nonexistent* property:

```typescript
class FieldTrip {
  destination string;

  constructor( destination: string ) {
    this.destination = destination; // ok
    console.log( `We're going to ${this.destination}!` );

    this.nonexistent = destination;
    //   ^^^^^^^^^^^
    //  Error: Property 'nonexistent' does not exist on
    //  type 'FieldTrip'
  }
}
```
* Explicitly declaring class properties allows TS to quickly understand what is or is not allowed to exist on instances of classes.
* Later, when class instances are in use, TS uses that understanding to give a type error if code attempts to access a member of a class instance not known to exist, such as with this continuation's **trip.nonexistent**:

```typescript
const trip = new FieldTrip( "planetarium" );

//ok
trip.destination; 

//Error -- Property 'nonexistent' does not exist on type 'FieldTrip'.
trip.nonexistent;
```

***
### 8.2.2 Function Properties p. 139
#### 8.2.2.1 Introduction
* Let's recap the fundamentals of JS method scoping and syntax.
* JS contains 2 syntaxes for declaring a member on a class is callable function: **method** and **property**.
* LTS has already illustrated the method of approach: `myFunction() {...}`.
* Example p. 140:

```typescript
class WithMethod {
  myMethod() {...}
}

new WithMethod().myMethod === new WithMethod().MyMethod; // true
```
* The other syntax is to declare a property whose value happens to be a function.
* This creates a new function *per instance* of the class. This can be useful with the `() =>` arrow functions. whose **this** scope should always point to the class instance.
* This **WithProperty** class contains a single property of name **myProperty** and `type() => void` that will be recreated for each class instance:

```typescript
class WithProperty {
  myProperty: () => {...}
}

new WithMethod().myProperty === new WithMethod().MyProperty; // false
```



#### 8.2.2.2 Passing a function as an argument to a class *WithPropertyParameters*

* Function properties can be given parameters and return types using the same syntax as class methods and standalone functions. p. 140
* After all, they're a value assigned to a class member; the value just happens to be a function.
* The following example (p. 140-141) has a **WithPropertyParameters** class which has a *takesParameters* property.
* The *takesParameters* property is of type: `( input: string ) => number`, which is an arrow function.

```typescript
class WithPropertyParameters {
  takesParameters = ( input: boolean ) => input ? "Yes" : "No";
}

const instance = new WithPropertyParameters();

//ok
instance.takesParameters( true );

// Error: Argument of type 'number' is not
// Assignable to parameter of type 'boolean'
instance.takesParameters( 123 );
                          ^^^

```

*** 
### 8.2.3 Initialization Checking p. 141
* With strict compiler settings enabled, TS will check that each property declared--whose type does not include *undefined*--is assinged a value in the constructore.
* This strict initialization checking is useful b/c it prevents code from accidentally forgetting to assign a value to a class property.

#### 8.2.3.1 Intialization Examples p. 141-142
* The following **WithValue** class does not assign a value to its *unused* property; TS recognizes this as an error:

```typescript

class WithValue {

  //ok
  immediate = 0;
  
  // ok -- set in the constructor
  later: number;
  
  // ok -- allowed to be undefined
  mayBeUndefined: number | undefined;
  
  //Error: property 'unused' has no intializer
  // and is not definitely assigned in the constructor
  constructor() {
    this.later = 1;
  }
}
```
* Without strict initialization checking, a class instance could be allowed to access a value that might be *undefined* even though the type system says it *can't be*.
* This following example (p. 142) would compile happily *if strict initialization checking didn't happen; but the resultant JS would crash at runtime:

```typescript
class MissingInitializer {
  property: string;
}

// TypeError: Cannot read property 'length' of undefined
new MissingInitializer().property.length;
```
* The billion-dollar mistake strikes again!
* See Chapter 12 on Using IDE features for more on the *strictPropertyInitialization* compiler option.

***

### 8.2.3.2 Definitely assigned properties p. 142
* Although strict initialization checking is useful most of the time, one may comr across some cases where a class property is *intentionally* able to stay unassigned after the class constructor.
* One may use a `!` exclaimation point (bang) after the name of a property to disable it's initialization check.
* This tells TS that the peropty will be assigned a value other than *undefined* before its first usage.
* Example p. 142-143:

```typescript
class ActivitiesQueue {
  pending!: string[]; //ok

  initialize( pending: string[] ) {
    this.pending = pending;
  }

  next() {
    return this.pending.pop();
  }
}

const activities = new ActivitiesQueue();

activities.initialize( ['eat', 'sleep', 'learn'])
activities.next();
```

***
### 8.2.4 Optional Properties p. 143
* Classes in TS may declare a property as optional with a `?` question mark after its declaration name, just like with TS interfaces.
* In this Example (p. 143), the optional **property** property is not allowed to be assigned in the class constructor regardless of strict property initialization checking:

```typescript
class MissingInitializer {
  property?: string;
}

//ok
new MissingInitializer().property?.length; 

// Error: Object is possibly 'undefined'
new MissingInitializer().property.length;
```



***
### 8.2.5 Read-Only Properties p. 143
* TS classes may declare a property as read-only by adding the **readonly* keyword before its declaration name--just like with TS interfaces.
* Per note in textbox on p. 144, might be best to use `#` (pound sign / hashtag) to specify private fields in case external 3rd party devs of your library might not realize that you've marked a property as read only. So probably use **JS private fields with *#*** instead of TS read-only properties.
* Example p. 144

```typescript
class Quote {
  readonly text: string;

  constructor( text: string ) {
    this.text = ;
  }

  emphasize() {

    // Error: cannot assign to 'text' bc it is a 
    // read-only property
    this.text += "!";
         ^^^^
  }
}

const quote = new Quote(
  "There is a brilliant child locked in every student."
);

// Error: Cannot assign to 'text' because it is a
// read-only property
Quote.text = "Ha!";
```
* Additional more complicated corner-case example on p. 144-145.

***

## 8.3 Classes as Types p. 145
* Classes are relatively unique in the type system in that a class declaration creates both a runtime value--the class *itself*--as well as a **type** that can be used in type annotations.
* Consider Example (p. 145-146). 
	* The name of the *Teacher** class is used to annotate a **teacher** variable. 
	* This tells TS that it should be assigned *only* values that are assignable to the **Teacher** class--including instances of the **Teacher** class itself!

```typescript
class Teacher {
  sayHello() {
    console.log("Take chances, make mistakes, get messy!");
  }
}

let teacher: Teacher;

teacher = new Teacher(); //ok

// Error: type 'string' is not assignable to 
// type 'Teacher'
teacher = "Wahoo!";
```
* Interestingly, TS will consider any object type that happens to include all the same members of a class to be assignable to the class.
* This is bc TS's structural typing cares *only* about the shape of the objects--*not* how the object is declared.
* Example (p. 146), **withSchoolBus** takes in a parameter of type **SchoolBus**. That can be satisfied by *any* object that happens to have a **getAbilities** property of type `() => string[]`, such as an instance of the **SchoolBus** class.

```typescript
class SchoolBus {
  getAbilities() {
    return [ "magic", "shapeshifting" ];
  }
}

function withSchoolBus( bus: SchoolBus ) {
  console.log( bus.getAbilities() );
}

// ok
withSchoolBus( new SchoolBus() );

// ok
withSchoolBus(
  {
    getAbilities: () => [ "transmogrification" ],
  }
);

withSchoolBus( {

  // Error: Type 'number' is not assignable to type
  // 'string[]'
  getAbilities: () => 123,

});
```

***
## 8/25/2024
## 8.4 Classes and Interfaces p. 147
### 8.4.1 Introduction
* Back in Chapter 7: Interfaces, I showed you how interfaces allow TS developers to set up expectations for object shapes in code.
* TS allows a class to declare its instances as adhering to an interface by adding the **implements** keyword after the class name, followed by the name of an interface.

### 8.4.2 Examples p. 147-148
* In this example, the **Student** class correctly implements the **Learner** interface by including its property *name* and its method *study()*, but the **Slacker** is missing a *study()* and thus results in a type error.

```typescript
interface Learner {
  name: string;
  study( hours: number ): void;
}

class Student implements Learner {
  name: string;

  constructor( name: string ) {
    this.name = name;
  }

  study( hours: number ) {
    for ( let i=0; i < hours; i += 1 ) {
      console.log( "...studying..." );
    }
  }
}

// Error: Class Slacker doesn't implement interface 
// 'Learner' properly b/c Property 'study' is missing 
class Slacker implements Learner {
  name = "Rocky";
}
```
* Marking a class as implementing an interface does not change anything about how the class is used.
* If the class already happened to match up to the interface, TS's type checker would have allowed its instances to be used in places where an instance of the interface is required anyways.
* TS won't even infer the types of methods/properties on the class from teh interface: if we had added a **study( hours ) {}** method to the **Slacker** example, TS would consider the **hours** parameter an implicit **any** unless we gave it a type annotation.
* Consider this new version (p. 148) of the **Student** class created in the previous example

```typescript
class Student implements Learner {
  // error: Member 'name' implicitly has 
  // type 'any' which is not allowable
  name;

  study( hours) {
    // Error: Parameter 'hours' implicitly
    // has an 'any' type
  }
}
```
* This is raising type errors with the *any* type.
* Implementing an interface is purely a safety check.
* It does not copy any interface members onto the class definition for you.
* Rather, implementing an interface signals your intention to the type checker and raises type errors int he class definition--rather than later on where class instances are used.
* It's similar in purpose to adding a type annotation to a variable even though it has an initial value.

***

### 8.4.3 Implementing Multiple Interfaces p. 149
* Classes in TypeScript are allowed to be declared as implementing multiple interfaces.
* The list of implemented interfaces for a class may be any number of interface names with commas in-between.

#### 8.4.3.1 Examples p. 149-150
* **Example 1**, p. 149, both classes are required to have a least a *grades* property to implement the **Graded** interface and a *report* property to implement the **Reporter** interface.
	* The **Empty** class has two type errors for failing to implement either of the interfaces properly.

```typescript
interface Graded {
  grades: number[];
}

interface Reporter {
  report: () => string;
}

class ReportCard implements Graded, Reporter {
  grades: number[];

  constructor( grades: number[] ) {
    this.grades = grades;
  }

  report() {
    return this.grades.join(", ");
  }

}

class Empty implements Graded, Reporter {}
      ^^^^^
// Error, class 'Empty' incorrectly implements 
// interface 'Graded' (see more on p. 149)


// Error, class 'Empty' incorrectly implements 
// interface 'Reporter' (see more on p. 149)
```

* In practice, there may be some interfaces whose definitions make it impossible to have a class that implements both interfaces.
* Attempting to declare a class implementing two conflicting interfaces will result in at least one type error on the class.
* **Example 2**, p. 150, has two interfaces: (a) **AgeIsANumber**; and (b) **AgeIsNotANumber**. Neither the **AsNumber** class nor the **NotAsNumber** class properly implements both interfaces.

```typescript
interface AgeIsANumber {
  age: number;
}

interface AgeIsNotANumber {
  age:() => string;
}

// Error: Property 'age' in type 'AsNumber' is not assignable
// to the same property in base type 'AgeIsNotANumber'
class AsNumber implements AgeIsNumber, AgeIsNotANumber {
  age = 0;
}


// Error: Property 'age' in type 'NotAsNumber' is not assignable
// to the same property in base type 'AgeIsANumber'
class NotAsNumber implements AgeIsNumber, AgeIsNotANumber {
  age() { return ""; }
}
```

***

## 8.5 Extending a Class p. 151

### 8.5.1 Intro p. 151
* When one extends a class in JS, one can add type checking to the derived class using TS.
* Example on p. 151:

```typescript
class Teacher {
  teach() {
    console.log( "The surest test of discipline..." );
  }
}

class StudentTeacher extends Teacher {
  learn() {
    console.log( "I cannot afford the luxury of a closed mind." );
  }
}

const teacher = new StudentTeacher();

// OK (defined on base class)
teacher.teach();

// OK (defined on subclass aka derived class)
teacher.learn();

// Error: Property 'otherFunction' does not exist 
// on type 'StudentTeacher'
teacher.otherFunction();
```
***

### 8.5.2 Extension Assignability p. 151
* Subclasses inherit members from their base class much like derived interfaces extend base interfaces.
* Instances of subclasses have all the members of their base class and thus may be used wherever an instance of the base is required.
* If a base class doesn't have all the members of a subclass does, then it can't be used when the more specific subclass is required.

#### 8.5.2.1 Examples 
* **Example 1** p. 151-152: instances of the following **Lesson** class may not be used where instances of its derived **OnlineLesson** are required, but derived instances may be used to satisfy either the base class or the subclass:

```typescript
class Lesson {
  subject: string;

  constructor( subject: string ) {
    this.subject = subject;
  }
}

class OnlineLesson extends Lesson {
  url: string;

  constructor( subject: string, url: string ) {
    super( subject );
    this.url = url;
  }
}

let lesson: Lesson;

// ok
lesson = new Lesson( "coding" );

// ok
lesson = new OnlineLesson( "coding", "oreilly.com");

let online: OnlineLesson;
online = new OnlineLesson( "coding", "oreilly.com" ); // ok

// error: property 'url' is missing in type 'Lesson'
// but required in type 'OnlineLesson'
online = new Lesson( "coding" );
```

* Per TS' structural typing, if all members on a subclass already exist on its base class with the same type, then instances of the base class are still allowed to be used in place of the subclass.
* **Example 2**, p. 152, has **LabeledPastGrades** only adds an optional property to **PastGrades**, so instances of the base class may be used in place of the subclass:

```typescript
class PastGrades {
  grades: number[] = [];
}

class LabeledPastGrades extends PastGrades {
  label?: string;
}

let subClass: LabeledPastGrades;

subClass = new LabeledPastGrades(); // ok
subClass = new PastGrades(); //ok
```
***

### 8.5.3 Overridden Constructors p. 153
#### 8.5.3.1 Intro
* As with vanilla JS, subclasses are not required by TS to define their own constructor. 
* Subclasses (aka derived classes) without their own constructor implicitly use the constructor of their base class (aka superclass) using the *super* keyword.

#### 8.5.3.2 Examples p. 153-154
* **Example 1**, the constructor for the **PassingAnnouncer** derived class correctly calls the constructor fromt eh base class using a *number* argument, while the **FailingAnnouncer** gets a type error.

```typescript
class GradeAnnouncer {
  message: string;
  
  constructor( grade: number ) {
    this.number = grade >= 65
    ?
      "Maybe next time..."
    :
      "You pass!";
  }
}

class PassingAnnouncer extends GradeAnnouncer {
  constructor() {
    super( 100 );
  }
}

class FailingAnnouncer extends GradeAnnouncer {
  constructor() {}

  // Error: constructors for subclasses must contain
  // a 'super' keyword call.
}
```
* Per JS rules, the constructor of a subclass must call the base constructor before accessing **this** or **super**.
* TS will report a type error if it sees a *this* or a *super* bbeing accessed before **super()**.
* **Example 2**, the following **ContinuedGradesTully** class erroneously refers to *this.grades* in its constructor **before** calling to *super()*.

```typescript
class GradesTally {
  grades: number[] = [];

  addGrades( ...grades; number[] ) {
    this.grades.push(...grades);
    return this.grades.length;
  }
}

class ContinuedGradesTally extends GradesTally {
  constructor( previousGrades: number[] ) {

    // Error b/c this is called *before* super()
    this.grades = [...previousGrades]:

    super();

    // ok b/c this is called *after* super()
    console.log("Starting with length", this.grades.length);
  }
}
```

***
### 8.5.4 Overridden Methods p. 154
* Subclasses may redeclare new methods with the same names as the base class.
* Remember, since subclasses can be used wherever the original class is used, the types of the new methods must be usable in place of the original methods.
* Example on p 155:

```typescript
class GradeCounter {
  countGrades( grades: string[], letter: string ) {
    return grades.filter( grade => grade === letter ).length;
  }
}

class FailureCounter extends GradeCounter {
  countGrades( grades: string[] ) {
    return super.countGrades( grades, "F" );
  }
}

class AnyFailureChecker extends GradeCounter {
  countGrades( grades: string[] ) {

    // Error see full text on p. 155
    return super.countGrades( grades, "F" ) !== 0;
  }
}

const counter: GradeCounter = new AnyFailureChecker();

// Expected type: number
// Actual number: boolean

const count = counter.countGrades( ["A", "C", "F"] );
```
***

### 8.5.5 Overridden Properties p. 155
* Subclasses may explicitly redeclare properties of their base class with the same name, as long as the new type is assignable to the type on the base class.
* As with overridden methods, subclasses must structurally match up with base classes.

#### 8.5.5.1 Examples p. 155-156
* **Example 1**, the base class **Assignment** declares its *grade* to be of type `number | undefined`.
	* Meanwhile, the subclass **GradedAssignment** declares it as a `number` that must always exist.
	* Expanding the allowed set of values of a property's union type is not allowed, as doing so would make the subclass property no longer assignable to the base class property's type.

```typescript
class Assignment {
  grade?: number;
}

class GradedAssignment extends Assignment {
  grade: number;

  constructor( grade: number ) {
    super();
    this.grade = grade;
  }
}
```
* **Example 2**  (p. 156), **VagueGrade**'s *value* tries to add `| string` on top of the base class **NumericGrade**'s number type, causing a type error:

```typescript
class NumericGrade {
  value = 0;
}

class VagueGrade extends NumericGrade {

  // Error: Property 'value' in type 'NumberOrString'
  // is not assignable to the same property in base 
  // type 'JustNumber'.
  // Type 'string | number' is not assignable to type
  // 'number'. Type 'string' is not assignable to
  // type 'number'.

  value = Math.random() > 0.5
    ? 1: "...";
}

const instance: NumericGrade = new VagueGrade();

// Expected type: number
// Actual type: number | string
instance.value;
```

***

## 8/26/2024
## 8.6 Abstract Classes p. 156
### 8.6.1 Intro p. 156-158
* Sometimes, it's useful to create a base class that does not declare any methods; instead, it must rely on derived subclasses to provide methods.
* These are called **abstract classes**, and created using the *abstract* keyword in front of the class name and in front of any method intended to be abstract.

### 8.6.2 Examples p. 157-158
* In this example, the **School** class and its **getStudentTypes** method are marked as *abstract*.
* Its subclasses--**Preschool** and **Absence**--are therefore expected to implement *getStudentStypes()*.

```typescript
abstract class School {
  readonly name: string;

  constructor( name: string ) {
    this.name = name;
  }

  abstract getStudentTypes(): string[];

}

class Preschool extends School {
  getStudentTypes() {
    return ["preschooler"];
  }
}

// Error: nonabstract class 'Absence' does not
// implement inherited abstract member 'getStudentTypes'
// from class 'School'
class Absence extends School { }
```
* **An abstract class *cannot* be instantiated directly.**
	* This is because that abstract class does not have definitions for some methods that its implementation may assume do exist.
* Only nonabstract classes (aka **concrete class**) can be instantiated.
* Continuing the previous example, attempting to call a new **School** results in a TS type error b/c *School* is an abstract class:

```typescript
let school: School;

school = new Preschool("Signal Hill Day Care"); //ok

// Error!
school = new School("Burr's Lane Jr. High");
```
* Abstract classes are often used in frameworks where consumers are expected to fill out details of a class.
* The class may be used as a type annotation to indicate values must adhere to the class--as with the earlier example of **school: School**--but creating new instances must be done with subclasses.

***

## 8.7 Member Visibility p. 158
### 8.7.1 JS Intro and TS History p. 158
* JS includes the ability to start the name of a class member with the `#` pound sign to mark it as a **private** class member.
* Private class members may *only* be accessed by instances of that class.
* JS runtimes enforce that privacy by throwing an error if an area of code outside the class tries to access the private method or property.
* TS's class support predates the introduction of **'officially supported *true*' privacy by # prefix** by JS in [ES2022](https://www.w3schools.com/js/js_2022.asp#mark_private_methods).
* While TS supports private class members, it also allows a more nuanced set of privacy definitions on class methods and class properties.
* TS's member visibilities are achieved by adding one fo the following keywords before the declaration name of a class member:
	1. **public** (default)-- allowed to be accessed by anybody, anywhere
	1. **protected** -- allowed to be accessed only by the class itself and its subclasses
	1. **private** -- allowed to be accessed *only* by the class itself
* The above keywords exist purely within the type system.
* The keywords are *removed* along with other type system syntax when TS code is transpiled to pure JS.

### 8.7.2 Example 1 p. 159
* Here, the **Base** class declares two *private* members, one *protected* and one *private*. It also has one 'true' private member using ES2022 native JS syntax **#truePrivate**.
* **Subclass** is allowed to access the *private* and *protected* members but not the **private** or **#truePrivate** members.

```typescript

class Base {
  isPublicImplicit = 0;
  public isPublicExplicit = 1;
  protected isProtected = 2;
  private isPrivate = 3;
  #truePrivate = 4;
}

class Subclass extends Base {
  examples() {
    this.isPublicImplicit; // ok
    this.isPublicExplicit; // ok
    this.isProtected; // ok

    // Error: Property 'isPrivate' is private
    // and only accessible within class 'Base'
    this.isPrivate;
    
    // Error: Property '#truePrivate' is private
    // and only accessible within class 'Base'
    this.#truePrivate;
  }
}

new Subclass().isPublicImplicit; //ok
new Subclass().isPublicExplicit; //ok

new Subclass().isProtected; //Error
new Subclass().isPrivate; //Error
```
* The key difference between TS's member visibilities and JS's true private declarations is that TS's exist only in the type system whereas JS's private declarations persist in the JS runtime.
* A TS class member declared as *protected* or *private* will compile to the same JS as if it were declared *public* explicitly or implicitly.
* As with interfaces and type annotations, **visibility keywords are erased when outputting JS.
* **Only `#private` fields are truly private in runtime JS.** 

***
### 8.7.3 Example 2 p. 160
* Visibility modifiers may be marked along with *readonly*. To declare a member both as *readonly* and with an explicit visibility, the visibility comes **first**.
* This **TwoKeywords** class declares its *name* member as both *private* and *readonly*.

```typescript
class TwoKeywords {
  private readonly name: string;

  constructor() {
    this.name = "Anne Sullivan"; // ok
  }

  log() {
    console.log( this.name ); // ok
  }
}

const two = new TwoKeywords();

// Error: Property 'name' is private and
// only accessible within class 'TwoKeywords'
// Error: Cannot assign to 'name' bc
// it is a read-only property
two.name = "Savitribai Phule";
```
* Note that it is *not* permitted to mix the old TS member visibility keywords (**public**, **protected**, **private**) and the official ES2022 **#private** fields.
	* Private fields are always private by default--so there is no need to additionally mark them with the old TS **private** keyword.

### 8.7.4 Static Field Modifiers p. 161



***

## 8.8 Summary of Chapter 8 p. 161

***

# Chapter 9: Generics




***
## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.

`<script>`
