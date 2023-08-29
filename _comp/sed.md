---
title: Sed Notes
permalink: /sed/
---

## 7/09/2022
* Links on [sed (for stream processing)](https://en.wikipedia.org/wiki/Sed) and [awk (for delimited columns by Aho, Weinberger, and Kernighan)](https://en.wikipedia.org/wiki/AWK).
* (Reviewed two links below on 8/22. Best to use other sed reources b/c these are very basic.)
	* <del>[Software Testing Help](https://www.softwaretestinghelp.com/unix-filter-awk-sed-commands/#:~:text=Unix%20provides%20sed%20and%20awk,well%20with%20delimited%20field%20processing.)</del>
	* <del>[Linux Geeks make use of](https://www.makeuseof.com/tag/sed-awk-learn/)</del>
 
## 7/11 
* More links on sed from Hacker News:
	* Grymoire's [Intro and Tutorial for Sed by Bruce Barnett](https://www.grymoire.com/Unix/sed.html) and associated [2015 HN thread](https://news.ycombinator.com/item?id=8851124) with a [comment about Grymoire's similar awk tutorial](https://news.ycombinator.com/item?id=8853658). Plus Grymoire's [grep tutorial](https://www.grymoire.com/Unix/Grep.html)
	* [Differences between grep, sed, awk from Linode](https://www.linode.com/docs/guides/differences-between-grep-sed-awk/#the-differences-between-grep-sed-and-awk) and [2023 HN thread](https://news.ycombinator.com/item?id=34280281)
	* [Gnu Sed manual and tutorial](https://www.gnu.org/software/sed/manual/sed.html)
	* Casual [quick notes on sed](https://github.com/adrianlarion/useful-sed) with associated [2021 HN thread](https://news.ycombinator.com/item?id=29196221). Note that there may be errors in some of these sed scripts.

## 7/12 
* More sed links: 
	* Good sed exercises at [50 sed examples](https://linuxhint.com/50_sed_command_examples/). Began going through more seriously on 8/23.
	* <del>This might be a better [set of 10 sed examples](https://www.makeuseof.com/sed-examples/)</del>. *Completed this on 8/23.*

## 7/13
* Reflections. GNU sed (invoked by gsed) works better than core utils sed that comes prepackaged with macOS. Important to use double quotes (") rather than single quotes('). And ability to chain regexps with a semi-colon (;) sequentially is pretty useful to keep patterns distinct. Although probably hard to maintain..
* Best video so far on [sed by Luke Smith](https://youtu.be/QaGhpqRll_k)

## 8/07
* More sed resources (see also Notes app):
	* From 2008 or so but updated since then. [Sed-one-liners](https://catonmat.net/worlds-best-introduction-to-sed), associated [text files with all one-liners](https://catonmat.net/wp-content/uploads/2008/09/sed1line.txt) and associated [HN comment](https://news.ycombinator.com/item?id=2431264). It's the first chapter of a $20 e-book [Sed One-Liners Explained](https://catonmat.net/sed-book). Note that catonmat = [Peter Krumins](https://catonmat.net/about), co-founder of Browserling.com. And these one-liners were originally compiled by [Eric Pement](https://www.pement.org/sed/)
	* From the same 2011 thread on [Sedtris: Tetris in sed](https://news.ycombinator.com/item?id=2430171) where the above catonmat one-liner article appeared, also found this [2008 other side of the moon Progamming Patterns in sed](https://tech.bluesmoon.info/2008/09/programming-patterns-in-sed.html)
* Completed Luke Smith video from 7/12.
* Began experimenting with catonmat's [first chapter](https://catonmat.net/worlds-best-introduction-to-sed)

## 8/08
* Hm, perhaps look at the sed resources at [Eric Pement's site](https://www.pement.org/sed/)
* On second thought, i think grymoire's original [Bruce Barnett's Sed intro and tutorial](https://www.grymoire.com/Unix/Sed.html) is the better way to go.

## 8/09
* Finished to the end of the flag section in Grymoire site, aka the section titled ['Write to a file with /w filename'](https://www.grymoire.com/Unix/Sed.html#toc-uh-10)
* Finished up to end of the ['Multiple commands witn an -command' section](https://www.grymoire.com/Unix/Sed.html#uh-13). Next section is 'Filenames on the command line'.

## 8/10 Regex notes
* z\* matches zero to any z's found. z+ matches 1 to any z's found. z? optionally matches z's found.
* Good [regex tutorial](https://www.regular-expressions.info/optional.html). Question mark is called a *quantifier*. This tutorial mostly focuses NFA aka "regex-directed" engines.
* The 12 reserved charactes in regex like *?.()[]* are called special characters or **metacharacters**.
	* Note that single quote and double quote are *not* metacharacters. You can treat them as literals.
* The section on how [regex engines work internally](https://www.regular-expressions.info/engine.html) is essential! The end of this section has a simple but clear example of how left-most matching and sequencing works when matching.
* This website also has a good [summary of GNU regexp](https://www.regular-expressions.info/gnu.html) for tools like GNU sed. But the site also has [extensive documentation about regexp support/flavors for many other languages, frameworks, and tools](https://www.regular-expressions.info/reference.html).
* Most flavors of sed use traditional NFA per the [3rd edition of Mastering Regular Expressions (2006)](https://www.oreilly.com/library/view/mastering-regular-expressions/0596528124/ch04.html). In other words, sed regex is non-deterministic. See [this excellent semi-academic blog post](https://www.abstractsyntaxseed.com/blog/regex-engine/nfa-vs-dfa). The end of [Chapter 4 of MRE](https://www.oreilly.com/library/view/mastering-regular-expressions/0596528124/ch04.html) has good examples to help determine if a particular regex engine is NFA, Traditional NFA, POSIX NFA, DFA, or a hybrid between NFA/DFA. 
	* NFA = Non-deterministic Finite Automata aka "regex directed"
	* DFA = Deterministic Finite Automata aka "text directed". Always greedy.
* Character classes = Character sets are synonyms. Defined by square brackets around the set [].
* ^ = negation for the remainder of a character class.
* Most of the usual [metacharacters act as a normal literal character when inside square brackets](https://www.regular-expressions.info/charclass.html) as part of a class! i.e. "In most regex flavors, the only special characters or metacharacters inside a character class are the closing bracket ], the backslash \, the caret ^, and the hyphen -. The usual metacharacters are normal characters inside a character class, and do not need to be escaped by a backslash. To search for a star or plus, use [+*]. Your regex will work fine if you escape the regular metacharacters inside a character class, but doing so significantly reduces readability."
	* Special note which I think applies to gsed: "The closing bracket ], the caret ^ and the hyphen - can be included by escaping them with a backslash, or by placing them in a position where they do not take on their special meaning. The POSIX and GNU flavors are an exception. They treat backslashes in character classes as literal characters. So with these flavors, you can’t escape anything in character classes."
* Common shorthands to avoid typing the same character class over and over again:
	* **\d** = [0-9], i.e., all digits
	* **\w** = [A-Za-z0-9_], i.e. all 'word' characters
	* Note "It always matches the ASCII characters [A-Za-z0-9_]. Notice the inclusion of the underscore and digits. In most flavors that support Unicode, \w includes many characters from other scripts. There is a lot of inconsistency about which characters are actually included. Letters and digits from alphabetic scripts and ideographs are generally included. Connector punctuation other than the underscore and numeric symbols that aren’t digits may or may not be included." from [this section](https://www.regular-expressions.info/shorthand.html)
	* **\s** = whitespace characters. BUT "\s stands for “whitespace character”. Again, which characters this actually includes, depends on the regex flavor. In all flavors discussed in this tutorial, it includes [ \t\r\n\f]. That is: \s matches a space, a tab, a carriage return, a line feed, or a form feed. Most flavors also include the vertical tab, with Perl (prior to version 5.18) and PCRE (prior to version 8.34) being notable exceptions. In flavors that support Unicode, \s normally includes all characters from the Unicode “separator” category. Java and PCRE are exceptions once again. But JavaScript does match all Unicode whitespace with \s." A lot of inconsistency!
	* you can negate any of the shortcuts above by use uppercase versions of the shortcuts. e.g., **\D** = anything *other than digits*; **\S** = anything *other than whitespace characters*.

## 8/11 Regex notes
* **\b** = very useful word border. Used in history file and detected The, These, There, Their, etc. See OneNote also from 8/11 under gsed notes.
* From [The Dot section](https://www.regular-expressions.info/dot.html), scroll to the bottom two sections. \N never matches line breaks. But more importantly, use the dot sparingly. Probably better to use a negated characer class instead of the form \[^ these chars are negated\].
* ^ and $ at the beginning and end of lines (obviously like in vim), are called [*String Anchors*](https://www.regular-expressions.info/anchors.html).
* [Parentheses are used for grouping](https://www.regular-expressions.info/brackets.html) while [**pipes \|**](https://www.regular-expressions.info/alternation.html) are used to demarcate different enumerated options like a multiple choice or case/switch block.
	* Note that POSIX like GNU usually chooses the longest option, etc., prefers *catapult* instead of *cat* in the expression **(cat \| catapult )**. So you need to be explicit to make sure the longest or left-most option is not used. 
* Optional items are marked by the **? question mark** as described in [this section](https://www.regular-expressions.info/optional.html) which also explains the concept of greediness.
* Star \(*) and Plus \(+) allow 0-infinite matches and and Plus allow 1-infinite matches. You can also specify how much reptition exactly with curly braces{}. See more at [this article](https://www.regular-expressions.info/repeat.html)

## 8/17 sed
* Tried duos of 'history', 'British', and 'local' in 4-test.md input file and used gsed command to remove them one at a time. Now need to have a generic regex that can remove n duplicated words.

## 8/18 sed
* After experimentation, I realized that using the **-r** flag to activate Extended Regular Expressions (ERE)  is critical to getting regex working well with gsed. 
* With that flag turned on, can use parentheses to create numbered capturing groups. For awhile, I could use gsed without the -r flag turned on; I was able to capture patterns in groups with parentheses just by making sure I properly escaped those parens with a backslash like so \\(. However, I got inconsistent results. 
* In the end, the best bet was to just turn on **-r** like this:
		`gsed -nr 's#\b(\w+)\b \b\1\b#\1  ~~~ \1#gp' source.txt >out.txt`
* The above example uses **-n** to suppress automatic printing. Other notes:
	* The **gp** options at the end ensure respectively: (1) that all instances per line are executed on (globally), NOT just the first instance; and (2) p means print each line where a line matches indicated pattern and is worked upon.
	* I'm using hash-marks (#) instead of the usual forward slash (/) as delimiters. 
	* I'm using **\\b** as word-boundaries. 
	* The '~~~' symbol shows how to visually see where i've inserted something into the doubled space.

## 8/19 sed
* Next step, try doing case insensitive substitutions using ['s/the/the the/I' from this section](https://www.grymoire.com/Unix/Sed.html#uh-10a)
* When using shuf to shuffle contents of /zhongwen, make sure to use the -o option to indicate output file, e.g., 
		`shuf source.txt -o output.txt`

## 8/22 
* [Short blog post](https://utcc.utoronto.ca/~cks/space/blog/unix/UnixTechnologyAndIdea) about Unix as a technology and as an idea. [HN thread](https://news.ycombinator.com/item?id=37205536)
* Purchased Peter Krumins' (catonmat) e-book [*Sed One-Liners Explained*](https://catonmat.net/sed-book). See Box.

## 8/23 sed
* Next two examples from [this 10 examples article](https://www.makeuseof.com/sed-examples/) that I referenced on 7/13.
	1. Interesting and quick way to doublespace a single-spaced file. i.e., add a blank line after each line. 
		`gsed 'G' 1-indigenous-test.md >out.txt`
	1. To add two blank lines in between each line, add another expression with a semi-colon.
		`gsed 'G;G' 1-indigenous-test.md >out.txt`
* Next several examples from [this 50 examples article](https://linuxhint.com/50_sed_command_examples/#s9) starting with Example #9. Referenced on 7/12.
	1. In addition to defining ranges (i.e., only execute this for lines 5-20'), one can set a pattern to look for before executing the action. For example, the one-liner below will only replace lowercase 'the' with uppercase "THE' when the line contains "These" with a capital T.
		`gsed -nr '/These/ s/the/THE/gp' 2-indigenous-test.md >out.txt`
	1. Also, the pattern for 'These' can accept regex syntax. So if we want to execute this substitution on lines for both 'These' and 'these', we can search for (T|t)
		`gsed -nr '/(T|t)hese/ s/the/THE/gp' 2-indigenous-test.md >out.txt`
	1. Unfortunately, the initial pattern does not allow flags so something like `/These/i` would not work. *BUT* the i flag when added to the g (global) and p (print) flags will pattern match for case insensitive the/The. And it will be case-insensitive for 't', 'h', and 'e'.
		`gsed -nr '/(T|t)hese/ s/the/THE/gpi' 2-indigenous-test.md >out.txt`
	1. Conversely, if you want to apply something to all the lines that **don't** have a 'These' in it, you can just add a **!** flag like so /These/!:
		`gsed -nr '/These/! s/the/THE/gpi' 2-indigenous-test.md >out.txt`

## 8/26 sed - Peter Krumins' Sed One-Liners
* **2.6** Insert a blank line below every line that matches a */pattern/*. 
	* PK's example:
		`gsed -r '/pattern/G'`
	* Jeff's example from hist-ss NYer article:
		`gsed -r '/Constable/G' gopnik-2023-dalle.md >out.txt`
	* Note that the explanation for the **G** flag comes from **Example 2.1**.
* **2.9** Duplicate all lines
	* PK's example:
		`gsed -r 'p'`
	* Jeff's example from hist-ss NYer article:
		`gsed -r 'p' gopnik-2023-dalle.md >out.txt`
* **3.1** Number each line of a file
	* PK's example:
		`gsed = filename | sed 'N;s_\n_\t_'` where _ is used as delimiter instead of usual /.
	* Jeff's example from hist-ss NYer article:
		`gsed = gopnik-2023-dalle.md | gsed 'N;s_\n_\t_' >out.txt`
	* *Note: This example calls sed twice with a pipe. Instance 1 loads the file using the **=** operator. And instance two searches for new lines and replaces them with tab characters.* 
* **3.4** Count number of lines in file *aka* simulate 'wc -l'
	* PK's example:
		`gsed -n '$='`
	* Jeff's example from hist-ss NYer article:
		`gsed -n '$=' gopnik-2023-dalle.md >out.txt`