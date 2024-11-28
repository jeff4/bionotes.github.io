---
title: HMC - Haskell MooC
permalink: /hmc/
sitemap: false
---


***

# HMC - New Page
* [Haskell Mooc Course](https://haskell.mooc.fi/)

***

## General Haskell Notes
* 11/03/2024 [Reimplementation of unix core utilities](https://github.com/Gandalf-/coreutils) in Haskell. [HN thread](https://news.ycombinator.com/item?id=41992270) with comments by [repo owner Austin](https://github.com/Gandalf-).
	* Austin has some [posts](https://www.anardil.net/tag/coreutils.html) on his blog discussing his work.
	* Austin is [answering questions](https://news.ycombinator.com/item?id=42032718) in the HN thread.

***

# Haskell mooc
# Lecture 1
## From 1.3.3 Uses of Haskell
* Examples of where Haskell is used can be found on [The Haskell Wiki](https://wiki.haskell.org/Haskell_in_industry) and [this 2022 blog post](https://serokell.io/blog/top-software-written-in-haskell)

## 1.6 Expressions and Types
* **Expressions** and **Types** are core to Haskell. Unlike Python, Java, C, etc., there are *no statements*.
* An expresssion must have a **value** and a **type**.
* From 1.6.1 Syntax of Expressions. Note how `function()` calls in C/Java/... assume input arguments. Whereas in Haskell, one simply uses spaces to separate a function and it's following list of parameters. 
	* C: `f(1)`; Haskell equivalent: `f 1`.
	* C: `f(1,2)`; Haskell equivalent: `f 1 2`.
* Example of how function calls bind tighter than operators; aka functions take precedence over operators, like how multiplication binds tighter than addition in algebra.
	* C: `a+b`; Haskell: `a+b`
	* C: `f(a) + f(b)`; Haskell: `f a + f b`
	* C: `f( a + g(b))` ; Haskell: `f( a + g(b) )`
* **NOTE:** function application *associates left*. 
* 1.6.2 Syntax of Types
	* **Int** is a signed 64bit number; **Integer** is an unbounded number type
	* **Double** is a floating point number
	* **Bool** true/false
	* **String** is an array of chars **[Char]**. In Section 1.6.3, they poit out that **String** and **[Char]** are synonyms and can be used interchangeably.

## 1.7 Golden Ratio Exercise (Structure of a Haskell Program)
* Created **Gold** module stored in `Gold.hs` file. Ran with both `runghc Gold.hs` and `stack runhaskell Gold.hs` and verified it works.
	* Note that executing the `stack` command kicked off an install process to the latest version of GHC.

## 1.8 Working with Examples
* For a simple one-line command, you can just paste it into **ghci** (Glasgow Haskell Compiler - Interactive).
* If one wants to cut and paste in multiple lines into **ghci**, use the `:{` and `:}` syntax and paste in between.
* Of course, one can use `:load` aka `:l` to load a file to run within **ghci**.
* Note there are two types of *division* operators: `/` and `div`, connected to `Num` and `Fractional`. More explanation of this when they discuss **type classes**.

## 1.9 Basic Structures
### 1.9.1 Conditionals instead of `if` statement.
* In languages like Java, **if** is a *statement*. If it doesn't have a value, it just *conditionally* executes other statements.
* In Haskell, **if** is an expression; it must have a value. It must select between 2 other expressions. It corresponds to the `?:` operator in C or Java. Let's express this in 3 languages

#### 1.9.1a Java
```java
int price = product.equals("milk") ? 1 : 2;
```

#### 1.9.1b Python
```python
price = 1 if product == "milk" else 2
```

#### 1.9.1c Haskell
```haskell
price = if product == "milk" then 1 else 2
```

***

## 10/24/2024

#### 1.9.1.1 Functions returning Bool
* In order to write **if** expressions in Haskell, one needs to know how to get values of type **Bool**. 
* The most common way is *binary* (aka accepts 2 arguments as input) comparison operators like:
	* **==** equal to 
	* **<** less than
	* **<=** less than or equal to
	* **>** greater than
	* **>=** greater than or equal to
* One oddity is that Haskell uses **`/=`** rather than the more commonly used **`!=`** operator for the *not-equals* operator.
* And of course, one can get **Bool** output values as a result of these operators:
	* **`&&`** logical *and*
	* **`||`** logical *or*
	* **`not`** function

### 1.9.2 Local Definitions
* For now, both the `let...in` and `where` constructs can be used interchangeably for small local variables.

### 1.9.3 A Word about Immutability
* Note that all "variables" in Haskell are more properly called **defintions** because they are immutable. 
* They are *not* just like a box that can contain some value like in many other programming languages.
* This is why idioms like **`i++`** will **not** work in Haskell.
* JH: I think Haskell "variables" (really, definitions), are similar to modern JavaScript variables declared by the **`const`** keyword. although that only prevents reassignment of the variable, but the value itself is changeable. Perhaps from the `Object.freeze()` and a recursive function like the below invented **`deepFreeze()`** function which is a recursive version of `Object.freeze()`:

```javascript
function deepFreeze(obj) {
  Object.freeze(obj);
  for (const key in obj) {
    if (typeof obj[key] === "object" && obj[key] !== null) {
      deepFreeze(obj[key]);
    }
  }
  return obj;
}

const myObj = {
  name: "Alice",
  address: { city: "New York" },
};

deepFreeze(myObj);
myObj.address.city = "Los Angeles"; // This will have no effect.
```

* Note that **shadowing** is when local definitions 'shadow' the names of variables defined elsewhere.
* Shadowing creates a new variable within a more restricted scope that uses the same name as some variable in the outer scope. See here for an example.
* **It is best to always choose new names for local variables so that shadowing never happens.** This way, the reader of the code will understand where the variables are used in an expression come from. See example.

***

## 10/25/2024

### 1.9.4 Pattern Matching
* The definition of a function can consist of multiple **equations**.
* The equations are matched in order against the arguments until a suitable one is found.
* This is called *pattern matching*.
* Consider this example:
```haskell
greet:: String -> String -> String
greet "Finland" name = "Hei, " ++ name
greet "Italy"   name = "Ciao, " ++ name
greet "England" name = "How do you do, " ++ name
greet _         name = "Hello, " ++ name
```
* The function `greet` generates a greeting given a country and name (which are both strings). 
* There is a special case for 3 countries: Finland, Italy, and England, and default case for everywhere else.
* I had to modify this code to work via `runghc Hello.hst` with a `main = doprint` construct because I wasn't using Prelude. Probably works better if I modify this to work in ghci.

#### 1.9.4a the _ pattern
* In any case, the **`_`** is a special pattern that matches anything. Be careful to place it as the **last case** b/c it will search for everything. Which can be a problem if you use this as one of the early/middle cases.

#### 1.9.4b the SHOW function from the standard library
* `show True` echoes back a variable value which is the bool **True**.
* Similarly `show 3` prints the number type **3**.
* Consider this simple example:
```haskell
describe :: Integer -> String
describe 0 = "zero"
describe 1 = "one"
describe 2 = "an even prime"
describe n = "the number " ++ show n
``` 
* Let's try running the above interactively in ghci: 
	1. Invoke ghci
	1. Use the multiple line command **`:{`** 
	1. Paste in the above commands 
	1. Close the block with **`:}`**. 
* Now, you can invoke the `describe` function as shown below, which should return the following output interactively.
```
ghci> describe 0
"zero"
ghci> describe 1
"one"
ghci> describe 2
"an even prime"
ghci> describe 82432
"82432"
```

#### 1.9.4c Reimplementation of the unicorn73 login password from before
* More efficient using pattern matching and the (**`_`**) pattern.

***

## 10/26/2024
### 1.9.5 Recursion
* [Link to section of the lecture](https://haskell.mooc.fi/part1#how-do-i-get-anything-done)
* In Haskell, many loops are implemented with recursion rather than the `for-loop` and `do-while` loops from Python, C/Java/similar languages.
* Here is the first recursive function which computes a factorial.
```haskell
factorial :: Int -> Int
factorial 1 = 1
factorial n = n * factorial (n-1)
```
* Paste this into **ghci**, where **==>** indicates what the expected output to be. Internal logic of what's happening:
```
factorial 3 becomes
3 * factorial (3-1)
3 * factorial (2)
3 * 2 * factorial (1)
3 * 2 * 1
FINAL OUTPUT: 6
```
#### 1.9.5a JH Explanation of factorial code
1. There is a case statement asking: Is the input argument **n** an integer that equals 1? 
	* If yes, then output = 1.
	* If no, then output = **n** times recursive function factorial(**n** - 1).
2. In the above case, **n = 3**. This means:
	* **n = 3**, which is *not* equal to 1. So therefore...
	* factorial 3 = **n** times factorial (**n minus 1**)
1. This simplifies to **3** times factorial (**3 - 1**) 
1. Which simplifies to **3** times factorial (**2**) 
1. Which simplifies to **3** times [ **2** times factorial (**2 minus 1**) ]
1. Which simplifies to **3** times [ **2** times factorial (**1**) ]
1. Now note that `factorial (1)` in the above expression is a case statement where if n=1, then output of factorial(1) = 1. So we can rewrite Step 6 above as:
	* **3** times [ **2** times **1** ].
1. 3 * 2 * 1 = **`Final answer = 1`**.

* When one tries to evaluate `factorial(-1)`, get this error:

```
<interactive>:8:11: error:
    • No instance for (Num (Int -> Int)) arising from a use of ‘-’
        (maybe you haven't applied a function to enough arguments?)
    • In the expression: factorial - 1
      In an equation for ‘it’: it = factorial - 1
```

***

## 10/28/2024
* Used pen and paper to work out the *internal logic* steps listed above from 10/26. Very interesting. In contrast, this is the implementation in JavaScript...

```javascript
function factorial(n) {
  // Check for invalid input
  if (n < 0) {
    return "Factorial is not defined for negative numbers";
  }

  // Base case
  if (n === 0 || n === 1) {
    return 1;
  }

  // Recursive case
  return n * factorial(n - 1);
}

console.log(factorial(5)); // Output: 120
```

***

#### 1.9.5b SquareSum example
* **squareSum** is a function that calculates: **1 squared** + **2 squared** + **3 squared** + **...** + **n squared** 
	* *aka*
**1<sup>2</sup> + 2<sup>2</sup> + ... + n<sup>2</sup>**
```haskell
squareSum 0 = 0
squareSum n = n^2 + squareSum (n-1)
```
* Output is:

```
ghci> squareSum 1
1
ghci> squareSum 2
5
ghci> squareSum 3
14
ghci> squareSum 4
30
ghci> squareSum 5
55
```

***

#### 1.9.5c Fibonacci Sequence Intro
* **Definition:** *The Fibonacci Sequence starts with `1,1`. To get the next element of the sequence, sum the previous two elements of the sequence.*
* First several elements: **1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, ...**

***

#### 1.9.5d Fibonacci Sequence (Slow Version)
* Compare to **2.1.2c Fibonacci Sequence (Fast Version)** below.
* **`fib`** is a recursively called function in the below.

```haskell
fibonacci 1 = 1
fibonacci 2 = 1
fibonacci n = fibonacci ( n-2 ) + fibonacci ( n-1 ) 
```

#### 1.9.5e Fib Sequence in JavaScript
* From [this page](https://www.geeksforgeeks.org/javascript-program-to-print-fibonacci-series/), there are multiple ways of implementing the Fibonacci sequence in JS.
* Here is the implementation using a for-loop:

```javascript
function fibonacci(num) {
  let num1 = 0;
  let num2 = 1;
  let sum;
  if (num === 1) {
    return num1;
  } else if (num === 2) {
    return num2;
  } else {
    for (let i = 3; i <= num; i++) {
      sum = num1 + num2;
      num1 = num2;
      num2 = sum;
    }
      return num2;
    }
}

console.log("Fibonacci(5): " + fibonacci(5));
console.log("Fibonacci(8): " + fibonacci(8));
```

* A more apples-to-apples comparison uses recursion in JS:

```javascript
function fibonacci(num) {
  if (num == 1)
    return 0;
  if (num == 2)
    return 1;
  return fibonacci(num - 1) + fibonacci(num - 2);
}

console.log("Fibonacci(5): " + fibonacci(5));
console.log("Fibonacci(8): " + fibonacci(8));
```

#### 1.9.5f Tree-like visualization of Haskell Fibonacci function
* Consider the slow but easily understandable recursive tree-like structure generated by the v1 implementation of Fibonacci.

***

## 10/29/2024
## 1.10 All Together Now!
* Finally, here is a complete Haskell Module that uses **if**s, **pattern matching**, **local definitions**, and **recursion**.
* This module concerns the [Collatz conjecture](https://en.wikipedia.org/wiki/Collatz_conjecture).
	* From 2017, [Numberphile video](https://youtu.be/5mFpVDpKX70?si=1mX4OHXAAtwb6BRJ). About 10 minutes long.
	* 2021 YouTube video (22:00 long) by [Veritasium](https://youtu.be/094y1Z2wpJg?si=5reUvOalF71cBhY4)
* Played around with using **f_** as a prefix denoting functions. Initial digits and initial underscore don't work. Also, initial capitalization like **F_function** doesn't seem to work.
* Complete Haskell program labelled *Collatz_b.hs*. Note that one can independently call any of the three functions: 
	1. **f1_step:** Given a positive integer as input, this function will output the next step in the Collatz sequence. If the input integer *x* is even, output integer = *x/2*. If the input integer *x* is odd, output integer = *3x+1*.
	1. **f2_collatz:** Given a positive integer as input, this function will output the number of steps needed to turn that postive integer into 1 using the Collatz sequence. e.g., **f2_collatz 20** outputs **`10`** which means there are 10 numbers from 20...1. Specifically, 20, 10, **5**, 16, 8, 4, 2, 1. (Odd members of the sequence are listed in **bold**. In this case, only **5** is bold; every other member leads to x/2 in the next step.) If we count that how many numbers are in that sequence (including 20 at the beginning and 1 and the end), we get **10**.
		* Similarly, **f2_collatz 97** outputs **`118`** because it takes 118 steps to get from 97 to 1. 
	1. **f3_longest:** Given a positive integer as an input, this function returns the positive integer below that input that produces the longest Colltaz sequence, aka the *largest stopping time*, per [this section of the Wikipdia article](https://en.wikipedia.org/wiki/Collatz_conjecture#Empirical_data).
		* The largest stopping time for numbers below **10** is *9* which requires **19 steps**.
		* The largest stopping time for numbers below **100** is *97* which requires **118 steps**.
		* The largest stopping time for numbers below **1000** is *871* which requires **178 steps**.
		* The largest stopping time for numbers below **10,00** is *6171* which requires **261 steps**.
* Here is the program itself, using JH notation

```haskell

module Collatz_d where

-- Original program found at https://haskell.mooc.fi/part1#all-together-now
-- Modified to clarify functions with f1_ prefix
-- and clarify variables with a v1_ prefix

-- Function 'f1_step()' generates the next step in the Collatz sequence
f1_step :: Integer -> Integer
f1_step x = if even x then v_down else v_up
  where 
    v_down = div x 2
    v_up = 3*x + 1

-- Function 'collatz(x)' computes how many steps it takes for the Collatz sequence
-- to reach 1 when starting from x
f2_collatz :: Integer -> Integer
f2_collatz 1 = 0
f2_collatz x = 1 + f2_collatz (f1_step x)


-- Function longest() finds the number with the longest Collatz sequence for
-- initial values between 0 and upperBound
f3_longest :: Integer -> Integer
f3_longest upperBound = f4_longest_helper 0 0 upperBound


-- helper function for Function longest()
f4_longest_helper :: Integer -> Integer -> Integer -> Integer 

-- end of recursion, return longest length found
f4_longest_helper number _ 0 = number

-- recursion step: check if n has a longer Collatz sequence than the 
-- current known longest
f4_longest_helper number maxlength n = 
  if len > maxlength
  then f4_longest_helper n len ( n-1 )
  else f4_longest_helper number maxlength (n-1)
  where len = f2_collatz n

```

***

## 10/30/2024
## 1.11 Indentation
### Two main rules
1. Things that are grouped together start at the same column (depth in tabs/spaces).
1. if an expression or equation needs to be split into multiple lines, increase the indentation.

### General thoughts
* Indentation definitely matters, like in Python.
* Best to use spaces.
* If one can't get indentation to work at first, try putting everything onton one long line

***

### Example 1
```haskell
-- this is ok
i x = let y = x+x+x+x in div y 5

-- but this is better
j x = let y =  x+x
               x+x
      in div y 5
```

***

### Example 2
```haskell
-- this is ok
k = a + b
  where a = 1
        b = 1

-- but this is better
l = a + b
  where
    a = 1
    b = 1
```

***

### Example 3: bad
```haskell
-- indentation not increased even though
-- expression split on many lines
i x = let y = x+x+x+x+x+x
in div y 5
```

***

### Example 4: bad
```haskell
-- indentation not increased even though
-- expression is split
j x = let y = x+x+x
      +x+x+x
      in div y 5
```

***

### Example 5: bad
```haskell
-- grouped things are not aligned
k = a + b
  where a = 1
    b = 1
```

***

### Example 6: bad
```haskell
-- grouped things are not aligned
l = a + b
  where
    a = 1
      b = 1

```

***

### Example 7: bad
```haskell
-- where is part of the equation, so indentation needs to increase
l = a + b
where
  a = 1
  b = 1

```
***

## 11/01/2024
# Lecture 2: Either You Die a Hero...

## 2.1 Recursion and Helper Functions
* Often, you'll find you need helper variables in recursion to keep track of things.
* You can get them by defining a helper function with more arguments.
* Analogy: arguments of the helper function are variables you update in your loop.

### 2.1.1 First Example

#### 2.1.1a Java

```Java
public String repeat String( int n, String str) {
  String result = "";
  while (n>0) {
    result = result + str;
    n = n-1;
  }
  return result;
}

```



#### 2.1.1b Python

```python
def repeatString( n, str ):
  result = ""
  while n > 0:
    result = result + str
    n = n-1
  return result
```

* Validated that it works. To execute, copy and paste above into `repeat.py` file. Then invoke interactive python environment with this script loaded with **`python -i repeat.py`**.
* To execute, type something like **`repeatString(3, "Hello! ")`** which outputs `'Hello! Hello! Hello! '`.

#### 2.1.1c Haskell version 1

```haskell
repeatString n str = repeatHelper n str ""

repeatHelper n str result = if ( n==0 )
                              then result
                              else repeatHelper (n-1) str ( result ++ str )
```

#### 2.1.1d More notes
* Verified that the above works. Example usage: **`ghci> repeatString 5 "Abc"`** generates output `"AbcAbcAbcAbcAbc"`.
* You might have noticed that the above implementations in Java and Python look a bit weird because they use `do-while` loops instead of `for` loops.
* This simply makes for a more straightforward conversion to Haskell.
* Let's make a tidier Haskell (version 2) by using **pattern matching** rather than an **if** (version 1)

#### 2.1.1e Haskell version 2

```haskell
repeatString n str = repeatHelper n str ""

repeatHelper 0 _   result = result
repeatHelper n str result = repeatHelper ( n-1 ) str ( result ++ str )
```

***

### 2.1.2 Second Example: Fibonacci Numbers

#### 2.1.2a Java implementation

```Java
public int fibonacci( int n ) {
  int a = 0;
  int b = 1;
  while ( n>1 ) {
    int c = a+b
    a = b;
    b = c;
    n--;
  }
  return b;
}
```

***

#### 2.1.2b Python implementation

```Python
def fibonacci(n):
  a = 0
  b = 1
  while n>1:
    c = a+b
    a = b
    b = c
    n = n-1
  return b
```
* Validated that it works. To execute, copy and paste above into `fib.py` file. Then invoke interactive python environment with this script loaded with **`python -i fib.py`**.
* Within the python environment, enter sample commands like **`fibonacci(n)`** where **n** is an integer input. Will return the corresponding Fib number, e.g., for `n = 1, 2, 3, 4, 5, 6`, the output will respectively be **1, 1, 2, 3, 5, 8**.

***

#### 2.1.2c Fibonacci Sequence (Fast Version)
* Fast version of Fibonacci numbers
* Compare to **1.9.5d Fibonacci (Slow Version)** above.
* Primary function: **`f1_fib`**
* Helper function: **`f2_helper`**

```Haskell
f1_fib :: Integer -> Integer
f1_fib n = f2_helper 0 1 n

f2_helper :: Integer -> Integer -> Integer -> Integer
f2_helper a b 1 = b
f2_helper a b n = f2_helper b (a+b) (n-1)
```


***

## 11/14/2024
## 2.2 Guards
* One more piece of syntax
* Instead of the usual **`if...then...else`** syntax, esp. if there are multiple cases, we can use the **conditional definition** aka **guarded definition** structure.
* This is somewhat like pattern matching in that there are multiple equations.
* *But*, one can have arbitrary code which decides which equation to use. Exmple:
```haskell
f x y z
  | condition1 = result1
  | condition2 = result2
  | otherwise = miscellaneous_result
```
* Note that: *otherwise* is a haskell keyword.

### 2.2.1 Examples
* Here are some examples using guards.
* First off, we have a function that describes the given number.
	* Note how important it is ot have the **`Two`** case before the **`Even`** case.

```haskell
describe :: Int -> String
describe n
  | n==2        = "Two"
  | even n      = "Even"
  | n==3        = "Three"
  | n>100       = "Big!!"
  | otherwise   = "The number "++show n++" is odd and below 100."
```
* Here is a factorial, implemented with guards instead of pattern matching.
* Unlike the above pattern-matching version, this one does not loop forever when given negative inputs.
```haskell
factorial n
  | n<0         = -1
  | n==0        = 1
  | otherwise   = n * factorial (n-1)
```
* You can even combine guards with pattern matching.
* Here's an implementation of a simple age guessing game:
```haskell
guessAge :: String -> Int -> String
guessAge "Griselda" age
    | age < 47 = "Too low!"
    | age > 47 = "Too high!"
    | otherwise = "Correct!"
guessAge "Hansel" age
    | age < 12 = "Too low!"
    | age > 12 = "Too high!"
    | otherwise = "Correct!"
guessAge name age = "Sorry, please guess another name and age." 
```

***

## 11/15/2024
## 2.3 List

* So far, we've only worked with singleton values like numbers and booleans. 
* Minor exception of strings which contain multiple characters.
* However, we need to handle *data structures*.
* The basic Haskell data structure is the **list**.
* Lists are used to store multiple values of the same type; aka they are **homogenous**.
* Example of a list literal: `[0,3,4,1+1]`.
* A list *type* is written as `[Element]`, where *Element* is the type of the list elements. 
* Haskell lists are implemented as singly-linked lists. More on this topic later.
* More examples:
```haskell
[True,True,False] :: [Bool]
["Oui", "moi"] :: [String]
[] :: [a]       -- more about this later
[[1,2],[3,4]] :: [[Int]]    -- a list of lists
[1..5] :: [Int]             -- uses range syntax
                            -- value is [1,2,3,4,5]
```

### 2.3.1 List Operations
* The Haskell Standard Library comes with lots of functions that operate on lists.
* Here are some of the most important ones together with their types. (For now, imagine **a** represents *any list*.)
```haskell
head :: [a] -> a        -- returns the first element
last :: [a] -> a        -- returns the last element
tail :: [a] -> [a]      -- returns everything except the first element
init :: [a] -> [a]      -- returns everything except the last element
take :: Int -> [a] -> [a]   -- returns the n first elements
drop :: Int -> [a] -> [a]   -- returns everything except the n first elements
(++) :: [a] -> [a] -> [a]   -- lists are concatenated with the ++ operator
(!!) :: [a] -> Int -> [a]   -- lists are indexed with the !! operator
reverse :: [a] -> [a]       -- reverse a list
null :: [a] -> Bool         -- is this list empty?
length :: [a] -> Int        -- the length of a list
```
* Note: the last two operations (**`null`** and **`length`**) actually jave more generic types, but for now we are pretending that we can only use them on lists.
* Lists can be compared with the **`==`** operator.
* **String** is just an alisa for **`[Char]`** which means string is a list of characters. This means you can use all list operators on strings!
```
ghci> :t "testString"
output... "testString" :: [Char]
```
* Some list operations come from the module **`Data.List`**. You can import a module in code or in GHCi with the **import Data.List** syntax. Example
```
ghci> import Data.List
ghci Data.List> sort[1,0,5,3]
output... [0,1,3,5]
```

### 2.3.2 Examples
* Here are some examples of working with lists. In this case, instead of showing you output from GHCi, we just use the **`==>`** to illustrate what the expression evaluates to.

#### 2.3.2.1 Indexing a List

#### 2.3.2.2 Define a function that discards the 3rd and 4th elements using 'take' and 'drop'

#### 2.3.2.3 Rotating a list by taking the first element and moving it to the end

#### 2.3.2.4 Reversing a list with 'range' syntax

## 2.4 A Word About Immutability
* Because Haskell is pure, it means that a function cannot change (aka *change*) their inputs.
* Mutation is a side effect; Haskell functions are only allowed output via their return value.
* This means that Haskell list functions always return a new list.
* Consider this...

```
GHCi, version 9.4.8: https://www.haskell.org/ghc/  :? for help
ghci> list = [1,2,3,4]
ghci> reverse list
[4,3,2,1]
ghci> list
[1,2,3,4]
ghci> drop 2 list
[3,4]
ghci> list
[1,2,3,4]
```
* The above immutabiity of lists (and variables) in Haskell amy seem inefficient. But it turns out to be both performant and useful. More on this later.

***
## 11/17/2024
## 2.5 A Word About Type Inference and Polymorphism
* So what does a type like `head :: [a] -> a` mean?
* It means that given a list that contains elements of any type **a**, the return value will be of the same type **a**.
* In this type, *a* is called a *type variable*.
* Type variables are types that start with a lowercase letter like `a`, `b`, `newTypeVariable`. 
* A type variable means **a type that is not yet known**; aka *a type that could be **anything***.
* Through the process of *type inference* (aka *unification*), *type variables* can be transformed into **concrete types** (where *Int*, *Bool*, etc. are concrete types).

### 2.5.0a Examples of Type Inference
* Let's look at some examples.
* If we apply `head` to a list of booleans, type inference will compare the type of head's input argument `[a]`, with the type of the actual argument `[Bool]` and deduce that the `a` must be a `Bool`.
* This means that the return type of `head` will in this case also be a `Bool`.

```haskell
head :: [a] -> a
head [True, False] :: Bool
```
* The function `tail` takes a list, and returns a list of the same type.
* If we apply `tail` to a list of booleans, the return value will also be a **list** of booleans.

```haskell
tail :: [a] -> [a]
tail [True, False] :: [Bool]
```
* If types don't match, we get a type error.
* Consider the operator **`++`**, which requires 2 list of the same type, as we can see from its type `[a] -> [a] -> [a]`.
* If we try to apply `++` to: (1) a list of booleans, plus (2) a list of chracters; we will get an error. See console output here:

```
ghci> "What, " ++ "moi?"
"What, moi?"
ghci> [True, False] ++ [True, False]
[True,False,True,False]
ghci> [True, False] ++ "moi?"

<interactive>:3:18: error:
    • Couldn't match type ‘Char’ with ‘Bool’
      Expected: [Bool]
        Actual: String
    • In the second argument of ‘(++)’, namely ‘"moi?"’
      In the expression: [True, False] ++ "moi?"
      In an equation for ‘it’: it = [True, False] ++ "moi?"
ghci>
``` 

* Type inference is really powerful. It uses the simple process of **unification** to get us types for practically any Haskell expression.
* Consider the following two functions:

```haskell
f xs ys = [head xs, head ys]
g zs = f "Moi" zs
```
* We can ask GHCi for their types and see that what Haskell understands about the types for functions **f** and **g**.
* See console output from GHCi below:

```
ghci> :{
ghci| f xs ys = [head xs, head ys]
ghci| g zs = f "Moi" zs
ghci| :}
ghci> :tail f
unknown command ':tail'
use :? for help.
ghci> :t f
f :: [a] -> [a] -> [a]
ghci> :t g
g :: [Char] -> [Char]
ghci>
```
* Through type inference, Haskell has figured out that the two arguments to **`f`** must have the same type, since their heads get put into the same list.
* The function **g**, which fixed one of the arguments of **f** to a stringgets a *narrower* type.
	* Type inference has decided that the argument **zs** for **g** must *also* have a type **`[Char]`** (i.e., a list of *Char*'s).
	* Because otherwise, the type of **f** would *not* match the call to **f**.

### 2.5.1 Sidenote: Some Terminology
* In a type like **`[Char]`**, we call **Char** a *type parameter*.
* A type like the list type that needs a type parameter is called a *parameterized type*.
* The fact that a function like **head** can be used with  many different types of arguments is called *polymorphism*. 
* The **head** function is said to be *polymorphic*.
* Note: there are many forms of polymorphism, and this Haskell form--which uses **type variables**--is called **parametric polymorphism**.

### 2.5.2 Sidenote: Type Annotations
* Since Haskell has type inference, you don't need to give any type annotations.
* However, even though type annotations aren't strictly required, there are good reasons to add them:
	1. Type annotations act as documentation. 
	1. Type annotations act as assertions that the compiler checks to help you spot mistakes
	1. Type annotations let us give a narrower type to a function than Haskell might infer.
* A good rule of thumb is to give top-level definitions type annotations.

## 2.6 The Maybe Type
* In addition to the list type, Haskell has other parameterized types too.
* Let's look at a very common and useful one: the **`Maybe`** type.
* Sometimes, an operation doesn't have a valid return value (e.g., division by zero). We have a few options:
	* We can use an error value, like **`-1`**. This is a bit ugly, but not always possible.
	* We can throw an exception. This is impure.
	* In some other languages, we would return a special null value that exists in (almost) all types. However, Haskell does not have a `null` built into the language.
* The solution Haskell offers us instead is to change our return type to a **`Maybe`** type.
* This is pure, safe, and neat.
* The type **`Maybe a`** has two *constructors*: **Nothing** and **Just**.
* **Nothing is simply a constant.
* **Just** takes a parameter. See table in the [Mooc course, Section 2.6](https://haskell.mooc.fi/part1#the-maybe-type).
* We can think of **`Maybe a`** as being a bit like **`[a]`** except there can only be 0 or 1 elements, not more.
* Alternatively, one can think of **`Maybe a`** as introducing a null value to the type **`a`**.
	* On can analogize **`Maybe Integer`** as Haskell's equivalent to Java's **`Optional <Integer>`**.
* One can create **Maybe** values by either specifying **Nothing** or **Just someOtherVlaue**. For more, see console output in the [Section 2.6](https://haskell.mooc.fi/part1#the-maybe-type).

## 2.7 Sidenote: Constructors
* As you can see above, we can pattern match on **Just** and **Nothing**--which are the constructors of **`Maybe`**. 
* Other constructors include constructors for **Bool**--which are **True** and **False**.
* The next lecture introduces constructors for the list type.
* Constructors can be used just like Haskell values.
* **Note: constructors that have no input arguments are *simply constants*.** Examples: **Nothing** and **False** are just constants.

## 2.8 The Either Type
* Sometimes it would be nice if one could add an error message or something to **Nothing**.
* This is why we have the **Either** type. The **Either** type takes two type arguments. The type **Either a b** has 2 consturctors: **`Left`** and **`Right`**.
* Both take an argument; **`Left`** takes **a** and **`Right`** takes **b** 
* See examples in table in [Section 2.8](https://haskell.mooc.fi/part1#the-either-type).
* **Note: Haskell has a convention where `Left` is for errors and `Right` is for success**.
* Example here where the **readInt** function only knows a few numbers; it returns a descriptive error for all other numbers.

```haskell
readInt :: String -> Either String Int
readInt "0" = Right 0
readInt "1" = Right 1
readInt s = Left ("Unsupported string: " ++ s)
```

* Note: the constructors of `Either` are called `Left` and `Right` because they refer to the left and right *type arguments* of `Either`.
	* Notice how in **`Either a b`**, **a** is the left argument and **b** is the right argument.
	* Thus, `Left` contains a value of type `a` and likewise `Right` of type `b`.
* Another example:

```haskell
iWantAString :: Either Int String -> String
iWantAString (Right str)        = str
iWantAString (Left number)      = show number
```

* As you recall, Haskell lists can only contain elements of the same type. You can't have a list like: `[1, "foo", 2]`.
* However, one can use `Either` to represent lists that can contain two different types of values.
* Example, where we track the number of people in a lecture, with the possibility of adding an explanation if a value is missing:

```haskell
lectureParticipants :: [Either String Int]
lectureParticipants = [Right 10, Right 13, Left "lecturer was sick", Right 3]
```

## 2.9 The case-of Expression
* We've seen pattern matching in function arguments.
* But there's also a way to pattern match in an expression. e.g.,

```haskell
case <value> of <pattern> -> <expression>
             of <pattern> -> <expression>
```

* As an example, let's rewrite the **describe** example from lecture one using **case**.

```haskell
describe :: Integer -> String
describe 0 = "zero" 
describe 1 = "one" 
describe 2 = "an even prime" 
describe n = "the number " ++ show n 
```

* Can be reimplemented as:

```haskell
describe :: Integer -> String
describe n = case n of 0 -> "zero"
                       1 -> "one"
                       2 -> "an even prime"
                       n -> "the number " ++ show n
```

* A more interesting example is when the value we are pattern matching on is not a function argument. Parse country code into a country name; return 'Nothing' if code not recognized in this example:

```haskell
parseCountry :: String -> Maybe String
parseCountry "FI" = Just "Finland"
parseCountry "SE" = Just "Sweden"
parseCountry _ = Nothing

flyTo :: String -> String
flyTo countryCode = case parseCountry countryCode of Just country -> "You're flying to " ++ country
                                                     Nothing -> "Sorry, you're not flying anywhere"
```
* console output

```
ghci> flyTo "FI"
"You're flying to Finland"
ghci> flyTo "DE"
"Sorry, you're not flying anywhere"
ghci>
```

* One could write the **flyTo** function using a helper function for pattern matching instead of using the case-of expression.

```haskell
flyTo :: String -> String
flyTo countryCode = handleResult (parseCountry countryCode)
  where handleResult (Just country) = "You're flying to " ++ country
        handleResult Nothing        = "Sorry, you're not flying anywhere."
```

* In fact, a case-of expression can always be replaced by a helper function. Variant #1. Given a sentence, decide whether it is a statement, question, or exclamation

```haskell
sentenceType :: String -> String
sentenceType sentence = case last sentence of '.' -> "statement"
                                              '?' -> "question"
                                              '!' -> "exclamation"
                                              _   -> "not a sentence"
```

* Variant #2 which is like Variant #1 before but uses a helper function instead of case-of syntax:

```haskell
sentenceType sentence = classify (last sentence)
  where classify '.' = "statement"
        classify '?' = "question"
        classify '!' = "exclamation"
        classify _   = "not a sentence"
```

* Sample console output for either version of the **sentenceType** function.

***

## 11/19/2024
### 2.9.1 When to Use Case Expressions
* You might be asking "What is the point of having another pattern matching syntax?"
* Let's discuss some pros and cons
* First and most importantly, **case** expressions enable us to pattern match against *function outputs*. We might want to write an early morning motivational messages to get lazy Haskellers going:

```haskell
motivate :: String -> String
motivate "Monday"       = "Have a nice week at work!" 
motivate "Tuesday"      = "You're one day closer to weekend!" 
motivate "Wednesday"    = "3 more day(s) until the weekend!" 
motivate "Thursday"     = "2 more day(s) until the weekend!" 
motivate "Friday"       = "1 more day(s) until the weekend!" 
motivate _              = "Relax! You don't need to work today. :)" 
```

* Using a **case** expression, we can run a helper function against the argument and pattern match on the result:

```haskell
motivate :: String -> String
motivate day = case distanceToSunday day of
  6 -> "Have a nice week at work!"
  5 -> "You're one day closer to the weekend!"
  n -> if n > 1
       then show (n - 1) ++ " more day(s) until the weekend!"
       else "Relax! You don't need to work today!"
```

* Btw, here is a 3rd implementation using guards:

```haskell
motivate :: String -> String
motivate day
  | n == 6 = "Have a nice week at work!"
  | n == 6 = "You're one day closer to the weekend!"
  | n > 1 = show (n - 1) ++ " more day(s) until the weekend!"
  | otherwise = "Relax! You don't need to work today!"
  where n = distanceToSunday day
```

* Soon, we will see how to define **distanceToSunday** using equations and **case** expressions.
* Secondly, if a helper function needs to be shared among many patterns, then equations won't work. e.g.:

```haskell
area :: String -> Double -> Double
area "square" x = square x
area "circle" x = pi * square x
  where square x = x * x
```

* This won't compile because the **where** clause only appends in the **`circle`** case; so the **square** helper function is not available in the **`square`** case.
* On the other hand, we can write:

```haskell
area :: String -> Double -> Double
area shape x = case shape of
  "square" -> square x
  "circle" -> pi * square x
  where square x = x*x

```

* Third, **case** expressions may help to write more concise code in a situation where a (long) function name would have to be repeated multipe times using equations. 
* Consider this naive, wordy implementation:

```haskell
distanceToSunday :: String -> Int
distanceToSunday "Monday"       = 6
distanceToSunday "Tuesday"      = 5
distanceToSunday "Wednesday"    = 4
distanceToSunday "Thursday"     = 3
distanceToSunday "Friday"       = 2
distanceToSunday "Saturday"     = 1
distanceToSunday "Sunday"       = 0
```

* Compare with this more concise implementation using **case** isyntax:

```haskell
distanceToSunday :: String -> Int
distanceToSunday d = case d of
  "Monday"      -> 6
  "Tuesday"     -> 5
  "Wednesday"   -> 4
  "Thursday"    -> 3
  "Friday"      -> 2
  "Saturday"    -> 1
  "Sunday"      -> 0
```
* The above 3 benefits make the **case** expression a versatile tool in the Haskeller's toolbox.

## 2.10 Recap: Pattern Matching

## 2.11 Quiz

***
## 11/20/2024
# Lecture 3: Catamorphic
## 3.1 Functional Programming, At Last!
* In Haskell, a function is a value, just like a number or a list is. 
* Functions can be passed as parameters (arguments) just like 'regular variable' can be. 
* Consider this simple example, with function **applyTo1** which accepts as input a function of type **`(Int->Int)`**, applies it to the number **1**, and returns the result:

```haskell
applyTo1 :: (Int -> Int) -> Int
applyTo1 f = f 1
```

* Let's define a simple function of type `Int->Int` and see the function **applyTo1** i action.

```haskell
addThree :: Int -> Int
addThree x = x + 3

applyTo1 addThree
  ==> addThree 1 -- output
  ==> 1 + 3 -- output
  ==> 4 -- output
```

* Let's go back to the type annotation for `applyTo1`

```haskell
applyTo1 :: (Int -> Int) -> Int
```

* The parentheses are needed because the type **Int -> Int -> Int** would be the type of a function taking two **Int** arguments. More on this later.

***

* Let's look at a slightly more interesting example. This time, we'll implement a polymorphic function `doTwice`.
* Note how we can use it various types of values and functions.


```haskell
doTwice :: (a -> a) -> a -> a
doTwice f x = f(f x)

doTwice addThree 1
  ==> addThree (addThree 1) -- output
  ==> 7 -- output
doTwice tail "abcd"
  ==> tail (tail "abcd") -- output
  ==> "cd" -- output
```

* More

```haskell
makeCool :: String -> String
makeCool str = "WOW" ++ str ++ "!"

doTwice makeCool "Haskell"
  ==> "WOW WOW Haskell!!" -- output
```

***
## 11/21/2024
### 3.1.1. Functioal Programming on LIsts.
* That was a bit boring. Luckily there are many useful list functions that take functions as arguments.
* By the way, functions that take functions as arguments (or return functions) are often called *higher-order functions*.
* The most famous of these list-processing higher-order functions is *map*.
* It gives you a new list by applying the given function to all elements of a list.

```haskell
map :: (a -> b) -> [a] -> [b]
map addThree [1,2,3]
  ==> [4,5,6] -- output
```
* The partner in crime for *map* is *filter*.
* Instead of transforming all elements of a list, *filter* drops some elements of a list and keeps others.
* In other words, *filter* selects the elements from a list that fulfill a condition:

```haskell
filter :: (a -> Bool) -> [a] -> [a]
```

* Here's an example: selecting the positive elements from a list:

```haskell
positive :: Int -> Bool
positive x = x>0

filter positive [0,1,-1,3,-3]
  ==> [1,3] -- output
```

* Note how both the type signatures of *map* and *filter* use polymorphism.
* They work on all kinds of lists.
* The type of *map* even uses two type parameters!
* Here are some examples of type inference using *map* and *filter*. 

```haskell
onlyPositive xs = filter positive xs
mapBooleans f = map f [False,True]
```

* Console output... `:t onlyPositive...`
```
ghci> :t onlyPositive
onlyPositive :: [Int] -> [Int]
ghci> :t mapBooleans
mapBooleans :: (Bool -> b) -> [b]
ghci> :t mapBooleans not
mapBooleans not :: [Bool]
```

* One more thing: remember how constructors are just functions? That means you can pass them as arguments to other functions!

```haskell
wrapJust xs = map Just xs
```

* Console output...

```
ghci> :t wrapJust
wrapJust :: [a] -> [Maybe a]
ghci> wrapJust [1,2,3]
[Just 1, Just 2, Just 3] 
```

***

### 3.1.2 Examples of Functional Programming on Lists

* How many "palindrome numbers" are between 1 and n?

```haskell
-- a predicate that checks if a string is a palindrome
palindrome :: String -> Bool
palindrome str = str == reverse str

-- palindromes n takes all numbers from 1 to n, converts them to strings using show, and keeps only palindromes
palindromes :: Int -> [String]
palindromes n = filter palindrome (map show [1..n])

palindrome "1331" ==> True
palindromes 150 ==>
  ["1", "2", "3", "4", "5", "6", "7", "8", ... "141"]
length (palindromes 9999) ==> 198
```
* How many words in a string start with the letter "a"?
* This uses the function *words* from tme module **Data.List** that splits a string into words.

```haskell
countAWords :: String -> Int
countAWords string = length (filter startsWithA (words string))
  where startsWithA s = head s == 'a'

countAWords "does anyone want an apple?"
  ==> 3 -- output
```

* The function *tails* from *Data.List* returns the list of all suffixes ("tails") of a list.
* We can use *tails* for many string processing tasks.
* Here's how *tails* works:

```haskell
tails "echo"
  ==> ["echo", "cho", "ho", "o", ""] -- output
```
* Here's an example where we find what characters come after a given character in a string.
* First of all, we use *tails*, *map* and *take* to get all substrings of a certain length.

```haskell
substringsOfLength ...
```
* There are some shorter substrings...
* more more 


## 11/29/2024

***
