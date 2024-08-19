---
title: CSS Notes
permalink: /css/
sitemap: false
---

# Learning Web Design, 5d, Jennifer N. Robbins
***
# Chapter 11: Introducing CSS p. 239
## 7/28/2024
* Book arrived in mail on Friday 7/26.
* Up to p. 242
* JNR = shorthand for *Learning Web Design* by Jennifer N. Robbins

***
## 7/30/2024
* Three ways of attaching styles to a document
	1. Inline styles (most primitive, less modular/scalable, not recommended). e.g. `<h1 style="color : dark-grey">Chapter 1 </h1>`.
	1. Embedded style sheet where one places all styles within a `<style> ... </style>` block inside the HTML `<head>` section.
	1. External style sheet. Most scalable. Either imported via the 
		*  `<link rel="stylesheet" href="file.css">` in the `<head>` section
		* **#import** rule
* Got `st1.css` and `st2.css` working in proj3 directory. Used some sample templates from [SheCodes.io](https://palettes.shecodes.io).
* p. 242. syntax is **selector {**`declaration`**}**, where `declaration` = list of *property:value* pairs.

### Selectors p. 243
#### More detail in later chapters, but for now...
1. *Element-type* selectors include `<h1>` and `<p>` and `body`.
1. *ID* selectors select element based on **id** atributes. Indicated by `#` symbol.

***

### Conflicting Styles: The Cascade p. 249
* Priority, Specificity, Rule Order

### The Box Model p. 251

### Grouped Selectors p. 252

### Units of Measurement p. 253
* Absolute Units
	1. px - pixel, defined as 1/96 of an inch in CSS3  
	1. in - inches
	1. mm - millimeters
	1. cm - centimeters
	1. q - 0.25 mm
	1. pt - points (1/72 of an inch). Points are a unit commonly used in print design
	1. pc - picas (1 pica = 12 points aka 1/6 of an inch). Used in print design
* Relative Units
	1. em - unit of measurement equal to the capital letter **M** in the current font size
	1. ex - x-height, aka about the height of a lowercase **x** in the current font
	1. rem - aka *root em*, equal to the *em* size of the root element (html).
	1. ch - zero width, equal to the width of a **0** (zero) in the current font and size
* Relative Units - Viewport
	1. vw - viewport width, equal to 1/100 of the current viewport width
	1. vh - viewport height, equal to 1/100 of the current viewport height
	1. vmin - viewport minimum unit, equal to the value of **vw** or **vh**, whichever is smaller
	1. vmax - viewport maximum unit, equal to the value of **vw** or **vh**, whichever is larger
* More on **rem** unit p. 254
	* In modern browsers, the default root font size is **16 pixels**. 
	* Therefore, an element sized to 10rem would measure 160 pixels.
* More on **em** unit p. 254
	* In traditional publishing, the em is equal to the capital letter **M** in the current font size
	* In CSS, an *em* is calculated ad the distance between baselines when the font is set without any extra space between the lines (aka *leading*). 
	* The trick to working with *em* is to remember each em is always relevant to the current font size of the element it's in. e.g., if one sets a 2em left margin on an `<h1>`, `<h2>`, or `<p>`, those elements will not line up nicely becuse the em units are based on their respective element sizes. See Fig 11-11 on p. 255.

***

## 7/31/2024
### Viewport Percentage Length ( vw / vh ) p. 255
* Viewport Width (vw) and viewport height (vh) are relatvie to the size of the current viewport.
* 1 vw = 1/100 of the current width of the viewport
* 1 vh = 1/100 of the current height of the viewport
* Viewport based units are useful for ensuring that images and text elements stay full width or height of the viewport like so:

```css
header {
	width: 100 vw;
	height: 100 vh;
}
```

* The equivalent for ensuring that the header is always exactly 50% of the current viewport height and width is:

```css
header {
	width: 50 vw;
	height: 50 vh;
}
```

# Chapter 12: Formatting Text p. 261
* Use the `Black Goose Bistro` sample webpage from Chapter 5.
* Current work stored in `proj-3/_ch12/`

### A Word about Properties p. 262
#### This table explains how the book's formatting conveys information about how to understand CSS properties as laid out in this volume.
1. Values
1. Default
1. Applies to
1. Inherits
1. In addition, here are some CSS-wide keywords. All CSS properties accept the three CSS-wide keywords.
	1. initial - explicitly sets the property to it's default/initial value
	1. inherit - explicitly force an element to inherit a style property from its parent
	1. unset - erases declared values occurrin earlier in the cascade

### Font Names p. 263

### All about Web Fonts p. 264 - 265

### Generic Font Families p. 266
* How to stack font families p. 267

### Specifying Font Size p. 269
* Sizing text with relative values, aka *rem* values vs *em* measurements p. 270 - 272

### Bold, Italic, Small-Caps, etc.
* Bold = Font Weight p. 273
* Italic = Font Style p. 274
* Small Caps = Font Variant in CSS 2.1  p. 275
* Shortcut to consolidate fonts into the shorthand **font** property p. 276

## 8/06/2024
### Advanced Typography with CSS p. 277

### More selectors p. 281
* In the previous chapter, we saw how to group selectors together in a comma-separated list so we can apply properties to several elements at once.
* Here are examples of the selectors we've already covered:
	* Element selector `p { color: navy }`
	* Grouped selectors `p, ul, td, th { color: navy }`
* Of course, that's hard-coded and hard to maintain. So for more maintanable CSS, let's learn about 3 options: (1) descendant selectors, (2) ID selectors, (3) class selectors

#### Descendant Selectors p. 281
* A **descendent selector** targets elements that are contained within another element.
	* This is an example of a contextual selector.
	* See text box on p. 283 for other examples of contextual selectors: child selector, next-sibling selector, subsequent-sibling selectors
* For example, `li em { color: olive }` will apply an *olive* color only to the **emphasized (em)** lines (li) in the diagram on p. 282.
* Another example: `h1 em, h2 em, h3 em { color: red }` *only* targets emphasized elements that appear in h1, h2, or h3 headings.

#### ID Selectors p. 282
* Remember, the *id attribute* gives an element a unique name to identify that element.
* *id* is commonly used to give names andmeaning to **div** and **span** elements.
* When referring to a previously defined *id*, one uses the `#` hashtag/pound symbol. e.g., 

```html

<li id="cat1"> First Cat </li>
<!-- Below line references the desired id selector in CSS -->
```

```css
li#cat1 { color: olive }
```

* Because *id* values must be unique in each HTML document, one can omit the element name like so:

```css
#cat1 { color: red }
```

* One can use an `ID selector` as part of a *contextual selector*. in the below example, a style is applied only to `a` elements that appear within the element identified as *resources*.
* In this way, one can treat links in the element named 'resources' *differently* than all the other links on the page without any additional markup:

```css
#resources a { text-decoration: BOLD }
```

#### Class Selectors p. 284
* One last selector type: class selectors.
* Unlike *id elements* that must be uniquely named in a document, **class elements** can share the same name.
* Also, an element can belong to multiple classes at the same time.
* *Class elements* are indicated by a `.` prior to the name, just as *id element* are indicated by a `#`.
* e.g., to select *all* paragraphs (indicated by `<p>` in html) that have the class name `class="superman"` 

```css
p.superman { color: blue }
```

* To apply a property to *every* element of the same class, one omits the element name in the selector but **leave the period in**. Example:

```css
.superman { color: red }
```

## 8/09/2024
### Specificity 101 p. 284
* Review of priority and specificity of when multiple selectors seem to conflict. In order, beginning with the *least specific and important* and ending with the  **most specific** and **most powerful and overriding**.
	1. **Individual Element Selectors** - weakest
	1. **Class Selectors** - overrides individual element selectors but no one else
	1. **ID selectors** - override class selectors but weaker than inline
	1. **Inline styles** - most powerful and specific and override ID selectors and *everyone else*
* Furthermore, p. 284-285 has a checkbox system to determine the more complex rules
* Make sure to go back to checkboxes above and work out in a paper notebook *and* do Exercise 12-5 on p. 286 to Black Goose Bistro.

### Text Line Adjustments p. 287
* This section styles entire lines of text rather than individual words/characters.

#### Line Height p. 287
* property name: **line-height**
* values: number, length measurement, percentage, normal
* applies to: all elements
* Defines the minimum distance fromt eh baseline to the baseline in text. we saw it before as a shorthand **font** property.
* Note: **the baseline** refers to the imaginary line upon which the bottoms of characters sit.
* See visual examples on p. 287-288

#### Indents p. 288
* property name: **text-indent**
* values: length measurement, percentage, 
* default value: 0
* applies to: block containers
* This applies indenting, including the ability to do hanging indents. See Fig 12-13 on p. 289
 
```css
p#1 { text-indent: 2em; } 
p#2 { text-indent: 25%; } 
p#3 { text-indent: -35px; } /* hanging indent */
```

#### Horizontal Text Alignment p. 289
* property name: **text-align**
* values: left, right, center, justify, start, end
* default value: start
* applies to: block containers
 

#### Underlines and other "decorations" p. 289
* property name: **text-decoration**
* values: none, underline, overline, line-through, blink
* default value: none
* applies to: all elements
* **The most popular use of `text-decoration` is *removing the underline in HTML hyperlinks*.**, e.g., `a { text-decoration: none; }`.

### Capitalization features p. 291-292
* property name: **text-transform**

#### Spacing of text between each character p. 292
* property name 1: **letter-spacing**
* property name 2: **word-spacing**

#### Text Shadow p. 293
* property name: **text-shadow**
* values: `horizontal offset, vertical offset, blur radius, color`, `none`
* default value: none
* applies to: all elements

### Many other text properties
* See box on p. 294
* partial list: white-space, vertical-align, word-break / line-break, text-justify, text-align-last, tab-size, hyphens, overflow-wrap, hanging-punctuation, direction, etc.

## 8/10/2024
### Completed Exercises 12-5 and 12-6
* Exercise 12-5 p. 286
* Exercise 12-6 p. 295

### Changing List Bullets and Numbers 
* p. 296 - 298

# Chapter 13: Colors and Backgrounds p. 303
* Color names p. 304. There are 140 standard colornames, per JNR as well as per the [HTMLColorCodes](https://htmlcolorcodes.com/color-names/) site: "Modern browsers support 140 named colors, which are listed below. Use them in your HTML and CSS by name, Hex color code or RGB value."
* Handy table listing all 140 colors, with associated RGB and hex values on p. 305 of JNR.
* Intro to RGB and Hex Colors p. 306-308.

### RGBa Color p. 309
* How to use 4th value to specify alpha channel aka transparaency.
* HSL (hue, saturation, lightness) equivalent is HSLa alpha channel on p. 311.

### Foreground Color p. 311
* Equivalent to text and border of an element.
* Consider the 'outline' color in PowerPoint or Apple iOS Image Editor

#### Color p. 311 - 312
* property name: **color**
* values: color value (css color names OR rgb OR hex number)
* default value: depends on browser/user preferences
* applies to: all elements

#### Example p. 312
* See image on p. 312

```css
blockquote {
	border: 4px dashed;
	color: green;
}
```

```html
<blockquote>
In the latitude of central New England, cabbages are note secure.
</blockquote>
```

### Background Color p. 312 - 314
* property name: **background-color**
* values: color value (css color names OR rgb OR hex number) \| transparent
* default value: transparent
* applies to: all elements

#### Other notes
* Bg color fills the **canvas** behind the element, plus any padding / extra space.
* Let's apply this to the `blockquote` above with this style: 

```css
blockquote {
	border: 4px dashed;
	color: green;
	background-color: #c6de89;
}
```
#### Example of marking up specific text elements p. 313
* In this HTML example... 

```html
<p>
Every variety of cabbage had their origin in the wild cabbage of Europe (
	<dfn class="glossary"><i>Brassica oleracea</i></dfn>
)
<p>
```
* ...the `<dfn>` element has a classname= *glossary*, which can be specifically targeted by this CSS:

```css
.glossary {
	color: #0378a9; /* blue */
	background-color: yellow;
}
```

#### Background Clipping p. 314
* property name: **background-clip**
* values: border-box \| padding-box \| content-box
* default value: border-box
* applies to: all elements

#### Other notes
* See Fig 13-12 on p. 314 for visuals of border-box, padding-box, and content-box.

### Opacity p. 315

#### Opacity property
* property name: **opacity**
* values: *number* from 0 to 1
* default value: 1
* applies to: all elements

## 8/11/2024
### Pseudo-Class Selectors p.316-320
* Note: A text-box in the left side column of page 316 summarizes the selectors JNR has covered so far.
* The concept of pseudo-class selectors refers to dynamic states of various potential classes, like whether a hyperlink `<a>` has been clicked, whether something has `focus` right now or not, or if there is a pointer `onHover` at the moment.
* **Pseudo-classes are denoted by the `:` colon prefix before the desired pseudo-class**. p. 316

#### Example: `<a>` HyperLink Pseudo-Class p. 316
* This css makes sure that unclicked links are colored *crimson* while links that have been clicked are colored *silver*:

```css
a:link {
	color: crimson;
}

a:visited {
	color: silver;
}
```

#### Focus State p. 317
* In this example, when a user selects a text input in a form, it gets a yellow background color to make it stand out from other form inputs:

```css
input:focus {
	background-color: yellow;
}
```

#### Hover State p. 317
* Hover states occur when mouse or other pointers glide over an element.
* Most commoly used to let user know that some action is possible.
* Also used to trigger pop-up menus for navigation or tooltips.
* Example which gives hyperlinks a light pink background color while the mouse hovers over them:

```css
a:hover {
	color: crimson;
	background-color: #ffd9d9;
}
```

* this css makes sure that underlines for a hyperlink only occurs on hover:

```css
a:hover {
	text-decoration: underline;
}
```

* See also box on using Hover on Touch Devices on p. 318. Hover doesn't really work the same way on mobile and other touch devices.

## 8/18/2024
### Putting it all together p. 318
* When one applies styles to an **a** element with all five *pseudo-classes*, the order in which these pseudo-classes appear is IMPORTANT.
* Example: if one puts **:link** or **:visited** last, they will *override* the states listed before them.
* The required order for link pseudo-classes is:
	1. **:link**
	2. **:visited**
	3. **:focus**
	4. **:hover**
	5. **:active**
* It is recommended that one provides a *:focus* style for users who use the keyboard to tab through the links on a page. p. 319
* See visual example Fig 13-14 on p. 319 which demonstrates the result of this css:

```css
a { text-decoration: none; }
a:link { color: maroon; }
a:visited { color: gray; }
a:focus { color: maroon; background-color: #ffd9d9; }
a:hover { color: maroon; background-color: #ffd9d9; }
a:active { color: red; background-color: #ffd9d9; }
```
***

### Pseudo-Element Selectors p. 320
* There are *four pseudo-elements* that act as though they are inserting ficional elements into the document structure.
* **In CSS3, Pseudo-elements are indicated by a `::` double-colon.** p. 320 (However, many browsers support the single-colon `:` syntax used for pseudo-elements in CSS2 for backward compatibility.)

#### First Letter, First Line p. 320
* See Fig 13-15 on p. 321 to see visually how this css code renders:

```css
p::first-line { letter-spacing: 9px; }
p::first-letter { font-size: 300%; color: orange; }
```

#### Generated content with ::before and ::after p. 321
* Bullets and list numbers are examples of *generated content* which is not included in the HTML source.
* Generated content can include icons before list icons, to display URLs next to links when a web document is printed into hard copy, to add language appropriate quotation marks around a quote, and much more.
* See Figure 13-16 on p. 322 to see how the below CSS + HTML renders:

##### CSS
```css
p.warning::before {
	content: url(exclamation.png);
	margin-right: 6px;
}

p.warning::after {
	content: " Thank you.";
	color: red;
}
```

##### HTML
```html
<p class="warning">We are required to warn you that undercooked food is a health risk.</p>
```
***

### Attribute Selectors p. 323
* Attribute selectors target elements based on attribute names or values. 
* In fact, ***class selectors* and *ID selectors* are just special cases of the broader category of *attribute selectors***. (text box on the right rail of p. 323)
* List of Attribute Selector Syntax p. 323 - 324
	1. **Simple attribute selector** - example: `img[title] {border: 3px solid;}`
	2. **Exact attribute selector** - example: `img[title="soccer-team"] {border: 3px solid;}`
	3. **Partial attribute value selector** - example: `img[title~="team"] {border: 3px solid;}` -- to find *any* string with team
	4. **Hyphen-separated attribute value selector** - uses vertical bar `|` to search for multiple variations, e.g., for English-US, English-UK, English-Australian, we might do something like `text[lang|="en"] {border: 3px}` which would target **en-us**, **en-uk**, and **en-au-tas**, respectively.
	5. **Beginning substring attribute value selector** - example: `img[src^="/images/icons"] {border: 3px solid;}`
	6. **Ending substring attribute value selector** - example: `img[filetype$=".pdf"] {border: 3px solid;}`
	7. **Arbitrary substring attribute value selector** - example: `img[title*="February"] {border: 3px solid;}`

***
### Background Images p. 324
#### Adding a Background Image p. 324
* property name: **background-image**
* values: url(*location of image*) \| none
* default value: none
* applies to: all elements

#### Repeated, tiled background p. 328
* property name: **background-repeat**
* values: repeat \| no-repeat \| repeat-x \| repeat-y \| space \| round
* default value: repeat
* applies to: all elements
* Additional notes:
	* **repeat-x**: repeat horizontally only 
	* **repeat-y**: repeat vertically only 
	* **space**: browser calculates how many background images an fit aross the width and height of the background area and adds equal amounts of space between the image. Leads to cropped images on the edges.
	* **round**: browser makes sure repeated image ends at the right location on the edge but distortions. see pictures in Fig 13-21 on p. 329. 

#### Position of background image p. 331
* See also textbox on left side of p. 332 - *background image **offset***.
* Background Position Origin on p. 333
* **Background Attachment** allows the image to *"float"* such that it stays in the center of the visible browser window even when the user scrolls up/down the page.
* *Background Size* sets the desired size of the background image. Without invoking this property, bg-images will always render at original dimensions/size of the source image. p. 336

### Shorthand Background Property p. 338
* Handy property that can specify *all* background styles in one shot
* property name: **background**
* values: background-color, background-image, background-repeat, background-attachment, background-position,  background-origin, background-size
* default value: *see individual properties for their respective defaults*
* applies to: all elements
* Example on p. 338 -- concise version

```css
body {
  background: white 
              url(source.png)
              no-repeat
              right
              top
              fixed;
}
```              

* Replaces this wordy version on p. 338 with same output

```css
body {
  background-color: white;
  background-image: url(source.png);
  background-repeat: no-repeat;
  background-position: right top;
  background-attachment: fixed;
}
```

* All of the property values for background are optional and may appear *in any order*. 
* To place multiple different background source images on the same viewport, see **multiple backgrounds** on p. 339.

### Gradients p. 340 - 348

***
### Finally, External Style Sheets p. 348 - 351
* External style sheets are by far the most powerful way to use CSS. p. 348


***

## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.

`<script>`
