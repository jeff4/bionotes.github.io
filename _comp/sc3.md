---
title: Scheme 3 - SICP Notes
permalink: /sc3/
sitemap: false
---


***
## 12/31/2024
* Using official/unofficial PDF of Second Edition by Harold Abelson, Gerald Jay Sussman, and Julie Sussman, last updated in 1996. Digital copy was updated around 2010 with latest and best typography.
* PDF edition runs to 855 pages
* Finished page 13, in the middle of the 1.1.3 Evaluating Combinations section which starts on p. 12.
 
***

## 1/05/2024
### 1.1.7 Example: Square Roots by Newton's Method
* p. 28. Define square root mathematically. For **input x**, *output **y*** = **&#8730;x** where **y** must be 0 or positive and y<sup>2</sup> = x.
* This describes a perfectly legit math function. However, this declarative description does not describe any procedure for calculating output *y*.
* Let's examine this pseudo-Lisp:

```lisp
(define (sqrt x)
  (the y (and (>= y 0)
              (= (square y) x)
         )
  )
)
```
* This only begs the question.
* The contrast between function (declarative?) and procedure is a reflection of the general distinction between describing *properties* of things describing *how* to do things is sometimes referred to the distinction between **declarative knowledge** and **imperative/procedural knowledge**
* In math, we are usually concerned with a declarative (*what is*) description; in CS, we are usually concerned with the imperative (*how to*) descriptions.
* How does one compute square roots?
* The most common way is to use Newton's method of successive approximations which says that whenever we have a guess *y* for the value of the square root of a number *x*, we can perform a simple manipulation to get a better guess (one closer to the actual square root) by averaging *y* with *x/y*.
* For example, we can compute the square root of 2 as follows. (See table on p. 29)
* Suppose our initial guess is 1 using a less general version of Newton's Method (it's actually Heron of Alexandria's method from the first century A.D.)

## 1/06/2025
* Let's formalize Newton's method for finding sq. roots using procedures.

```scheme
(define (sqrt-iter guess x)
  (if (good-enough? guess x)
    guess
    (sqrt-iter (improve guess x)
      x
    )
  )
)
```
* A guess is improved by averaging it with the quotient of the radicand and the old guess:

```scheme
(define (improve guess x)
  (average guess (/ x guess)
  )
)

;where

(define (average x y)
  (/ (+ x y) 2)
)
```
* We also have to say what we mean by *good enough*. Let's try this below but we should see Exercise 1.7 for a better version.

```scheme
(define (good-enough? guess x)
  (< (abs
       (- (square guess) x))
       0.001
  )
)
```
* Finally, we need a way to get started. What is the seed/initial value or initial guess? This is the code if intial **guess = `1.0`**:

```scheme
(define (sqrt x)
  (sqrt-iter 1.0
    x)
)
```

* If we type these definitions to the interpreter, we can use **sqrt** just as we use any procedure. Examples calling the **sqrt** function:

```scheme

(sqrt 9)
; output: 3.00009155413138
```

* more examples on p. 31
* See [ChatGPT explanation of this code](https://chatgpt.com/share/677cd1e0-4878-8013-bcd6-1976bda93702), generated on 1/06/2025
