---
title: Client JavaScript
permalink: /web-js/
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

## 7/17/2024
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
* All of these separate bits of code share a single global **Window* object; they all have access to the same underlying **Document** object.
* Scripts that are not modules also share a top-level namespace.

#### iFrames p. 728-729
* If a webpage includes an embedded frame (i.e., using the `<iframe`> element), the JS code in the embedded document has a *different global object* than the enclosing window.
	* Thus, the iframe also has a distinct Document object and global object from the enclosing window.
* However, if the container document and the contained document are both loaded from the same server, the code in one document can interact with the code in the other document.
* See Section 15.13.6 (p. 957) for more info on how to send messages can be passed between JS in the containing window and the JS in the contained iframe.

#### Sequence p. 729
* One can think of JS program execution as occurring in two phases.
* **Phase 1:** the document content is loaded, and the code from the `<script>` elements is run.
	1. Scripts generally run in the order in they are placed in the doc (modulo **defer** and **async** attributes of the `<script>` tag).
	1. The JS code within any single script is run from top to bottom, subject to standard JS control-flow.
	1. Some non-obvious things might happen like the creation/loading of various classes and objects so they are available for Phase 2.
* **Phase 2:** After the document is loaded and all scripts have run, then the asynch and event-driven part of JS execution starts.
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
1. This marks the transition from Phase 1 to Phase 2.
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


***

## register info
* to paste *```javascript* from the register **j**, type `"jp`.
* to paste *`<script>`* from the register **k**, type `"kp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.

`<script>`
