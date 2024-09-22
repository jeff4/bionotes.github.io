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
9/21/2024

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
