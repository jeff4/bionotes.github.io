---
title: Vue.js Notes
permalink: /gvu/
sitemap: false
---

# Beginning Vue 3 Development
* Subtitle: Learn Vue.JS 3 Web Development
* Author: Greg Lim, Twitter: @greglim81
* Published: November, 2022
* 147 Pages
* Kindle max location number: 3051
* JH shorthand = GVU = Greg VUe


***
## 8/26/2024
* get started with GVU book.
* Up to location 117/3051
* Also began watching the 3-hour [Vue.js Crash Course 2024](https://www.youtube.com/watch?v=VeNfHj6MhgA) by Traversy Media. Up to 17:17 rn.
* Began going through [Vue Intro docs](https://vuejs.org/guide/introduction.html)

## Notes on Vue.JS docs
### Single-File Components
* A `*.vue` file is a SFC (Single-File Component) file that is similar to HTML.
* It must consist of three parts:
	1. Logic -- **JavaScript** in the `/* script */` section
	1. Content -- **HTML** in the `/* template */` section
	1. Styling -- **CSS** in the `/* style */` section
* of course, a regular HTML document has *script* and *style* sections to hold onto parts 1 and 3 respectively. So as we can see, SFC / *.vue files are very similar to `*.html` files.
* Per my reading of this [Composition API FAQ](https://vuejs.org/guide/extras/composition-api-faq), i believe i'll just go with the classic **Options API** for now b/c i'm mostly doing small and simple projects for now. However, at some point, I may learn the **Composition API** as well. Or go directly to React. That article also has a nice comparison of the Vue Composition API vs. React Hooks.
* Sped through the [vue.js tutorial](https://vuejs.org/tutorial/#step-1)
* Built my own vue app with the [quick start](https://vuejs.org/guide/quick-start.html)
    * see ~/champ/proj-3/vue1

### Deprecated next steps
1. Install coc using :PlugInstall using [these instructions](https://dev.to/rajikaimal/vim-auto-completion-with-coc-nvim-ie3). Not needed anymore b/c I'm using neovim.
2. See also [IDE support page](https://vuejs.org/guide/scaling-up/tooling.html#ide-support)
3. install coc-volar
4. continue with [vue core docs](https://vuejs.org/guide/essentials/application.html)

***

## 9/01/2024
* Made a lot of progress, as can be seen through the [vim](/vim) and [git](/git-notes/) pages. Got neovim working, set up new repo, everything is synching properly. Now to decide which tutorials to use and which initial app to build.
* Also learned more about Vite. See ChatGPT dialogue from this date.
* Another tutorial i'm checking out is the [2-hour crash course](https://www.youtube.com/watch?v=KTFH4P8unUQ) by John Komarnicki
	* Code is available at his [GH repo](https://github.com/johnkomarnicki/vue-3-crash-course).
	* His sample app is called [Vue Todos](https://sparkling-platypus-7955f2.netlify.app/)

### Examining HelloWorld.vue
* Looking at this SFC, John introduces [props](https://youtu.be/KTFH4P8unUQ?si=pfcUFgfnq_mqNoFj&t=978), which is how messages are passed between SFCs. Within the **\<script\>** area, the **defineProps()** function has a list of different properties. In this case, 

```typescript
defineProps({
  msg: {
    type: String,
    required: true,
  }
}) 
```

* That **msg** is then passed into the *template* aka *html* section within the 'handlebar moustaches' (double `{{}}`). like so:

```html
<h1 class="green">{{ msg }}</h1>
```

### Examining TheWelcome.vue
* At [17:26](https://youtu.be/KTFH4P8unUQ?si=i2cL9uApvAMKX_A7&t=1046), John talks about the `#heading` and `#icon` attributes modifying the **\<template\>** element in *WelcomeItem*.  
* These are **named slots**. They are references to content contained in the **WelcomeItem.vue** file.

### Examining /src/router/index.js
* At [18:36](https://youtu.be/KTFH4P8unUQ?si=Q-iH5DCXJOjNO8bf&t=1116), talk about the index.js file in the router directory. doesn't seem to exist in my copy. 
* Hm, neither `/router/index.js` nor the `*.vue` files stored in `/src/views/` directory seem to exist. i.e., both the `/router` and `/views` subdirectories are missing.

### 
