---
title: Notes on Scheme and Lisp
permalink: /sc1/
sitemap: false
---


***


## General Lisp Notes
* YouTube 2019 Linux Conf.Au lecture ["Lets LISP like it's 1999"](https://youtu.be/hGY3uBHVVr4?si=zyiLMY61npZlMcgW&t=1950)
* 2018 BP Learning ["Intro to Scheme Programming"](https://youtu.be/6k78c8EctXI?si=-d467ZmuYGpqPkVr)

***

# BP Learning
## 12/27/2024
* **6:23** - comparison with other languages. Page count of how long each language specification is for Scheme, vs. C, C++, Java, C#, JS.  
	* Most of those specs do not include libraries. Closest is C at 176 pages
	* Scheme comes in under 50 pages, which includes the standard libraries
* **8:30** Two models for programming: Turing Machines and Lambda Calculus.
	* They can accomplish all the sam things, but operate very differently. 
* **9:15** A lot of people think of Scheme as a functional programming language. That's technically *not* true because functional programming languages do not allow assignments but Scheme does.
	* Most Scheme programmers try to mostly avoid using assignments but it is not completely forbidden.
* Scheme is standardized through **R*n*RS** where *n* refers to an integer. Full name is Revised<sup>n</sup> Report on the Algorithmic Language Scheme.
	* For more, see the [Standardization section](https://en.wikipedia.org/wiki/History_of_the_Scheme_programming_language#Standardization) of the [wiki page](https://en.wikipedia.org/wiki/History_of_the_Scheme_programming_language) on the history of Scheme.
	* The latest large standard is [R<sup>6</sup>RS](https://www.r6rs.org), ratified in 2007.
	* The latest small revision is called [R<sup>7</sup>RS](https://r7rs.org) from 2022. The [R<sup>7</sup>RS website](https://www.r6rs.org) contains PDF and [html versions](https://standards.scheme.org/corrected-r7rs/r7rs.html) for the R<sup>7</sup>RS spec.
	* As of 2018, most people use and know R<sup>5</sup>RS from the mid 1990s. This talk is based on R5.
* **10:20** Originally, Brendan Eich planned to use Scheme as the programming language for the web browser. That's why JavaScript borrows a lot from Scheme.
	* Originally, Eich was hired by Netscape to implement Scheme, but b/c of Netscape's biz dev deal with Sun / Java, they rebranded and changed the syntax what eventually became ECAMScript to resemble Java.
* **11:15** Why should we learn scheme?
	* Some of the best books ever published on programming use Scheme	
	* Scheme expands one's imaginatin on relationship between code and data, how does programming really work, what is the purpose of syntax, how do you make something powerful without too much clutter, how does one pare down features to a minimal set?

## Scheme Syntax
* **13:08**
* Goal of Scheme is to have as minimal syntax as possible. 
* Basic procedure call uses *prefix'd* **function** followed by *n* number of *arguments*.
	* Procedures can have dashes inside
	* There are no in-fix operators like simple math operators **+**, **-**, **x**, **/**, etc. Or more accurately, these operators exist but only as prefix operators that come *first* before the arguments
    * Benefit is that this is that [Polish Notation](https://en.wikipedia.org/wiki/Polish_notation) means that one can have unary, binary, ternary, or arbitrarily large number of arguments without getting tangeled up with how does one wrangle with the syntax of binary operators like **+**.

## If statements (15:03)

```scheme
(if
  condition-check-procedure
  then-procedure
  else-procedure
)
```

### Example
```scheme
(if (< x 3)
  (display "I am a number less than 3")
  (display "I am a number that is 3 or greater")
)
``` 

* Note: **`<`** is a procedure call, it is *not* an infix operator, followed by arguments **`x`** **`3`**

***

## 12/29/2024
## Basic Syntax: Lists of Values
* **15:18** Everything in Scheme is a list, even the code.
* Use a **single quote** in front of a group of values to specify that it is a list instead of a procedure call. 
	* Note that Scheme refers exclusively to functions as **procedures**. For more on this plus similarities/differences with Haskell, see [ChatGPT](https://chatgpt.com/share/6771e4ba-6388-8013-a730-2a23f4244dc5)
* **17:30** Try some REPLs at this online [Scheme playground](https://try.scheme.org):

```scheme
(define x '(1 2 3))
(car x) ;; output: 1
(cdr x) ;; output: (2 3)
```
 
* Legacies of developing LISP on the [IBM 704](https://en.wikipedia.org/wiki/IBM_704)
* `car` = Contents of Address part of the Register
* `cdr` = Contents of Decrement of the Register
* `cons` used to *construct* lists, e.g. this single line `(cons 1 (cons 2 (cons 3 '())))` outputs this: **(1 2 3)**.
	* Note that one must first *create* an empty list with `()`, and then add elements (starting with 3, then 2, then 1) to that empty list.
* Local variables are generated with the **`let`** command. 
* **18:10** There are many types of **`let`** commmands, the most common is **`let*`**
	* Other variants: vanilla **let**, **letrec**, etc.

## Basic Syntax: Creating a function with Lambda

```scheme
(lambda
  parameter-list
  function-body
  more-function-body
  ...
)
```
* The last expression evaluated is the return value of the function.
* Lamdbda functions are *'born anonymous*, but can be assigned names using *let*, *set!*, or *define*.
* Examples of procedures that multiply by 2x, using *define*, *let*`+ local variable, etc.
* 

## Misc Synatax
* Empty list `'()`
* Booleans `#t` for **true**; `#f` for **false**
* Functions that yield side-effects are marked with a **`!`**, e.g,. `set!` modifies a variable.
* single line comments begins and goes through EOL using the semicolon **`;`**.

## Recursion. 
* **20:35** Scheme really wants you to use recursion instead of iteration.
	* All routines can be written nested of the same procedure (aka **recursively**) *or* using the `while` loop (aka iteratively/procedurely)
	* Maybe better way of thinking about recursion is saying *a function calls itself*.
* Procedural routines talk about the *method* of how something is done
* In contrast, recursive routines talk about the *logic* of how something is done
* Scheme emphasizes the focus on logic and makes everything recursive.
* **21:20** A Scheme program usually does 3 things:
	1. Check to see if you are done
	1. Perform a single task well
	1. Narrow a bigger task to a smaller task
* **22:00** By encapsulating into a recursive programs, we can:
	1. Eliminate problems with variables that we left or forgot to set
	1. Explicitly mark **control-handling** vs. **task-handling** even for non-standard flows
	1. Create a function which is more easily proven to be correct, since all in-flows and out-flows are marked
* **22:37** Example of a program that eats 100 apples. Comparison of procedural vs. recursive implementation 
* **24:33** Tail Call elimination and why recursion in Scheme is *not* expensive
	* scheme was the first programming language to introduce tail-call elimination
	* TC-elimination does **not** eat stack space. Stops the explosion in the call stack that comes from repeated resursive calls. The recursive version of the 100 apples program has a *constant* stack size
	* eliminates many tradeoffs between writing elegant code (well-structured, easy to understand) versus optimized code (performant/efficient)
* **26:06** Poorly formatted table that shows programming languages that support tail calls (scheme, scala, f#, lua, **JS *after* ES6** and for Safari only), those that don't (C#, Java, Python, JS *before* ES6). And it depends for Lisp overall, C, and Obj-C.
