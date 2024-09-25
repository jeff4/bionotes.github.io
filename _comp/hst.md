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
1. Used this [Initial install](https://www.haskell.org/ghcup/install/) of GHCup and this command `curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh`.
1. Options I selected:
	* **A** to append ghcup to **.bashrc** file
	* **N** to decline install of HLS language server for now
	* **Y** to install *Haskell Stack* for better integration with GHCup
1. Installer completed. Tested result with [these GHCi instructions](https://downloads.haskell.org/ghc/latest/docs/users_guide/ghci.html#introduction-to-ghci)
1. Changed `~/demo-files/proj-1/` to main haskell directory. Added this:

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
* We are able to combine fnctions using an operator like **.** juast as we can combine numbers using a binary operator like **+**.
* We use the term **operator** because **.** is written *in-between* its arguments rather than *before* its arguments.
* We discuss operators in more detail in Section 3.7.
* The direct combination of functions using the operator **.** is not possible in other programming paradigms. Or at least, that would be considered an "advanced" aspect of those other programming languages.

## 1.9 Types and functional programming p. 14
* Benefits of using types in Haskell
* Provides a constraint on the kinds of input parameters and kind of output result are accepted/generated by a function.
* This enables **type checking**
* For example, if we try to invoke **scale horse horse**, we will get an error b/c **scale** expects 1 image and 1 number; *not* 2 input images.
