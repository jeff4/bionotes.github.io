---
title: Front End JavaScript
permalink: /fe-js/
sitemap: false
---

## WebJS / Client JS / Front End JavaScript

***

## 7/16/2024
## Flanagan Chapter 15 Web Programming p. 713
* aka front-end or client-side JS

### 15.1.1 JS inside HTML `<script>` tags
* Although one can place JS code directly in-line within an HTML page, it's far more common now to use the **src** attribute of the `<script>` tag like so: 

```html
<script src="client-scripts/digitalClock.js"></script>
```

* Important note: HTML does *not* support this concise syntax `<script/>`. One must *always* have an opening and closing script tag like so: `<script> </script>`.
* p. 718-719. When importing JS modules, one must load the top-level module with the **type="module"** of the `<script>` tag. See section 10.3.5 for complete detials.

#### No languages supported other than JS p. 719
* Back in the 90s, there was a thought that non-JS languages would be supported, leading to the **langauge="javascript"** and **type="application/javascript"** attributes of the `<script>` tag. 
* Turns out that is not needed b/c JS is the only language of the web. So basically can ignore the `language=` and `type=` attributes of script with the possible exception of embedding live data in a web page.

#### 'defer' and 'async' attributes of the <script> tag
* In the 90s before formalization of the DOM, JS modified HTML page content using the **document.write()** method.
* Back then, `document.write()` tag would execute wherever it is in the HTML page. One hack people used to do was to place all the documents.write() statements at the bottom of the page. 
	* This way, JS would only execute after the other HTML content had first loaded in the client browser.
* That style is now deprecated, esp. since a `<script>` with a **document.write()** statement placed in *the middle* of an HTML page would **blocking** aka **synchronous**. (see p. 720.)
* Solution: introducing the **async** and **defer** attributes as part of the `<script>` tag.
	* Getting conflicting (possibly wrong) answers from ChatGPT about when **async** and **defer** were introduced. 
	* For now, let's assume that browsers started supporting them around 2009, was formally supported as a 'W3C Recommendation' in October 2014.
* Syntax:

```html
<script defer src="deferred.js"></script>
<script async src="async.js"></script>
```

* Note, per this [phind.com answer](https://www.phind.com/search?cache=j3l4x7oq4j2f8ktvtyqibe8w), one can place the **defer** and **async** attributes after the **src=** attribute. Like so:

```html
<script src="deferred.js" defer ></script>
<script src="async.js" async ></script>
```
* Both defer and async are ways of telling the browser that the linked script does not use `document.write()` to generate HTML output.
	* Therefore, the browser can continue to parse and render the document while simultaneously downloading the script.
* **The defer attribute** of the `<script>` tag causes the browser to defer execution of the script until after the document has been fully loaded and is ready to be manipulated.
* **The async attribute** of the `<script>` tag causes the browser to run the script as soon as possible but *does not block document parsing while the JS is being downloaded* to the client browser.
* If a `<script>` tag has both attributes, the **async** attribute takes precedence.
* Scripts with the **type="module"** attribute are automatically executed after the document has been downloaded to the client; as if it had the **defer** attribute. This can be overridden by paring type=module with an **async** attribute in the same `<script>` tag.

***

## 7/17/2024 - More Flanagan
### 15.1.2 Brief intro to the DOM p. 722

* Short intro; there is much more detail on the DOM in Section 15.3 (p. 760).
* The DOM API mirrors the tree structure of an HTML document. 
* For every HTML tag in the document, there is a corresponding JS *Element* object.
* For every run of text in the HTML document, there is a corresponding JS *Text* object.
* The *Element*,*Text*, and *Document* classes are all subclasses of the **Node** superclass.
* *Node* objects are organized into a tree structure that JS can query and traverse using the DOM API.
* The DOM API includes methods for creating new **Element** and **Text** nodes, inserting them into the document as children of other **Element** objects, moving them around the document, and for deleting them from the document.
* There is a JS class that corresponds to every single HTML tag type.
* Each occurrence of a tag in a document is represented by an instance of the class. Examples:
* The HTML `<body>` tag is represented by an instance of the JS **HTMLBodyElement** class.
* The HTML `<table>` tag is represented by an instance of the JS **HTMLTableElement** class.
* The HTML `<img>` tag is represented by an instance of the JS **HTMLImageElement** class. Note also that HTMLImage has a JS `src` property that corresponds to the *src* attribute of the HTML `<img>` tag.

### 15.1.3 The Global Object in Client Browsers
* There is one global object per browser or tab.
* All the JS code running in that window shares that same global object.
* This is true regardless of how many scripts or modules in the document. Furthermore, that means that any property is visible to all other scripts.
* The global object is where the JS standard library is defined, including the **parse()** function, the `Math` object, the `Set` class, etc.
* The **document** JS property of the window's global object represents the currently displayed document.
* The global object's **fetch()** method makes http network requests.
* The global object's **Audio()** constructor allows JS programs to play sounds.
* In web browsers, the global object does double duty. In addition to defining built-in types and functions, the global object also represnts the current web browser window.
* The global object defines properties like **history** (represent the window's browsing history, see Section 15.10.2), **innerWidth** (window's current width in pixels).
* A critical property of the global object is named **window**, and the value is the global object itself.
	* This means you can simply type `window` to refer to the global object in your client-side code.
	* When using window-specific features, it is often good to include the `window.`- prefix. eg, `window.innerWidth` is clearer than just `innerWidth`.

### 15.1.4 Scripts all share a namespace p. 727
* Module-based scripts are clean b/c functions, classes, variabless, etc are private to their module. (Unless one of those items are explicitly exported with the `export` or `object.export` keywords.)
* In contrast, non-module scripts all share the same global namespace of a document.
	* This can be convenient for small JS programs, but once you include 3rd-party libraries, it all becomes a mess.
* This is one reason to use `let`, `class`, and `const` from ES6. 
	* Unlike the legacy `var` and `function` declarations which create properties on the shared global object, modern keywords do not create properties on the global object.
	* **Note:** however `let`, `class`, and `const` *still* live in the shared namespace.

### 15.1.5 Execution of JS programs p. 728
* There is no formal definition of a 'program' in client-side JS.
* But in general, a JS program consists of all the bits of JS code within or referenced from a single HTML document.
* All of these separate bits of code share a single global **Window** object; they all have access to the same underlying **Document** object.
* Scripts that are not modules also share a top-level namespace.

#### iFrames p. 728-729
* If a webpage includes an embedded frame (i.e., using the `<iframe`> element), the JS code in the embedded document has a *different global object* than the enclosing window.
	* Thus, the iframe also has a distinct Document object and global object from the enclosing window.
* However, if the container document and the contained document are both loaded from the same server, the code in one document can interact with the code in the other document.
* See Section 15.13.6 (p. 957) for more info on how to send messages can be passed between JS in the containing window and the JS in the contained iframe.

#### Sequence p. 729
* One can think of JS program execution as occurring in two phases.

#### Phase 1
* The document content is loaded, and the code from the `<script>` elements is run.
	1. Scripts generally run in the order in they are placed in the doc (modulo **defer** and **async** attributes of the `<script>` tag).
	1. The JS code within any single script is run from top to bottom, subject to standard JS control-flow.
	1. Some non-obvious things might happen like the creation/loading of various classes and objects so they are available for Phase 2.

#### Phase 2
* After the document is loaded and all scripts have run, then the asynch and event-driven part of JS execution starts.
	1. If a script is going to be active in Phase 2, then one of the things it must have done during Phase 1 is to register at least *one* event handler or callback function that will be invoked async.
	1. During the event-driven Phase 2, the browser invokes event handler functions and other callbacks in response to things that happen asynch.
	1. Event handlers are most commonly invoked in response to user input (mouse clicks, keystrokes, etc.) but also by network activity, resource loading, elapsed time, or errors in JS
	1. For more on events and event handlers, see Section 15.2.

#### More on Phase 2 events p. 730
* Some of the first events to happen in Phase 2 are the **DOMContentLoaded** and **load** events.
	* *DOMContentLoaded* is triggered when the HTML document has been completely loaded and parsed.
	* The *load* event is triggered when all the document's external resources (e.g., images) are also fully loadd.
* JS programs often use one of the above events as a trigger or starting signal.
* It is common to see programs whose scripts define functions but take no action other than registering and event handler function to be triggered by the *load* event at the beginning of Phase 2.
	* This *load* event handler than manipulates teh document and does whatever it is that the program is supposed to do.
* Note: it is common in JS programming for an event handler function such as *load* to register yet other event handler functions.
* Phase 1 is relatively short, and should ideally be less than 1 second.
* Once a document is loaded, Phase 2 lasts as long as the document is displayed in the web browser.

### Client-Side JS Threading Model p. 731
* JS is a single threaded language. Single-threaded execution makes for simpler programming.
* One can assume that two event handlers will *never* run at the same time.
* One can manipulate the document knowing that no other thread is attempting to modify it at the same time.
* One never need worry about race conditions etc. when writing JS code.
* Single-threaded execution means that web browsers stop responding to user input while scripts and event handlers are executing.
* However, this means that JS programmers have to be careful to keep their execution times short b/c they don't want the user to be waiting while their page hangs.
	* If an event handler performs a computationally intensive task, the browser may become nonresponsive, possibly causing the user to think that it has crashed.

#### Web workers p. 731
* The web platform defines a controlled form of concurrency called a **web worker**.
* A web worker is a background thread for performing computationally intensive tasks without freeing the UI.
* The code that runs in a web worker thread does not have access ot document content. 
	* Web worker JS does not share any state with the main thread or with other workers.    
	* Web worker JS can only communicate with the main thread and other workers through asynch message events so that concurrency is not detctable in the main thread.
* Thus, **web workers do *not* change the single-threaded execution model** of JS.
* See Section 15.13 for more on safe threading and web workers.

#### Client-Side JS Timeline p.732
##### More detailed breakdown of the steps in a client-side web page live, more granular than the *Phase 1* and *Phase 2* distinction from above.
1. The web browser creates a **Document object** and begins parsing the web page, adding **Element objects** and **Text nodes** to the document as it parses HTML elements and their textual content. The `document.readyState` property has the value *loading* at this stage. 
1. When the HTML parser encounters a **`<script>`** tag that does not have any of the *async*, *defer*, or *type="module"* attributes, it adds that script tag to the document and then executes the script. 
	* The script is executed synchronously, and the HTML parser pauses while the script downloads (if necessary) and runs. 
	* A script like this can use **document.write()** to insert text into the input stream, and that text will become part of the document when the parser resumes. 
	* A script like this often simply defines functions and registers event handlers for later use, but it can traverse and manipulate the document tree as it exists at that time. 
	* That is, non-module scripts that do not have an *async* or *defer* attribute can see their own `<script>` tag and document content that comes before it.
1. When the parser encounters a `<script>` element that has the async attribute set, it begins downloading the script text (and if the script is a module, it also recursively downloads all of the script’s dependencies) and continues parsing the document. 
	* The script will be executed as soon as possible after it has downloaded. 
	* But the parser does not stop and wait for it to download. 
	* Asynchronous scripts must *not* use the **document.write()** method. They can see their own `<script>` tag and all document content that comes before it, and may or may not have access to additional document content.
1. When the document is completely parsed, the **document.readyState** property changes its value to *interactive*.
1. Any scripts that had the *defer* attribute set--along with any module scripts that do *not* have the *async* attribute--are executed in the order in which they appear in the document.
	* Async scripts may also be executed at this time.
	* Deferred scripts now have access to the complete document and they must *not* use the **document.write()** method.
1. The browser fires a **DOMContentLoaded** event on the **Document** object.
	* This marks the transition from Phase 1 to Phase 2.
	* Note, however, that there may still be *async* scripts that have not yet executed at this point.
1. Phase 2 is in full swing. The document is fully parsed at this point.
	* But the client browser may still be waiting for additional content, such as images, to load.
	* When all such content finishes loading, and when all *async* scripts have loaded and executed, the **document.readyState** property changes state to *complete* and the browser now fires the *load* event on the **Window** object.
1. From this point on, event handlers are invoked asynchronously in reponse to user input events, network events, timer expirations, etc.

### 15.1.6 Program Input/Output p. 734
* Like any program, client-side JS programs process input data and then produce output data. Here are some types of input:
	1. The content of the document itslef, which the JS code can access via the DOM API.
	1. User input in the form of events. The HTML **`<button>`** element may respond to mouse clicks or touchscreen taps. Or, the HTML **`<textarea>`** element may accept text input. See Section 15.2 for more.
	1. The URL of the document being displayed is available to client-side JS as the **document.URL**. If one passes this string to the **URL()** constructor (Section 11.9), one can easily access the path, query-string, and other sections of the URL.
	1. The content of the http *Cookie* request header is available to the client-side code as **document.cookie**.
		* Cookies are usually used by server-side code to maintain user ssessions but client-side code can also use them when needed.
		* See Section 15.12.2 (p. 932) for more.
	1. The global **navigator** property provides access to info about the web browser, the OS it's running on, and the capabilities of each. For example:
		* **navigator.userAgent** is a string that identifies the web browser.
		* **navigator.language** is the user's preferred language.
		* **navigator.hardwareConcurrency** returns the number of logical CPUs available to the web browser
		* the global **screen** property provides access to the user's display size via the **screen.width** and **screen.height** properties.
		* In a sense, the **navigator** and **screen** objects are to web browsers as environment variables are to Node programs.

#### JS client-side output p. 735
* Client-side JS typically provides output by manipulating the DOM api; or by using a framework like React, Angular, Vue, Next.JS to manipulate the document.
* Client-side code can also use **console.log()** and related methods to produce output. 
	* **Note:** *console.log()* output can only be viewed in the developer tools console. So this is useful for debugging that is hidden from end-users.

### JS Program Errors p. 735
* Unlike Node applications and other apps running directly on the OS, a JS program in a web browser can't really 'crash'.
* If an exception occurs while your client-side JS is running and you do not have a **try/catch** statement to handle it, an error message will be displayed to the dev tools console.
	* **But**, any event handlers that have ben registered keep running and responding to events. 
* To define an error handler of last resort, set the **onError** property of the *Window* object to an error handler function.o
* for more on handling of Promises and managing the call stack, view p. 735-736.

***

### 15.1.8 The Web Security Model p. 737
* There are two competing goals that browser-makers try to balance:
	1. Preventing malicious code from running that can read or alter user data, compromise user privacy, etc.
	1. Make client-side APIs powerful and effective for building web apps.

#### What JS Can't Do p. 737
* The first line of defense is that some web browsers simply don't support certain capabilities. 
* E.g., client-side JS does not provide any way to write or delete arbitrary files or list arbitrary directories on the client computer.
* This means that the vanilla JS cannot simply delete data or plant viruses.
* Furthermore, client-side JS does not have general networking capabilities. Although there APIs like the below, general-purpose internet clients and servers cannot be written with client-side JS. 
	* A client-side JS program can make (only?) make http requests. (Section 15.11.1 for more.)
	* The WebSockets API defines a socket-like affordance for communicating with specialized servers (Section 15.11.3)

#### Same-Origin Policy p. 738
* The *same-origin policy* is a sweeping security restriction of what web content JS code can interact with.
* It typically comes into play when a web page includes `<iframe>` elements.
* In this case, the same-origin policy governs the interactions of JS code in one frame with the content in other iframes.
* The origin of a document is defined as the protocol, the host, and the port of the URL from which the document was loaded.
* Documents loaded from different web servers have different origins; documents loaded via different ports on the same host also have different origins.
* A document loaded with the `http:` protocol has a different origin than the `https:` protocol even if they come from the same web server.
* Browsers typically treat every **file:URL** as a separate origin.
* **Note:** the origin of the script is not relevant to the same-origin policy. What matters is the orign of the **document** in which the script is embedded. (see p. 738-739 for more.)
* The same-origin policy poses problems for large websites with multiple subdomains like *www.example.com* and *store.example.com*. Two solutions:
	1. Alter their origin by setting the **document.domain** to the domain suffix.
	1. **CORS** aka Cross-Origin Resource Sharing 

***

## 7/18/2024
* Tested xss scripting example below on localhost with `live-server` and it worked.

#### Cross-Site Scripting p. 740
* **XSS** aka **cross-site scripting** is a term for a category of security issues in which an attacker injects HTML tags or scripts into a target website.
* Front-end devs must guard against XSS.
* A web page is vulnerable to XSS if it dynamically generates document content and bases that content on user-submitted data without first *sanitizing* that data by removing any embedded HTML tags from it.
* As a trivial example, consider the following HTML page that uses JS to greet users by name:

`<script>`

```javascript
let userName = new URL(document.URL).searchParams.get("userName");
document.querySelector('h1').innerHTML = "Hello " + userName;

```

`</script>`
* The 2-line script extracts input from the "userName" query parameter of the document URL.
* It then uses the DOM API to inject an HTML string inot the first `<h1>` tag in the document.
* The page is intended to be invoked with an URL like this: `http://www.example.com/greet.html?userName=Jeff`.
* When used likje this, it displays the text "Hello Jeff". 
* **But**, consider what happens when it is invoked with this query parameter `userName=%3Cimg%20src=%22x.png%22%20onload=%22alert(%27hacked%27)%22/%3E`. When the URL-escaped parameters are deoded, the URL causes this HTML to be injected into the document: `Hello <img src="x.png" onload="alert('hacked')"/>`.
	* After the image loads, the string of JS in the **onload** attribute is executed and the global **alert()** function displays a modal dialogue window to appear.
	* Of course, a single dialog box is relatively benign, but demonstrates that arbitrary code execution is possible on this site b/c it allows unsanitized HTML.
* XSS is called this b/c more than one site is involved.
	* Site B includes a specially created link to Site A.
	* If Site B can convince users that that it is a legit site and they can click the Site B lin, they will be taken to Site A--**but now Site A will be running code from Site B**!
	* Exploit 1: deface the page or cause other malfuctions on Site A.
	* Exploit 2: Even worse, can read account info and other stuff from cookies stored by Site A, sending that data back to Site B.
	* Exploit 3: Injected code could even track user keystrokes and send that data back to Site B.
* **Solution I:** replace special HTML characters in untrusted input string with their equivalent HTML entities. (see example on p. 741-742.
* **Solution II:** Structure web app so that untrusted content is always displayed in an `<iframe>` with the **sandbox** HTML attribute set to disable scripting and other capabilities.

***

### 15.2 Events p. 742
* Client-side JS use an async, event-driven programming model. This means that the browser generates an **event** every time something interesting happens to the document, browser, or associated element/object.
* In client-side JS, events can occur on any element within an HTML document. This means that web browsers are *more complicated than Node programming*.

#### Definitions related to events p. 743 - 745
1. **Event Type** aka **Event Name**
	* This string specifies what kind of event occurred. 
	* For example, *type* **mousemove** means that the user has moved the mouse. 
	* The *type* **keydown** means that the user has pressed a key on the keyboard down.  
	* The *type* **load** means that a document or some other resource has finished loading on the client from the network.
	* B/c the type of an event is just a string, it's sometimes called an *event name*.
1. **Event Target**
	* This is the object upon which the event occurred or with which an event is associated.
	* When we speak of an event, we must specify both the type and the target
	* A **load** event *on* a `Window`, for example, or a **click** event *on* a `<button>` element.
	* The most common event targets are Window, Document, and Element objects.
	* Other targets include **Worker objects** (see Section 15.13 on threads). Workers are targeted by *message* events when a worker thread sends a message to the main thread.
1. **Event Handler** aka **Event Listener**
	* This function handles or responds to an event. Applications register their event handler functions with the web browser, specifying *event types* and *event targets*. 
	* When an event of the specified type occurs on the specified target, the browser invokes the handler function.
	* When event handlers are invoked for an object, we say that the browser has 'fired', 'triggered', or 'dispatched' the event.
	* There are a number of ways to register event handlers; see Sections 15.2.2 and 15.2.3 for more.
1. **Event Object**
	* Event objects are associated with a particular event and contains details about that event.
	* Event objects are passed as arguments to the event handler function.
	* All event objects have a **type property** that specifies the event type and a **target property** specifying the event target.
	* Each event type defines a set of properties for its associated event objects.
	* e.g., a *mouse event object* includes coordinates of the mouse pointer.
	* e.g., a *keyboard event object* includes key pressed and associated modifier keys that were also pressed.
1. **Event Propagation**
	* Event propagation is the process by which a browser decides which objects to trigger event handlers on.
	* For events that are specific to a single object--such as the **load** event on the *Window* object or a **message** event on a *Worker* object--no propagation is required.
	* But when certain kinds of events occur on elements within the HTML document, they propagate up the document tree.
		* If the user moves the mouse over a hyperlink, the **mousemove** event is first fired on the `<a>` element that defines the linke. 
		* *Then*, the event is fired on the containing elements: perhaps a `<p>` element, a `<section>` element, or the Document object itself.
	* It is sometimes more convenient to register a single event handler on a Document or some other container element than to register handlers on each individual element you're interested in.
	* An event handler can stop the propagation of an event so that it will not continue to bubble and will not trigger handlers on containing elements.
	* Handlers do this by invoking a a method of the event object.
	* In another form of event propagation, known as **event capturing**, handlers specially registered on container elements have the opportunity to intercept (aka *capture*( events before they are delivered to their actual target. See Section 15.2.4 for more.
1. **Default Actions**
* Some events have default actions associated with them. 
* e.g., when a click event occurs on a hyper link, the default action is for the browser to follow the link and load a new page. Event handlers can prevent the default action by invoking a method for the event object.
	* This is called **cancelling** the event. See Section 15.2.5

## 7/19/2024
### 15.2.1 Event Categories
##### Client-side JS suppports so many *event types* that this chapter will not cover them all. However, this book will group events into a few common categories.
1. **Device-dependent input events** 
	* Examples: mousedown, mousemove, mouseup, touchstart, touchmove, touchend, keydown, keyup
1. **Device-independent input events** Events that are device agnostic. e.g., 
	* The *click* event indicates that a link or button (or other document element has been activated. This activation can come from a mouse click, a keyboard, or with a tap on a touch screen.
	* The *input* event is a device-independent superclass of keydown which supports keyboard input, as well as cut-and-paste, and methods used for ideogram based scripts like Chinese.
	* The *pointerdown*, *pointermove*, and *pointerup* event types are device-independent alternatives to mouse and touch events, which respond to pointers, touch-screens, pen- and stylus- inputs.
1. **User Interface events** aka UI events are higher-level events. Often on HTML form elements.
	* *Focus* event is when a text input field gains keyboard focus.
	* *Change* event is when a user changes the value displayed by a form element.
	* *Submit* event is when a user clicks a **Submit** button in a form.
1. **State-change events**
	* Events from network or browser activity; not from user input.
	* Example: **load** fired by the *Window* object after a document finishes loading.
	* Example: **DOMContentLoaded** fired by the *Document* object after a document finishes loading.
	* Also, browsers fire *online* and *offline* events on the Window object when network connectivity changes.
	* Example: **popstate** event is fired by the browser's history management mechanism in response to the browser's Back button (See 15.10.4).
1. **API-specific events**
	* A number of web APIs defined by HTML and related specs include their own event types.
	* The HTML `<video>` and `<audio>` elements define a long list of associated event types such as *waiting*, *playing*, *seeking*, *volumechange*, etc. for media playback.
	* Generally speaking, web platform APIs that are async and were developed before **Promises** were added to JS are event-based and define API-specific events.
	* Example: The **IndexedDB API** fires *success* and *error* events when database requests succeed or fail.
	* Although the new **fetch() API** for making HTTP requests is Promise-based, it replaced the old XMLHttpRequest API which itself defined several API-spcific event types.

### 15.2.2 Registering Event Handlers p. 747
* There are 2 basic ways to register event handlers.
* First: set a property on the object or document element of the event target. (This goes back to the 1990s.)
* Second: pass the handler to the **addEventListener()** method of the object or element.

#### Method 1: Setting Event Handler Properties p. 747
* Simplest and oldest way.
* By convention, event handler properties have names that start with *on* followed by the event name, e.g., *onclick*, *onchange*, *onload*, *onmouseover*, etc.
* The following event handler example sets the *onload* property of the **Window** objet to a function.

```javascript
/* The function defined below is an event handler--
 * it is invoked when the document loads.
 */

window.onload = function() {

	// Look up a <form> element
	let form = document.querySelector("form#shipping");


	// Register an event handler function on the
	// form object that will be invoked before 
	// the form is submitted.
	// Assume the isFormValid() function is 
	// defined elsewhere.
	
	form.onsubmit = function(event) {

		// check whether form inputs are valid
		if (!isFormValid(this) ) {

			// and if form inputs are *not* valid,
			// then prevent form submission
			event.preventDefault();
		}
	};
};
```

* The shortcoming of event handler properties is that they are designed around the assumption that event targets will only have at most one hanlder for each type of event.
* It is often better to register event handlers using the *addEventListener()* because that technique (Method #2) does *not* overwrite any previously registered handlers.

##### Setting Event Handler Attributes p. 748
* The event handler properties of document elements can also be defined directly in the HTML file as attributes on the corresponding HTML tag.
* Handlers that would be registered on the *Window* element with JS can be defined with attributes on the `<body>` tag in HTML.
	* But this technique is generally frowned upon in modern web development. But it is possible and it's documented here b/c you may see it in legacy code.
* When defining an event handler as an HTML attribute, the attribute value should be a string of JS code.
* That code should be the *body* of the event handler function; *not* a complete function declaration.
	* i.e., your HTML event handler code should not be surrounded by curly braces `{}` and prefixed with the **function** keyword. e.g.

```html
	<button onclick="console.log('Thanks!!');"> Please Click Here. </button>
```
    
* If an event handler attribute contains multiple JS statements, you must remember to separate those statements with semicolons or break the attribute value across multiple lines.
* When you specify a string of JS code as the value of an HTML event handler attribute, the browser converts your string into a function that works something like this:

```javascript

function( event ) {
	with( document ) {
		with( this.form || {} ) {
			/* your code here */
		}
	}
}
```

* The **event** argument above means that your handler code can refer to the current event object as an *event*.
* Avoid the code above in general; see more on p. 750.

#### Method 2: Add Event Listeners p. 750
* The better, more modern way of adding event listeners.
* Any object can be an *event target* automatically defines a method named **addEventListener()**.
	* This includes objects like **Window** objects, **Document** objects, and all document **Element** objects.
* The `addEventListener()` method accepts **three arguments**:
	1. The **event type** for which the handler is being registered. The event type (aka *event name*) is a string that does **not** include the 'on-' prefix used when setting event handler properties (Method #1 above).
	1. The **function** that should be invoked when the specified type of event occurs.
	1. The final argument is optional and explained below. (p. 752). This argument is a boolean. If the boolean value is `true`, than the handler function is registered as a **capturing event handler** and is invoked at a different phase of eent dispatch. See more in 15.2.4.
		* See more on passing in an **Options** object as the third argumnet on page 752-753.
* Consider this code, which registers *two handlers* for the **click** event on the `<button>` element.

#### Code Part 1: HTML

```html
<button id = "mybutton"> Click me! </button>

<script> <!--opening script tag for JS below -->
```

#### Code Part 2: JavaScript

```javascript
let b = document.querySelector( "#mybutton" );

b.onclick = function() {
	console.log( "Thanks for clicking me!!" );
};

b.addEventListener( 
	"click" , () => {
		console.log( "Thanks again!" );
	}
);
```

#### Code Part 3: Closing HTML tag

```html
</script>
```

* Note the differences between the two techniques used. Calling **addEventListner()** with *click* as its first argument does *not* affect the value of the `onclick` property.
* In this code, a button click will log *two messages* to the developer console.
* If we called *addEventListener()* first and *then* set **onclick**, we would still log two messages--just in the opposite order.
* More importantly, you can call addEventListener() multiple times to register more than one handler function for the same event type of the same object.
* When an event occurs on an object, all the handlers registered for that type of event are invoked in the order in which they are registered.
* Invoking `addEventListener()` more than once on the same object with the same arguments has no effect.
* The handler function remains registered only *once*, and the repeated invocation does not alter the order in which handlers are invoked.

##### removeEventListener() p. 751
* `addEventListener()` is paired with a  `removeEventListener` method which expects the same two arguments (plus an optional third argument) but removes an event handler function from an object rather than adding it.
* It is often useful to temporarily register an event handler and then remove it soon afterward.
* For example, p. 751

***

## 7/20/2024
* Began checking out [MDN docs on Event Handlers](https://developer.mozilla.org/en-US/docs/Web/Events/Event_handlers).
* Another entry point is [MDN intro to events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events).
* Look at how many events are listed in the [MDN event reference!](https://developer.mozilla.org/en-US/docs/Web/Events) three columns, including what objects these events are fired on:
	1. **Animation** events fired on *Document*, *Window*, *HTMLElement*.
	1. **Async data fetching** events fired on *AbortSignal*, *XMLHttpRequest*, *FileReader*.
	1. **CSS Transition** events fired on *Document*, *Window*, *HTMLElement*.
	1. **Messaging events** (aka events related to a window receiving a msg from another browsing context) fired on Window.
	1. **Pointer events** (aka hardware-agnostic notification from devices including mouse, touch, pen/stylus) fired on *Document*, *HTMLElement*.
	1. **SVG events** fired on *SVGElement*, *SVGAnimationElement*, *SVGGraphicsElement*.
	1. And many more...
* Got pages "t09.html" / "t10.html" working with button to change color. Use live-server, etc.
* Back to Flanagan p. 754

### Sections skimmed p. 754 - 760
* 15.2.3 Event Handler Invocation 
* 15.2.4 Event Propagation
* 15.2.5 Event Cancellation
* 15.2.6 Dispatching Custom Events

***

## 7/22/2024
### 15.3 Scripting Documents p. 760
* Every Window object has a **document** property that refers to the `Document` object. Section 15.3 is all about the DOM, Document object.
* See this diagram generated on 7/21/2024 by ChatGPT:

```
Window
└── Document
    └── Node
        ├── Element
        │   ├── HTMLElement
        │   │   ├── HTMLDivElement
        │   │   ├── HTMLSpanElement
        │   │   ├── HTMLParagraphElement
        │   │   └── ... (other HTML element classes)
        │   └── SVGElement
        ├── Text
        └── ... (other node types)
```

1. The `Window` object is not part of the DOM class hierarchy that starts with `Node`. Instead, `Window` is the global object that represents the browser window and provides the environment in which scripts run. It has properties and methods for controlling the browser window, accessing the DOM, and handling events, among other things.
1. The relationship can be described like this:
	1. **Window**: The global object that represents the browser window. It provides properties and methods for controlling the window and interacting with the DOM. For example, `window.document` provides access to the `Document` object, which represents the entire HTML document.
	1. **Document**: The `Document` object is a property of the `Window` object. It represents the entire HTML document and serves as the entry point for accessing the rest of the DOM.
1. In summary, the `Window` object is the top-level object in the browser's JavaScript environment. The `Document` object is a property of the `Window` object, and the DOM class hierarchy begins with `Node` under the `Document` object.

### 15.3.1 Selecting Document Elements
* The **JS Document** object has a *head* property (that maps to the HTML `<head>` element).
* The **JS Document** object has a JS *body* property (that maps to the HTML `<body>` element).
* However, to select *more nested* JS Elements objects (mapping to the corresponding HTML tags that are also further nested), we must use the DOM JS methods **querySelector()** and **querySelectorAll()**.
* Each Element, e.g., a `button` JS object therefore has a DOM method like `button.querySelector()`. This is so named from the CSS syntax for **selectors**. p. 761.
* CSS selectors can describe elements by: (1) tag name; (2) the value of their `id` attribute; or (3) words in their `class` attribute. Examples:
	* `div` Any `<div>` element
	* `#nav` The element with `id="nav"`
	* `.warning` The element with "warning" in its class attribute
* The `#` character is used to match based on the `id` attribute and the `.` character is used to match based on the class attribute.
* JS Element objects can also be selected based on more general attribute values:
	* `p[lang="fr"]` A paragraph written in French, aka HTML tag `<p lang="fr">`.
	* `*[name="x"]` Any element with the `name="x"` attribute.
* Note in the above examples, we combine a tag name selector (or a `*` wildcard for many tag names) with an attribute selector.
* See also these more complex combinations:
	* `span.fatal.error` Any HTML tag <span> with *fatal* and *error* in its `class` attribute.
	* `span[lang="f"].warning` Any HTML tag <span> in French with the `warning` class.
* Selectors can also specify document structure
	* `#log span` Any <span> descendant of the element with HTML `id="log"`
	* `#log>span` Any <span> child of the element with HTML `id="log"`
	* `body>h1:first-child` The first `<h1>` child of the `<body>` 
	* `img + p.caption` A HTML `<p>` element with class `"caption"` immediately after an `<img>` tag
	* `h2 ~ p` Any `<p>` HTML tag that follows an `<h2>` HTML tag is a sibling of it.
* If two selectors are separated by a comma, it means we've selected elements that match either one of the selectors:
	* `button, input[type="button"]` All `<button>` and `<input type="button">` elements 
* As one can see, the CSS selectors allow us to reer to elements witin an HTML document by type, ID, class, attributes, and position within the document.

#### querySelector()
* The **querySelector()** method takes a CSS selector string as its input argument. 
* The **querySelector()** method outputs the first matching element in the document that it finds; *of* returns a **null** if nothing matches.
* e.g., to find the document element for the HTML tag with the attribute `id="spinner`:

```javascript
let spinner = document.querySelector("#spinner");
```

#### querySelectorAll()
* Similar to **querySelector()** method except it matches *all* matching elements in the document.
* The following selector finds all HTML Elements with `<h1>`, `<h2>`, `<h3>`.

```javascript
let titles = document.querySelectorAll("h1, h2, h3");
```

* Importantly, the return value of querySelectorAll() is *not* an array of ELement JS objects.
* Instead, the return is an array-like JS object called a **NodeList**.
* `NodeList` JS objects have a **length** property and can be indexed like regular arrays.
* `NodeList` JS objects are also iterable and can be manipulated by the modern `for/of` loop construct.
* To convert a `NodeList` JS object into a regular array, pass the NodeList into `Array.from()`.
* The **querySelectorAll()** and **querySelectorAll()** are implemented by both the **Element** and **Document** JS classes.
	* When invoked on an element, these methods will only return elements that are children of that element.

#### CSS Pseudoelements
* CSS defines pseudoelements like `::first-line` and `::first-letter`.
* In CSS, these match portions of *text nodes* rather than actual elements.
* However, **querySelectorAll()** and **querySelectorAll()** will *not* work when fed `::first-letter`.
* Furthermore, for security/privacy reasons, many browsers will refuse to return matches for `:link` and `:visited`.

#### Using closest() and matches() p. 764-765

#### Other Element Selection methods p. 765
* In addition to **querySelectorAll()** and **querySelectorAll()**, the DOM also defines a number of older element selection methods that are mostly obsolete. e.g:
	**getElementById()**
	**getElementsByName()**
	**getElementsByTagName()**
	**getElementsByClassName()**

#### Historical ShortCut Selectors p. 765 - 766
* For historical reasons, the **Document** class defines shortcut properties to access certain kinds of nodes. 
* For example the JS *Document* object has properties **images**, **forms**, and **links** that map to the HTML elements `<img>`, `<form>`, `<a>`, respectively.
* The above properties refer to HTMLCollection objects which are much like NodeList objects. But in addition to be being indexed by arrayIndex, they can be accessed by *element ID* and or *element name*.

### 15.3.2 Document Structure and Traversal p. 767

#### Element Objects p. 767 - 768

1. parentNode
1. children
1. childElementCount
1. firstElementChild, lastElementChild
1. nextElementSibling, previousElementSibling

### Two sample functions p. 768 - 769
* These functions demonstrate how one can recursively do depth-first traversal of a document
* **Function 1:** `traverse( e,f)` which recursively traverses the Document or an Element *e*, invoking the function *f* on *e* and each of e's descendants

```javascript
function traverse( e, f) {

	// Invoke f() on e
	f(e);  

	// Iterate over the children
	for( let child of e.children ) {

		// Recurse on each
		traverse( child, f );
	}
}
```

* **Function 2:** `traverse2( e,f )`

```javascript
function traverse2( e, f) {

	// Invoke f() on e
	f(e);

	// Iterate over the children linked-list style
	let child = e.firstElementChild;
		while( child !== null ) {

			// Recurse
			traverse2( child, f );
			child = child.nextElementSibling;

		}

}
```

### Alternate Method of Traversal: Documents as Trees of Nodes p. 769 - 771
* If one wishes to use **Text** nodes (and not ignore them), one can use a different set of properties that are alwys defined on all Node JS objects.
* All Node JS objects define these properties:
	1. parentNode
	1. childNodes
	1. firstChild, lastChild
	1. nextSibling, previousSibling
	1. nodeType
	1. nodeValue
	1. NodeName
* This method is pretty fragile, b/c if even a single blank line `\n` is added, it moves everything off by one. p. 771.

### 15.3.3 Attributes
* An *HTML element* is basically a **tag name** plus a series of **attributes** (aka name/value pairs called attributes).
* The clunkier method to create/read/update/delete these attributes is using methods defined by the JS *Element* class such as: `getAttribute()`, `setAttribute()`, `hasAttribute()`, and `removeAttribute()`.
* The preferred method is accessing these attributes as **properties of the corresponding *JS object***, aka properties of the **HTMLElement** JS object.
* i.e., it's usually easier to easier to find the URL like so (instead of calling something like `getURL()`):

```javascript
let jeffImg = document.querySelector("#main_image");
let jeffUrl = jeffImg.src; // aka src attribute is the URL of the image

jeffImg.id === "main_image"; // returns true b/c we looked up the image by id

```
#### Form-submission attribute access sample code p. 773

```javascript
let f = document.querySelector("form") // find first <form> in the document
f.action = "https://www.example.com/submit"; // Set the URL to submit it to
f.method = "POST";  // Set the HTTP request type
```

* **Important Note:** While HTML attributes are note case-sensitive, **JS property names *are* case-sensitive**.
	* To convert an attribute nmae to the equivalent JS property, write it in lowercase.
	* If the attribute is more than one word long, put it in Camel Case, e.g., `defaultChecked` and `tabIndex`.
	* *Exception:* Event Handler properties like `onclick` are written in all lowercase.
* Some HTML attribute names are reserved words in JS. The general rule for these words is to prefix the propery name with "html" when converting to JS.
	* e.g., The HTML `<label>` element has an HTML attribute called **for**.
	* of course, `for` is a reserved word in JS.
	* So we convert the HTML tag `<label for=" ">` into the JS property **htmlFor** of the JS object **label**.
* Note that the HTML `class` attributes is translated into the JS property **className**. (If we followed the usual rule above, it should turn into the JS property **htmlClass**.

#### Property-based API does not allow deletion p. 774
* Note that this property-based API for getting and setting attribute values does not define any way to remove an attribute from an element. 
* In particular, the **delete** operator cannot be used for this purpose. If you need to delete an attribute, use the **removeAttribute()** method.

#### The Class Attribute p. 774
* The class attribute of an HTML element is a particularly important one. 
* Its value is a space-separated list of CSS classes that apply to the element and affect how it is styled with CSS.
* Because `class` is a reserved word in JavaScript, the value of this attribute is available through the 
**className** property on JS *Element* objects.
* Unfortunately, the HTML `class` attribute of html `<elements>` are poorly named. 
	* The value for class is a *list* of CSS classes, not just a single class.
	* It is common in client-side JS programming to add and remove individual class names from this list rather than working with the list as a single string.
* For this reason, JS Element objects also define a **classList** property that allows one to treat the html `<class>` attribute as a list.
* The value of the *classList* JS object is an iterable Array-like object.
* Example for when we want to know the user that the program is busy, we display a spinner. To do do this, we have to remove the *hidden* class and add the *animated* class

```javascript
let jeffSpinner = document.querySelector*("#spinner");
jeffSpinner.classList.remove("hidden");
jeffSpinner.classList.add("animated");
```

#### Dataset Attributes p. 775
* Sometimes, we want to add additional info to an HTML element.
* In HTML, any attribute whose name is lowercase and begins with the prefix *data-* is considered valid and one can use them for any purpose.
* These **dataset attributes** will not affect the presentation of the elements on which they appear.
* These dataset attributes define a standard way of attaching additional data without compromising the HTML validity. See example below
* HTML

```html
<h2 id="title" data-section-number="16.1">Attributes</h2>
```

* JS to access section number in above HTML:

```javascript
let number = document.querySelector("#title").dataset.sectionNumber;
console.log(number);  // will output 16.1
```

15.3.4 Element Content
* Element content as HTML p. 777
	* innerHTML vs. outerHTML
	* p. 779 "**innerText** has some unusual and complex behaviors, such as attempting to preserve table formatting. It is not well specified nor implemented compatibly between browsers, however, and should no longer be used."
* Element content as Plain Text p. 778
	* Use the `textContent` property

### 15.3.5 Creating, Inserting, Deleting Nodes p. 779


### 15.3.6 Example p. 782 - 785
* Using JS and the DOM to generate a Table of Contents for your HTML page.


### Section 15.4 Scripting CSS p. 785





***

## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to paste `fired on Document, Window, HTMLElement.` from the register **d**, type `"dp`.
* to paste `**querySelectorAll()** and **querySelectorAll()**` from the register **q**, type `"dq`.
* to yank next 3 words and store in register **a**, type `"ay3w`.
* to yank from cursor to end of the current line and store in register **b**, type `"by$`.

`<script>`
**querySelectorAll()** and **querySelectorAll()**
