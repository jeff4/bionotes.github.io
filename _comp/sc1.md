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

12/29



