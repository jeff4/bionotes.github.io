---
title: HST notes on Haskell
permalink: /hst/
sitemap: false
---


***
## General Haskell Notes
* 11/03/2024 [Reimplementation of unix core utilities](https://github.com/Gandalf-/coreutils) in Haskell. [HN thread](https://news.ycombinator.com/item?id=41992270) with comments by [repo owner Austin](https://github.com/Gandalf-).
	* Austin has some [posts](https://www.anardil.net/tag/coreutils.html) on his blog discussing his work.
	* Austin is [answering questions](https://news.ycombinator.com/item?id=42032718) in the HN thread.

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
* Here is an example of me running `square.hs`

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
