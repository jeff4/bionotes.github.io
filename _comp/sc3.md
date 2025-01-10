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

***

## 1/08/2025
* Refactored with clearer procedure/function names:

```scheme
; function f1
(define (f1-sqrt-iter guess x)
  (if (f4-good-enough? guess x)
    guess
    (f1-sqrt-iter (f2-improve guess x)
      x
    )
  )
)

; function f2
(define (f2-improve guess x)
  (f3-average guess (/ x guess)
  )
)

; function f3
(define (f3-average x y)
  (/ (+ x y) 2)
)

; function f4
(define (f4-good-enough? guess x)
  (< (abs
       (- (square guess) x))
       0.0001
  )
)


; function f5 -- main() function
(define (f5-sqrt x)
  (f1-sqrt-iter 1.0
    x)
)
```

* Verified program output using https://try.scheme.org --

```scheme
(f5-sqrt 2)
1.4142156862745097

(f5-sqrt 3)
1.7320508100147274

(f5-sqrt 4)
2.0000000929222947

(f5-sqrt 5)
2.2360688956433634

(f5-sqrt 6)
2.4494943716069653

(f5-sqrt 7)
2.64576704419029

(f5-sqrt 8)
2.8284271250498643

(f5-sqrt 9)
3.000000001396984

(f5-sqrt 10)
3.162277665175675
```

* Let's reimplement these functions in Haskell:

```haskell
-- function f1
f1_sqrtIter :: Double -> Double -> Double
f1_sqrtIter guess x
  | f4_goodEnough guess x = guess
  | otherwise             = f1_sqrtIter (f2_improve guess x) x

-- function f2
f2_improve :: Double -> Double -> Double
f2_improve guess x = f3_average guess (x / guess)

-- function f3
f3_average :: Double -> Double -> Double
f3_average x y = (x + y) / 2

-- function f4
f4_goodEnough :: Double -> Double -> Bool
f4_goodEnough guess x = abs ((guess * guess) - x) < 0.0001

-- function f5 -- main function
f5_sqrt :: Double -> Double
f5_sqrt x = f1_sqrtIter 1.0 x
```
* Call the program by entering into GHCi: `f5_sqrt x` where *x* = input number. e.g `f5_sqrt 49` gives output `7.000000141269659`.

***

## 1/09/2025
### 1.1.8 Procedures as Black-Box Abstractions
* p. 33 **sqrt** is our first example of a process defined bya  set of mutually defined procedures.
* Note that the definition of **f1-sqrt-iter** is recursive (in Haskell version, **f1_sqrtIter**).
* The idea of recursion is a bit alien/disturbing. See Section 1.2 for more.
* See Figure 1.2 on p. 34 for decomposition / analysis of the parts of the **f5-sqrt** program.
	* Note that **square()** and **abs()** are procedures that come for free with Scheme. The rest are marked with new custom procedures, reading from top to bottom.
	* f5-sqrt
		* f1-sqrt-iter
			* f2-improve
				* f3-average
			* f4-good-enough
				* square()
				* abs()

#### 1.1.8.1 Local Names
* Importance of having local variable names that don't "bleed" into other contexts (aka *scopes*).
* p. 36 'A formal parameter of a procedure has a very special role in the procedure definition, in that it doesn't matter what the name the formal parameter has.
	* 'Such a name is called a **bound variable**; the procedure definition **binds** its formal parameters.
	* 'The meaning of a procedure definition is unchanged if a bound variable is consistently renamed throughout the defintion.'
* p. 37 'If a variable is *not* bound, we call that a **free variable**.' 

### up to page 55
* Big O Notation, aka capital Theta notation.
* 1/10/2025
