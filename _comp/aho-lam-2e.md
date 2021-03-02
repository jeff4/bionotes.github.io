---
title: Compilers 2nd Edition, 2007
permalink: /aho-lam-2e/
---


# Compilers: Principles, Techniques, & Tools
* [2nd Edition - "The Purple Dragon" book](https://en.wikipedia.org/wiki/Compilers:_Principles,_Techniques,_and_Tools)
* Authors: Alfred V. Aho, Monica S. Lam, Ravi Sethi, Jeffrey D. Ullman

## Chapter 1:  Introduction

### 1.2: The Structure of A Compiler
* Within the black box of the compiler are two subsections: **analysis** and **synthesis**

* **Analysis** Subsection aka *The Front End*
	* Breaks up the source program into constituent pieces and imposes a grammatical structure on them. 
	* Turns grammatical structure into an intermediate representation.
	* If the source program is syntatically ill-formed or semantically unsound, then it tries to return informative error messages to the programmer.
	* Generates a *symbol table* which is passed along with the intermediate representation
* **Synthesis** Subsection aka **The Back End**
	* Consolidates the intermediate representation and symbol table together and turns them into the desired target program.

#### Phases of compilation
* **Lexical Analyzer &#8594; Syntax Analyzer &#8594; Semantic Analyzer &#8594; Intermediate Code Generator &#8594; Machine-Independent Code Optimizer &#8594; Code Generator &#8594; Machine-Dependent Code Optimizer**
*  *character stream* &#8594; Lexical Analyzer &#8594; *token stream* &#8594; Syntax Analyzer &#8594; *syntax tree* &#8594; Semantic Analyzer &#8594; *syntax tree* &#8594; Intermediate Code Generator &#8594; *intermediate representation* &#8594; Machine-Independent Code Optimizer &#8594;*intermediate representation* &#8594;  Code Generator &#8594; *target-machine code* &#8594; Machine-Dependent Code Optimizer &#8594; *target-machine code*

#### 1.2.1 Lexical Analysis
* Lexical analysis aka scanning reads the stream of input characters from the source code and organizes them into [lexemes](https://en.wikipedia.org/wiki/Lexical_analysis#Lexeme).
* The scanner then assigns a token to each lexeme in the form: {*token-name*, *attribute-value*}. 


#### 1.2.2 Syntax Analysis
* The second phase of the compiler is called syntax analysis aka parsing.





