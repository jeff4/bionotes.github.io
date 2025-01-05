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

