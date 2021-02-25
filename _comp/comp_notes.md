---
title: Comp Notes
permalink: /comp_notes/
---

## Log
* 2/21/2021: upgraded laptop to Big Sur. Downloaded Atom editor.
* 2/22/2021: downloaded Command Line Tools for Mac OS v. 12.4 and was able to get "Hello World" working in Atom and cmdline using clang. Appropriate because it has been exactly 43 years and 1 day since K&R pubished this, per [Daring Fireball](https://daringfireball.net/linked/2021/02/23/hello-world) and [CSAIL at MIT](https://twitter.com/MIT_CSAIL/status/1363875135191678984).
* 2/24/2021
	* Started new paper notebook
	* Drew diagram of **Figure 2.1 – Typical Toolchain**: Preprocessor&#8594;Compiler&#8594;Assembler&#8594;Static Linker&#8594;Dynamic Linker.
	* Drew diagram of **Fig 2.2 – Stages of a Typical Unix Compiler**: Scanner&#8594;Parser&#8594;*AST*&#8594;Semantic Routines&#8594;Multiple rounds of Optimizers&#8594;Code Generator&#8594;*Assembly.s output* 
	* Experimented with clang to output AST per instructions [here](https://bastian.rieck.me/blog/posts/2015/baby_steps_libclang_ast/)
* **cpp** is a confusingly overloaded term. 
	* First, it may refer to the first part of the gcc tool chain which is the *cpp* **C P**re**P**rocessor. 
	* Secondly,  the .cpp in *foo.cpp* is the file extension for C++ source files. E.g., "hello.cpp" compiles to a C++ executable that runs the "hello.o" object code.
* Per Figure 2.1 (see JH notes Comp #1, 2/22/2021), the gcc compiler is also called cc1 per this [Stack Overflow article](https://stackoverflow.com/questions/63561353/is-gcc-a-compiler-or-is-it-a-collection-of-tools-for-the-compilation-process).

### Tools in a typical toolchain
* Preprocessor (e.g., **cpp** in gcc)
* Compiler proper (e.g., **cc1** in gcc)
* Assembler (called [**as** or **gas**](https://en.wikipedia.org/wiki/GNU_Assembler) in gcc)
* Static linker (e.g., [ld](https://ftp.gnu.org/old-gnu/Manuals/ld-2.9.1/html_node/ld_3.html) in gcc)
* Dynamic linker (e.g., [ld.so](http://manpages.ubuntu.com/manpages/cosmic/man8/ld.so.8.html) in gcc)
* See also Fig. 2.1 and drawings in JH Notes Comp #1, 2/22/2021.

### Subcomponents within a Unix Compiler
* Scanner
* Parser (generates AST)
* Semantic Routines
* A series of code optimizers
* Code generator
* See also Fig. 2.2 and drawings in JH Notes Comp #1, 2/24/2021.

