---
title: Notes on vim
permalink: /vim/
---

## 2023 Log
* 2/18/2023 - Found good reasoning and explanation of syntax highlights for vim [here](https://www.cduan.com/technical/vi/vi-4.shtml) 
* 2/25/2023 - Great advanced vim resource especially vimscripting [here](https://learnvimscriptthehardway.stevelosh.com/)
* 3/02/2023 - Cool new tricks in this 14-minute MAKC [Youtube video](https://www.youtube.com/watch?v=B-EPvfxcgl0) titled "My Favorite Vim Tricks". Outline:
	* Tabs, Custom Workspaces, Multi-language Spell Checking, (auto) completeion Ctrl-p/n, File Explorers, Visual Block mode, Macros 
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
