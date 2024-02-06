---
title: Notes on vim
permalink: /vim/
---

## Log
* 2/18/2023 - Found good reasoning and explanation of syntax highlights for vim [here](https://www.cduan.com/technical/vi/vi-4.shtml) 
* 2/25/2023 - Great advanced vim resource especially vimscripting [here](https://learnvimscriptthehardway.stevelosh.com/)
* 3/02/2023 - Cool new tricks in this 14-minute MAKC [Youtube video](https://www.youtube.com/watch?v=B-EPvfxcgl0) titled "My Favorite Vim Tricks". Outline:
	* Tabs, Custom Workspaces, Multi-language Spell Checking, (auto) completonn Ctrl-p/n, File Explorers, Visual Block mode, Macros 
* 3/03/2023 - From The Valuable Dev. [A Vim Guide for Advanced Users](https://thevaluable.dev/vim-advanced/) ... part of series. 
	* First article for beginners is [here](https://thevaluable.dev/vim-commands-beginner/).
	* Guide for intermediate users is [here](https://thevaluable.dev/vim-intermediate/)
* 3/03 - [*Vim Tips for the Intermediate Vim User*](https://jemma.dev/blog/intermediate-vim-tips) By Jemma Issroff, starts with talking about mini-golf and then starts goes into interesting examples. 
* 3/04 - From this Hacker News [comment](https://news.ycombinator.com/item?id=33812893)
	* Best user manual and [guide with examples](https://vimhelp.org/usr_01.txt.html#usr_01.txt) is built into the editor.
	* [Table of contents](https://vimhelp.org/usr_toc.txt.html) accessible via *:h user_toc.txt*
	* [Reference Manual](https://vimhelp.org/#reference_toc) accessible via *:h reference_toc*
	* [Cheatsheet](https://vimhelp.org/quickref.txt.html) accessible via *:h quickref*
* 3/05 Famous Stackover Flow [answer from 8/09/2009](https://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim/1220118#1220118)--epic explanation about how to grok vi.
	* From same thread is this [answer from 2010](https://stackoverflow.com/a/2559262) which has a ton of shortcuts, a starter .vimrc file etc.
* 3/10 Figured out proper autocommands to change colorscheme based on Insert or Command mode.
* 3/11 Decide which new colorschemes to add. Partially inspired by [this YouTube video](https://www.youtube.com/watch?v=7R7LOxOoAw0)
	* [Gruvbox](https://github.com/morhetz/gruvbox)
	* [Solarized](https://ethanschoonover.com/solarized/)
	* [Nord](https://www.nordtheme.com/)
* 3/12 Successfully followed [these instructions](https://www.cyberciti.biz/programming/vim-plug-a-beautiful-and-minimalist-vim-plugin-manager-for-unix-and-linux-users/) to install vim-plug
	* Also installed dracula, codedark, and personal favorite: Kolor.
* 3/21 Lots of progress documented in OneNote. For autocomplete based on other words in the document, go into Insert mode and try Ctrl-n and Ctrl-p. For more, see [this help doc](https://vimdoc.sourceforge.net/htmldoc/insert.html#i_CTRL-N) or [this help doc](https://vimdoc.sourceforge.net/htmldoc/insert.html#ins-completion)
* 3/23 Delighted by typing ci{ or di{ where i refers to "inside" and you can (c)hange or (d)elete everything inside those curly braces.
	* Works for ci* where * = parentheses, quotes, brackets, curly braces, any open/closed tokens.
* 3/25 Need to rewatch this [video](https://www.youtube.com/watch?v=bQfFvExpZDU) on g commands. Off the top of my head:
	* gj and gk in the context of a long line of text which appears visually as a single paragraph allows one to move up and down *within* that paragraph without going to different lines
		* Also works by adding movement so g5j will move 5 lines down within the visual block of text
	* gu [text object] makes everything lowercase. gU [text object] makes everything uppercase.
		* e.g., gu$ makes everything lowercase to the end of the line.
		* e.g., gU5w makes the next 5 words uppercase
* 5/04 [List of vim-friendly apps and utilities](https://github.com/erikw/vim-keybindings-everywhere-the-ultimate-list) and associated [HN thread](https://news.ycombinator.com/item?id=35816361)
* 7/11 Vim's implementation of grep. Some links discussing various flavors of regex related to perl, vim, Basic Regular Expression (BRE) synatx, Extended Regular Expression (ERE) synatx, etc.
	* Very short [comparison of regex flavors](http://vimregex.com/#compare) from this [Guide to regex in vim](http://vimregex.com/)
	* [Stack overflow question from 2010](https://stackoverflow.com/questions/3864467/whats-the-difference-between-vim-regex-and-normal-regex). See this [comment](https://stackoverflow.com/a/14851587) and also use vim *:help perl-patterns*
	* vim's regex mode, invoked by prepending with \v. See vim *:help /\v*
	* See also vim *:help pattern*
* 8/05 - Creator and maintainer of vim [Bram Moolenaar](https://en.wikipedia.org/wiki/Bram_Moolenaar) passed away. :( [HN thread with personal anecdotes](https://en.wikipedia.org/wiki/Bram_Moolenaar)
* 8/27 - Created distinct [page for my sed notes](/sed/)

## 9/16/2023

* Got back into [vim-plug](https://github.com/junegunn/vim-plug) because I want to have proper \*.astro syntax highlighting. Referencing the [vim-astro plugin](https://github.com/wuelnerdotexe/vim-astro). Adapted instructions from this [Linux vim-plug guide](https://www.linuxfordevices.com/tutorials/linux/vim-plug-install-plugins). Main steps: (1) add a new line to `.vimrc`; (2) start new terminal window; and (3) Open a vim file and type `:PlugInstall`.
* I also edited my `.gitignore` file within `/proj-4/a2-astro` so that temporary vim files like `*.swp` and `*.swo` are not tracked/pushed by git, per [these instructions](https://stackoverflow.com/questions/4824188/git-ignore-vim-temporary-files#comment28311078_4824199)
	* Should read more about how [.gitignore works](https://git-scm.com/docs/gitignore)
* Note. I currently am able to indent pretty effectively with the `ctrl-v`, select how many rows with `j`, `shift-I`, type text or tabs to apply to all lines sequence. However, deletion (aka outdenting) doesn't seem to work to well. Reread section 5 [Blockwise operators](https://vimdoc.sourceforge.net/htmldoc/visual.html#blockwise-operators) to see if I can fix this.
	* Another potential [resource](https://vim.fandom.com/wiki/Shifting_blocks_visually)

## 9/24/2023
* to switch immediately to tab number 'n', type `ngt`. e.g, to move to tab 5, type `5gt`.
* when invoking vim on the command line, typing `vim -p filename1.txt filename2.txt` will automatically open desired files all at once, each in its own tab all in the same instance of vim.


## 9/27/2023
* Very handy way of deleting to a `search string` e.g., 'Nashville'. Instead of typing `dtN`, type `d/Nashville` followed by <CR> or `Enter` key. See [this answer](https://vi.stackexchange.com/questions/14459/delete-to-next-search-result)
* Note that to search backwards, `Shift-/` aka `?` works just like usual reverse search. e.g., instead of typing `dTN`, type `d?Nashville` followed by <CR> or `Enter` key. 

## 10/11/2023
* vim has a built in sort utility works very well. If you want to sort all lines `:%sort u`. For more see [this article](https://vim.fandom.com/wiki/Sort_lines#:~:text=Yes%2C%20it%27s%20that%20simple.,%27%3E%20on%20the%20command%20line.)

## 2/05/2024
* Notes on `qq` macro recordings can be found in a7 > History of Technology section > Pasquinelli Chapter 2 *aka* `54-pas-chap2`.
* Notes on new `qq` macro recordings can be found in a7 > Eng > Part II Diallectics *aka* `72-p2`.

## 2/06/2024
* This is how you paste into the `:` command line, officially called the *Ex command line*. Add something to the default register using `y` for yank, e.g., `yl` for 1 letter, `yw` for 1 word.
	* e.g., `yb` for one word backward
	* Then, go to ex cmd line by typing <esc> and typing `:`
	* `<Ctrl> + r` and then type *"* to access the default register
	* Can type `"a` to access the **a** register
* For more detailed instructions in how to enter in escape/control characters, see this comment
