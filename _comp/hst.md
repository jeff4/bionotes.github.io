---
title: HST notes on Haskell
permalink: /hst/
sitemap: false
---

***

## 9/20/2024

*  Simon Thompson,  [Haskell: The Craft of Functional Programming](https://www.haskellcraft.com/craft3e/Home.html), 3rd edition.
* **hst** = **H**askell book by **S**imon **T**hompson
* Published by Pearson
* First edition published in August, 1996 
* Second edition published in 1999
* Third and most current edition published in 2011

***

# HST Chapter 1

***

## Setting up Haskell environment
* Recent [reddit link](https://www.reddit.com/r/haskell/comments/1aoaqxw/q_advantages_of_using_stack_vs_ghcup/) with good info from early 2024

## Haskell.org documentation
1. [Initial install](https://www.haskell.org/ghcup/install/) of GHCup
1. [Explanation of Cabal vs. Stack](https://gist.github.com/merijn/8152d561fb8b011f9313c48d876ceb07)
1. [First steps for Haskell](https://www.haskell.org/ghcup/steps/)


## Other links
* [2022 Stack Overflow](https://stackoverflow.com/questions/72056777/installing-ghcup-vs-vanilla-ghc-for-haskell) on GHCup vs. vanilla GHC
* [2024 Reddit](https://www.reddit.com/r/haskell/comments/1aoaqxw/q_advantages_of_using_stack_vs_ghcup/) on Stack vs. GHCup

## Don't use Brew for Haskell
* **haskell-platform is *No Longer Supported*. DO NOT USE.** And do not use brew generally for haskell looks like. Brew is not really the best option as of 2022. Best to go with GHCup. Read this [important 2022 answer](https://stackoverflow.com/questions/22499433/how-to-install-haskell-on-mac-os#comment130239140_73173644)
* **brew install haskell-stack** from [this May 2020 Stack Overflow answer](https://stackoverflow.com/a/29247096).
* Update that ghc version 9.2.4 or later is best for Apple Silicon per [this comment](https://stackoverflow.com/questions/22499433/how-to-install-haskell-on-mac-os#comment131204054_73173644)


## 9/22 installs
1. Used these [instructions](https://www.haskell.org/ghcup/install/) to install GHCup and this command `curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh`.
1. Options I selected:
	* **A** to append ghcup to **.bashrc** file
	* **N** to decline install of HLS language server for now
	* **Y** to install *Haskell Stack* for better integration with GHCup
1. Installer completed. Tested result with [these GHCi instructions](https://downloads.haskell.org/ghc/latest/docs/users_guide/ghci.html#introduction-to-ghci)
1. Changed `~/Dropbox/proj-1/` to main haskell directory. Added this:

```haskell
main = print (fac 20)
fac 0 = 1
fac n = n * fac (n-1)
```

## Other notes
* To quit *GHCi*, type `<ctrl>-D`.

## 9/25
## Section 1.7 Definitions p. 9 - 11
* Here is how you define a function named **addOneToThisNumber** that outputs a result of type **Integer:** `addOneToThisNumber :: Integer`
* Note that function names like **addOneToThisNumber** begin with a lowercase letter while the type of the output is capitalized. In languages with C-derived syntax, we might call this function *addOneToThisNumber()*.

## Section 1.8 Function Definitions p. 11
* Let's define a function, say something that accepts an *integer* as input and outputs *integer^2*. Let's call this function **square()**. 
* In Haskell, we would define this function like so, by indicatig the required datatype of the input as well as the required datatype of the output. And then we'd have a se3cond line that specifies how things work inside the black box. Line 1 is the function signature with input parameters and output type. Line 2 is the algorithm about how the function will operate.

```haskell
square :: Integer -> Integer
square n = n*n
```
* p. 12. Note that in Haskell, we call a parameter (aka the box that contains the value of a desired input variable) a **"formal parameter"**.
	* in contrast, what in JS we would call the **argument**, aka the *value* that is being passed into a particular parameter location, is called in Haskell the **"actual parameter"**.
* Here is an exxample of me running `square.hs`

```
[01:44:43 ~/Dropbox/proj-1]:ghci
GHCi, version 9.4.8: https://www.haskell.org/ghc/  :? for help
ghci> :load square
[1 of 2] Compiling Main             ( square.hs, interpreted )
Ok, one module loaded.
ghci> square 6
36
ghci>
```
* Note that the file `square.hs` was stored in the same directory where invoked **ghci**.
* When there are multiple input parameters (aka haskell *formal parameters*), we list them all first and reserve the final place for the output. 
* For example, if we have a function called **scale()** that increases the size of an input *Image* by some *Integer*, we need two input parameters and one output which is also an image. So the function signature (aka function declaration)  look like this: `scale :: Image -> Integer -> Image`. 
	* Where the first instance of Image is an input parameters

## 9/25/2024
* In the general case, for ***i* = 1 to n** `input parameters` **p<sub>*i*</sub>**, with an `output result` of type **outputType**, a function signature looks like this:
		**functionName() ::** **p<sub>1</sub>** -> **p<sub>2</sub>** -> **p<sub>3</sub>** -> ... -> **p<sub>n</sub> ->** **outputType**
* Note that all the **p<sub>*i*</sub>** and the **outputType** are all *types* as defined by Haskell.

### Function composition
* Now let's use something similar to the chain rule to chain multiple functions **f<sub>1</sub>**, **f<sub>2</sub>**, **f<sub>3</sub>**, **...**, **f<sub>k</sub>** together.
* Let's compose a function that flips the horizontal (**flipHorizontal()** aka **flipH**) with one that flips the vertical (**flipVertical()** aka **flipV**)
* Let's define a new function that does a complete 180 degrees rotation called **rotate()** aka **rotate**:
```haskell
rotate :: Image -> Image
rotate inputPhoto = flipH (flipV inputPhoto)
```
* Composing functions is such a common activity that Haskell provides a simplified syntax for this:
```haskell
rotate :: Image -> Image
rotate inputPhoto = flipH . flipV
```
* p. 14 The direct combination of functions illustrates the power of functional programming.
* We are able to combine functions using an operator like **`.`** just as we can combine numbers using a binary operator like **`+`**.
* We use the term **operator** because **.** is written *in-between* its arguments rather than *before* its arguments.
* We discuss operators in more detail in Section 3.7.
* The direct combination of functions using the operator **.** is not possible in other programming paradigms. Or at least, that would be considered an "advanced" aspect of those other programming languages.

## 1.9 Types and functional programming p. 14
* Benefits of using types in Haskell
* Provides a constraint on the kinds of input parameters and kind of output result are accepted/generated by a function.
* This enables **type checking**
* For example, if we try to invoke **scale horse horse**, we will get an error b/c **scale** expects 1 image and 1 number; *not* 2 input images.

### Brief mention of Type Abstraction p. 15
* We talk more about type abstraction in section 1.13 and in Chapter 16

## 1.10 Calculation and evaluation p. 15

## 9/27/2024

## 1.11 The essence of Haskell programming p. 16
* Let's now compare Haskell to OO and other imperative languages.

### Key aspects of Haskell and functional programming p. 16-17
1. Working in Haskell, we concentrate on using a rich collection of data types--including functions themselves, as well as types as defined by the user--to model the objects in the problem domain.
1. Programming over these is done by writing functions. Functions are defined by equations like:
	```haskell
	rotate :: Image -> Image
	rotate pic = flipH (flipV pic)
	-- above line could be expressed with dot notation
	rotate pic = flipH . flipV
	{- multi-line comment -}
	```
1. Finally, computing with these functions is done by calculating (aka *evaluating*) using definitions to calculate a result.
	* In an equation like the `rotate` function above, **pic** is a variable in the mathematical sense of something that stands for an *arbitrary* Image.

### Difference between functional and OO/imperative languages
* One needs to understand that Haskell variables are *very different* from variables in languages like Java, C, C++. etc.
* **A Java variable is like a box**. The value stored within that box changes by making an assignment.
	* In Java, one computes by changing the contents in those boxes (aka *variables*). 
	* The status of a variable's contents is also called the **state**.
	* Methods which change state are said to have **side-effects**.
* **A Haskell variable does *not* vary**. The way one programs in haskell is to write functions which describe how particular data values are **related to each other**.
* There is no state maintained in Haskell, and Haskell functions do *not* have **side-effects**.

### Summary of Haskell advantages p. 17
1. Haskell programs are **higher-level**
1. Functions in Haskell can themselves be passed around just like any other **data** (JH: aka functions can just act as parameters?).
1. Haskell functions are without side-effecs. But using **monads**, one can perform I/O, interact with filesystems, interoperate with other languagest, etc.
1. Easy parallellization because imperative languages like Java must maintain consistency of state between multiple threads/cores. Since Haskell has no state, this problem is elminated.
1. Easier to refactor because there are no side-effects
1. Properties and proofs are much easier to do in Haskell vs in other languages.

## 1.12 DSL Domain Specific Languages
* Although Haskell is a general purpose language, it can a powerful place within which to embed *DSLs* (Domain Specific Languages). DSLs aka *little languages* can be stand alone such as LaTeX, Verilog, Excel/R.
* Examples of eDSLs using Haskell include:
	1. **Lava** for circuit simulation and layout (1998)
	1. **Paradise** for pricing financial products (2008)
	1. **Orc** for orchestrating computations in science (2010)

## 1.13 Two models of Pictures
* Example of a horse-based DSL

***

## 1.14 Tests, properties, and proofs p. 22
### 1.14.1 Tests and properties p. 22
* Let's look at the previous example about *Pictures* from section 1.13. How do we test it? One method: write a test of the form: **apply this function() to this input...and then verify the output which should looke like this**.* See Figure 1.4 on p. 23.
* The tests in Fig 1.4  can be defined with the equality operator **`==`** in Haskell, returning **`True`** or **`False`** 
* Tests like the above can work for a single input. 
* **Property-based testing** in the the GHC-compatible Haskell testing library [QuickCheck](https://en.wikipedia.org/wiki/QuickCheck) allows us to check whether a property holds for a whole collection of randomly generated inputs.

### 1.14.2 What do we mean by property? p. 24
* Informally, it's like the earlier line *'If we flip an **image** twice in a mirror we expect to get back the **original image** where any **image** refers to any bitmap/raster 2d set of pixels.
* Let's formalize this as a set of 4 haskell functions:
	1. prop_rotate :: Picture -> Bool
	1. prop_flipV :: Picture -> Bool
	1. prop_flipH :: Picture -> Bool
* These are tests using the above 3 functions:
	1. **Test 1** `prop_rotate pic = flipV (flipH pic) === flipH (flipV pic)`
	1. **Test 2** `prop_flipV pic = flipV (flipV pic) == pic`
	1. **Test 3** `prop_flipH pic = flipH (flipV pic) == pic`

* If we use **QuickCheck** to these properties and evaluate in Haskell, we get the result: `+++ OK, passed 100 tests.` for Test 1 and Test 2.
* For Test 3, we get this output: `*** Failed! Falsifiable (after 3 tests and 3 shrinks): ["ab"]`
* The above failure tells us that the property is not always true and gives us an example of when it goes wrong.
* The testing is automatic: once we have written the properties to test, the data are generated randomly from *type: **Picture***. 
* Through the rest of the book, we will see more complex examples of property based testing and how to adjust the controls of Quick Check

***

### 1.14.3 Coverage and Proof p.24-25
* Whereas property-based testing simplifies automated testing, it's not formally proven. Proofs can cover *all* cases, with **zero exceptions**.
* Example of Pythagoras' Theorem.
* Proofs are possible for most programming languages, but is substantially easier for functional languages than any other programming paradigm.
* We will explore proofs more in Chapter 9: List Processing Functions.

***

# Chapter 2
## 9/29/2024
* the `it` keyword only works [within the GHCi interpreter](https://www.quora.com/What-does-the-it-keyword-do-in-Haskell/answer/Tikhon-Jelvis). It is bound to the result of the last expression typed into GHCi. Just typing `it` into the ghci will just echo the previous result, i think?
* p. 32 list of standard ghci commands

## 9/30/2024
## Using GHCI p. 29
* p. 33. **Task 3**. Steps:
	1. Invoke ghci
	1. Load first script module by typing **`:load FirstScript.hs`**
	1. Type following commands: `double 2 3`**,** `double square`**,** `2 double`**,**.
* Note that all of the above 3 commands leads to an error. B/c the function **double** expects a single input parameter that comes *after* the function. All of the above do not follow that structure.
	* Command 1 includes both **2** and **3** as *two* integer parameters whereas function **double** expects one integer parameter.
	* Command 2 provides the function **square** as a parameter. But the function **double** expects an integer parameter.
	* Command 3 provides an integer *before* the function **double**; but the parameter needs to enter *after* the function.


## 2.4 The standard Prelude and the Haskell libraries p. 33
* Definitions of the standard Haskell types are contained in the **Preulde.hs** file.
* When Haskell is used, the default is to load the standard prelude.
* Standard Hasell types include integers, lists, functions over the same, arithmetic functions, list functions **map** and **++**.
* p. 33 see `:browse Prelude` command.
* As Hasell has developed, the **prelude** has grown. In order to make the prelude smaller and to free up some keywords/names from it, many of the definitions have been moved *from* the Haskell Prelude *to* the Haskell Standard Libraries.
* In addition to the standard libraries, the Haskell Platform includes various contributed libraries which support concurrency, functional animations, etc. 

## 2.5 Haskell Modules p. 34
* A typical piece of software will contain thousands of lines of source code. We can structure this by breaking the code into subcomponents called **modules** in Haskell, of the form `module <ModuleName> where...`
* A module may **import** definitions from other modules, e.g., 
```haskell
module Ant where
import Insect
...
```
* The import statement means that we can use all the definitions in **Insect** when making definitions in **Ant**.
* in this text, we use the conventions:
	1. There is exactly one module per file
	1. The file **Blah.hs** contains a module named **Blah**.
* See Figure 2.5 on p. 34 to understand how a GHCi session works wrt Prelude, modules, libraries, etc.

***

## 10/02/2024

## 2.6 A Second Example: Pictures p. 35
* A running example in Chapter 1 was of pictures, and we saw two implementations of these functions, one in **Pictures.hs** giving an *ASCII art* version. 
* And the other in *PicturesSVG.hs* has rendering pictures in a web browser.
* Copied source code from p. 36 into cdp1 

***

## 10/04/2024
* A few more links.
* [Basic Haskell Examples](https://www.haskellforall.com/2015/10/basic-haskell-examples.html) at Haskell for All:
	* The Haskell community self-selects for people interested in unique things that Haskell can do that other languages cannot do. 
	* Consequently, a large chunk of Haskell example code in the wild uses advanced idioms (and I'm guilty of that, too).
	* So I would like to swing the pendulum in the other direction by just writing five small but useful programs without any imports, language extensions, or advanced features. 
	* These are programs that you could write in any other language and that's the point: you can use Haskell in the same way that you use other languages.
* From [reddit](https://www.reddit.com/r/haskell/comments/ksct8f/simple_elegant_code_examples_to_demonstrate/)
* [99 Haskell Problems](https://wiki.haskell.org/H-99:_Ninety-Nine_Haskell_Problems)

***

## 10/22/2024

### Install on minipro-23
* Simple, single line install, per [these instructions](https://www.haskell.org/ghcup/install/):
```
curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh
```
* Went through steps as discussed on 9/22/2024 for laptop. 
1. Options I selected:
	* **A** to append ghcup to **.bashrc** file
	* **N** to decline install of HLS language server for now
	* **Y** to install *Haskell Stack* for better integration with GHCup

* Got this message `Note: On OS X, in the course of running ghcup you will be given a dialog box to install the command line tools. Accept and the requirements will be installed for you. You will then need to run the command again. On Darwin M1 you might also need a working llvm installed (e.g. via brew) and have the toolchain exposed in PATH.`:w
* Since minipro-23 has already been upgraded to Mac OS Sequoia (v. 15.0.1), I figured Xcode cmdline tools (CLT) is lalready upgraded to latest version.
	* Verified version of CLT by typing: `brew config` at terminal. Returned `CLT: 16.0.0.0.1.1724870825`.
* Went back to terminal window with GHCup install and pressed **`<ENTER>`**
* Note, installed in the `base` mamba environment. Noting b/c there may be some python dependency for either install or running of Haskell/GHC?
* Ok, it all seemed to work!

### Hello World on minipro-23
```
(base) [15:28:26 ~]:ghci
GHCi, version 9.4.8: https://www.haskell.org/ghc/  :? for help
ghci> let myString = "Hello Jeff!"
ghci> putStrLn myString
Hello Jeff!
ghci> [CTRL-D]
Leaving GHCi.
(base) [15:30:10 ~]:
```
***

### Install on imac-2018
* Simple, single line install, per [these instructions](https://www.haskell.org/ghcup/install/):
```
curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh
```
* Everything was same as minipro-23 above. Working as expected.
* For some reason, this rebooted my `.bashrc` file such that the earlier command `eval "$(starship init bash)"` now seems to work for both Terminal and Alacritty.

***

## 10/23/2024
* Let's build a simple TSV to CSV converter in Haskell. Example #2 from 2015 [article on Basic Haskell Examples](https://www.haskellforall.com/2015/10/basic-haskell-examples.html)
* Hm, didn't work.
* Let's try [lecture course](https://haskell.mooc.fi/) that comes in 2 parts. Here is [Part 1](https://haskell.mooc.fi/part1#lecture-1-and-so-it-begins)
	* Found on this [reddit comment from 2022](https://www.reddit.com/r/haskell/comments/yftmbm/comment/iu8suis/)
* Also, consider the [Haskell Wiki Book](https://en.wikibooks.org/wiki/Haskell)

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
* When one tries to evaluate `factorial(-1)`, get this error:
```
<interactive>:8:11: error:
    • No instance for (Num (Int -> Int)) arising from a use of ‘-’
        (maybe you haven't applied a function to enough arguments?)
    • In the expression: factorial - 1
      In an equation for ‘it’: it = factorial - 1
```
***

10/28/2024
* Used pen and paper to work out the *internal logic* steps listed above from 10/26. Very interesting. In contrast, this is the implementation in JavaScript...

