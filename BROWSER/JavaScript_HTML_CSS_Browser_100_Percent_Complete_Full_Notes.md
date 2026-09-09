# JavaScript + HTML + CSS + Browser --- 100% Complete Full Notes

> **Purpose:** A professional, end-to-end reference covering JavaScript,
> HTML, CSS, and the browser as one integrated web platform.
>
> **Scope:** Beginner → Intermediate → Advanced → Professional → Senior
> Frontend Engineer → Web Platform Specialist.
>
> This is a **full concept note**, not a beginner-only syllabus. It
> explains what each major concept is, why it exists, how it interacts
> with the other layers, common APIs, important browser behavior,
> security, performance, accessibility, testing, and production
> architecture.

------------------------------------------------------------------------

# Table of Contents

1.  Web Platform Mental Model
2.  Internet, HTTP, DNS, TLS and Web Requests
3.  Browser Architecture
4.  HTML Fundamentals
5.  HTML Document Structure
6.  HTML Elements and Semantics
7.  HTML Text Content
8.  HTML Links and Navigation
9.  HTML Images
10. HTML Audio and Video
11. HTML Tables
12. HTML Forms
13. HTML Metadata and Head
14. HTML Accessibility
15. HTML SEO and Structured Data
16. HTML Embedded Content and Iframes
17. HTML Modern Interactive Elements
18. HTML Web Components
19. HTML Internationalization
20. CSS Fundamentals
21. CSS Syntax, Values and Units
22. Selectors
23. Cascade, Specificity and Inheritance
24. Box Model
25. Display and Formatting Contexts
26. Positioning and Stacking
27. Colors, Backgrounds and Borders
28. Typography
29. Flexbox
30. CSS Grid
31. Responsive Design
32. Container Queries
33. Media Queries and User Preferences
34. CSS Functions and Custom Properties
35. CSS Transforms
36. CSS Transitions and Animations
37. Advanced CSS Layout
38. Modern CSS Features
39. CSS Architecture
40. JavaScript Fundamentals
41. JavaScript Types and Values
42. Variables, Scope and Hoisting
43. Operators and Expressions
44. Control Flow
45. Functions
46. Closures
47. Objects
48. Prototypes and Inheritance
49. Classes and OOP
50. `this`, Call, Apply and Bind
51. Arrays
52. Strings
53. Map, Set and Weak Collections
54. Destructuring, Spread and Rest
55. Iterators and Generators
56. Symbols and Well-Known Symbols
57. Error Handling
58. Regular Expressions
59. Dates, Time and Intl
60. Modules
61. Promises
62. Async/Await
63. Event Loop and Concurrency
64. Memory Management and Garbage Collection
65. DOM
66. DOM Traversal and Selection
67. Creating and Updating HTML from JavaScript
68. Attributes, Properties and Classes
69. CSSOM and Styling from JavaScript
70. Events
71. Event Propagation and Delegation
72. Forms with JavaScript
73. Fetch and HTTP APIs
74. XMLHttpRequest and Legacy AJAX
75. WebSockets
76. Server-Sent Events
77. URL and URLSearchParams
78. Storage and Cookies
79. IndexedDB
80. Cache API and Offline Storage
81. File API
82. Drag and Drop
83. Clipboard
84. Notifications and Permissions
85. Geolocation
86. Media Devices and Recording
87. Canvas
88. SVG
89. WebGL and GPU APIs
90. Browser Observers
91. Window, Document and Navigator
92. Location and History
93. Timers, Animation Frames and Scheduling
94. Page Lifecycle and Navigation Lifecycle
95. Rendering Pipeline
96. Loading Pipeline and Critical Rendering Path
97. Web Performance
98. Core Web Vitals
99. Browser Security Model
100. Same-Origin Policy
101. CORS
102. CSP and Trusted Types
103. XSS and DOM Security
104. CSRF and Authentication
105. Cookies and Browser Security
106. Iframes and postMessage
107. Web Workers
108. Service Workers
109. Shared Workers and Shared Memory
110. Web Components Deep Dive
111. Shadow DOM
112. Custom Elements
113. Templates and Slots
114. PWA
115. Accessibility Engineering
116. Browser DevTools
117. Testing
118. Browser Automation
119. Type Safety and TypeScript Concepts
120. npm and Frontend Tooling
121. Bundlers and Build Pipelines
122. Source Maps
123. Linting and Formatting
124. Frontend Architecture
125. State Management
126. Component Architecture
127. API Integration Architecture
128. Authentication and Authorization
129. Real-Time Applications
130. Offline-First Applications
131. CSS + JavaScript Integration
132. HTML + JavaScript Integration
133. HTML + CSS Integration
134. Browser Compatibility
135. Progressive Enhancement
136. Security Headers
137. Performance Architecture
138. Error Monitoring and Observability
139. Production Deployment
140. Frontend Code Quality
141. Common Anti-Patterns
142. Practical Projects
143. Professional Checklists
144. Final Mastery Path

------------------------------------------------------------------------

# Part 1 --- Web Platform Mental Model

## 1.1 The Three Core Technologies

A browser application is primarily built from:

-   **HTML** --- structure and meaning.
-   **CSS** --- presentation, layout, visual behavior.
-   **JavaScript** --- behavior, computation, interaction,
    communication.

A useful model:

``` text
HTML
  ↓
DOM
  ↓
CSS + CSSOM
  ↓
Render Tree
  ↓
Layout
  ↓
Paint
  ↓
Composite
  ↓
Screen

JavaScript
  ↕
DOM / CSSOM / Browser APIs
  ↕
Network / Storage / Media / Workers
```

HTML describes **what exists**.

CSS describes **how it should look and lay out**.

JavaScript describes **what it should do**.

The browser supplies the runtime that connects all three.

------------------------------------------------------------------------

# Part 2 --- Internet, HTTP, DNS, TLS and Web Requests

## 2.1 Entering a URL

When a user enters:

``` text
https://example.com/products?id=10
```

the browser may perform:

1.  URL parsing
2.  DNS lookup
3.  TCP connection
4.  TLS handshake for HTTPS
5.  HTTP request
6.  Server processing
7.  HTTP response
8.  HTML parsing
9.  CSS/JS/image discovery
10. Additional requests
11. DOM/CSSOM construction
12. Rendering

## 2.2 URL Anatomy

``` text
https://example.com:443/products?id=10#reviews
│       │           │    │        │       │
scheme  host        port path     query   fragment
```

Important URL APIs:

``` js
const url = new URL("https://example.com/products?id=10");

console.log(url.hostname);
console.log(url.pathname);
console.log(url.searchParams.get("id"));
```

## 2.3 HTTP Concepts

Know:

-   request/response
-   methods
-   status codes
-   headers
-   body
-   content types
-   caching
-   cookies
-   authentication
-   redirects
-   compression
-   connection reuse

Methods:

-   GET
-   POST
-   PUT
-   PATCH
-   DELETE
-   HEAD
-   OPTIONS

Status families:

-   `1xx` informational
-   `2xx` success
-   `3xx` redirection
-   `4xx` client error
-   `5xx` server error

------------------------------------------------------------------------

# Part 3 --- Browser Architecture

A modern browser contains multiple cooperating subsystems.

Conceptually:

``` text
Browser
├── Browser/UI process
├── Renderer process
├── Network service
├── GPU process
├── Storage systems
└── Other isolated processes/services
```

Important concepts:

-   process isolation
-   site isolation
-   renderer
-   JavaScript engine
-   DOM engine
-   CSS engine
-   compositor
-   GPU acceleration
-   networking
-   browser security boundary

The exact architecture differs by browser and platform.

------------------------------------------------------------------------

# Part 4 --- HTML Fundamentals

## 4.1 Basic Document

``` html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>My Page</title>
</head>
<body>
  <h1>Hello</h1>
</body>
</html>
```

## 4.2 DOCTYPE

``` html
<!doctype html>
```

This requests standards mode in modern browsers.

## 4.3 Elements

General form:

``` html
<tag attribute="value">content</tag>
```

Void elements include examples such as:

``` html
<img>
<input>
<br>
<hr>
<meta>
<link>
```

------------------------------------------------------------------------

# Part 5 --- HTML Document Structure

Important elements:

-   `html`
-   `head`
-   `body`
-   `title`
-   `meta`
-   `link`
-   `style`
-   `script`
-   `base`
-   `noscript`

Global attributes include:

-   `id`
-   `class`
-   `style`
-   `title`
-   `lang`
-   `dir`
-   `hidden`
-   `tabindex`
-   `data-*`
-   `contenteditable`
-   `draggable`
-   `spellcheck`
-   `translate`
-   `role`
-   `aria-*`

------------------------------------------------------------------------

# Part 6 --- HTML Elements and Semantics

Semantic HTML communicates meaning.

Major structural elements:

``` html
<header>
<nav>
<main>
<section>
<article>
<aside>
<footer>
```

Content elements:

``` html
<h1> ... <h6>
<p>
<strong>
<em>
<mark>
<small>
<blockquote>
<q>
<code>
<pre>
<time>
```

Semantic HTML improves:

-   accessibility
-   SEO
-   maintainability
-   browser behavior
-   document structure

Prefer semantic elements over generic `<div>` elements when a semantic
element exists.

------------------------------------------------------------------------

# Part 7 --- HTML Text Content

Understand:

-   headings
-   paragraphs
-   lists
-   ordered lists
-   unordered lists
-   description lists
-   inline semantics
-   quotations
-   code
-   preformatted text
-   abbreviations
-   definitions
-   citations
-   time
-   edits

Examples:

``` html
<ol>
  <li>First</li>
  <li>Second</li>
</ol>

<dl>
  <dt>HTTP</dt>
  <dd>Hypertext Transfer Protocol</dd>
</dl>
```

------------------------------------------------------------------------

# Part 8 --- HTML Links and Navigation

Basic:

``` html
<a href="/products">Products</a>
```

Important concepts:

-   absolute URLs
-   relative URLs
-   fragments
-   `target`
-   `rel`
-   download links
-   mail links
-   telephone links
-   accessibility names
-   external link security

Example:

``` html
<a
  href="https://example.com"
  target="_blank"
  rel="noopener noreferrer">
  Open
</a>
```

------------------------------------------------------------------------

# Part 9 --- HTML Images

Basic:

``` html
<img
  src="photo.jpg"
  alt="Mountain landscape"
  width="800"
  height="500">
```

Important:

-   `alt`
-   intrinsic dimensions
-   responsive images
-   lazy loading
-   decoding
-   priority
-   `picture`
-   `source`
-   `srcset`
-   `sizes`

Example:

``` html
<img
  src="small.jpg"
  srcset="small.jpg 480w, large.jpg 1200w"
  sizes="(max-width: 600px) 100vw, 50vw"
  alt="Landscape">
```

`alt` is part of accessibility, not merely an SEO field.

------------------------------------------------------------------------

# Part 10 --- HTML Audio and Video

Audio:

``` html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
</audio>
```

Video:

``` html
<video controls width="800">
  <source src="movie.mp4" type="video/mp4">
</video>
```

Learn:

-   controls
-   autoplay restrictions
-   muted playback
-   preload
-   poster
-   tracks
-   captions
-   subtitles
-   media events
-   Media Source Extensions concepts
-   adaptive streaming concepts

------------------------------------------------------------------------

# Part 11 --- HTML Tables

Use tables for tabular data.

``` html
<table>
  <caption>Employees</caption>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Role</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Ana</td>
      <td>Developer</td>
    </tr>
  </tbody>
</table>
```

Know:

-   `caption`
-   `thead`
-   `tbody`
-   `tfoot`
-   `tr`
-   `th`
-   `td`
-   `scope`
-   row/column spanning
-   accessible table headers

------------------------------------------------------------------------

# Part 12 --- HTML Forms

Important elements:

-   `form`
-   `label`
-   `input`
-   `textarea`
-   `select`
-   `option`
-   `optgroup`
-   `button`
-   `fieldset`
-   `legend`
-   `datalist`
-   `output`

Input types:

-   text
-   password
-   email
-   number
-   tel
-   url
-   search
-   date
-   time
-   datetime-local
-   month
-   week
-   color
-   checkbox
-   radio
-   range
-   file
-   hidden
-   submit
-   reset
-   button

Validation:

``` html
<input
  type="email"
  required
  minlength="5">
```

JavaScript:

``` js
const form = document.querySelector("form");

form.addEventListener("submit", event => {
  if (!form.checkValidity()) {
    event.preventDefault();
  }
});
```

Important concepts:

-   constraint validation
-   `validity`
-   `checkValidity()`
-   `reportValidity()`
-   `setCustomValidity()`
-   FormData
-   multipart upload
-   autocomplete
-   input modes
-   disabled/read-only states

------------------------------------------------------------------------

# Part 13 --- HTML Metadata and Head

Common:

``` html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="...">
<link rel="icon" href="/favicon.ico">
<link rel="stylesheet" href="/app.css">
<script src="/app.js" defer></script>
```

Learn:

-   charset
-   viewport
-   description
-   robots
-   canonical URL
-   icons
-   manifest
-   preload
-   prefetch
-   preconnect
-   module scripts
-   resource hints

------------------------------------------------------------------------

# Part 14 --- HTML Accessibility

Accessibility starts with semantic HTML.

Core concepts:

-   accessible name
-   role
-   state
-   property
-   keyboard accessibility
-   focus
-   focus order
-   screen readers
-   accessibility tree
-   labels
-   descriptions
-   landmarks
-   headings
-   alternative text

Use ARIA only when native HTML cannot express the required semantics.

Bad:

``` html
<div onclick="save()">Save</div>
```

Better:

``` html
<button type="button">Save</button>
```

------------------------------------------------------------------------

# Part 15 --- HTML SEO and Structured Data

Learn:

-   title
-   meta description
-   heading hierarchy
-   semantic content
-   canonical links
-   robots directives
-   sitemap concepts
-   structured data
-   Open Graph
-   social metadata
-   crawlability
-   indexability

Structured data commonly uses JSON-LD:

``` html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Example"
}
</script>
```

------------------------------------------------------------------------

# Part 16 --- Embedded Content and Iframes

``` html
<iframe
  src="https://example.com"
  title="Example">
</iframe>
```

Learn:

-   iframe isolation
-   sandbox
-   permissions policy
-   `allow`
-   `referrerpolicy`
-   embedding restrictions
-   cross-origin communication
-   `postMessage`

Security:

``` html
<iframe
  src="..."
  sandbox>
</iframe>
```

------------------------------------------------------------------------

# Part 17 --- Modern Interactive HTML

Important modern elements/APIs:

``` html
<details>
<summary>More</summary>
Content
</details>
```

``` html
<dialog id="dialog">
  <p>Hello</p>
</dialog>
```

JavaScript:

``` js
dialog.showModal();
dialog.close();
```

Also learn:

-   popover
-   `popover` attribute
-   `showPopover()`
-   `hidePopover()`
-   disclosure patterns
-   dialog focus behavior

------------------------------------------------------------------------

# Part 18 --- HTML Web Components

Core pieces:

-   Custom Elements
-   Shadow DOM
-   HTML templates
-   slots
-   custom states
-   form-associated custom elements

Architecture:

``` text
Custom Element
    │
    ├── Shadow Root
    │     ├── Template
    │     └── Styles
    │
    └── Public API
```

------------------------------------------------------------------------

# Part 19 --- HTML Internationalization

Learn:

-   `lang`
-   `dir`
-   bidirectional text
-   RTL
-   Unicode
-   language-specific formatting
-   localization
-   translated attributes
-   `Intl`
-   date/number/currency formatting

------------------------------------------------------------------------

# Part 20 --- CSS Fundamentals

Basic:

``` css
button {
  color: white;
  background: black;
}
```

CSS consists conceptually of:

``` text
Selector
  +
Declaration block
  +
Properties
  +
Values
```

------------------------------------------------------------------------

# Part 21 --- CSS Syntax, Values and Units

Units:

-   `px`
-   `%`
-   `em`
-   `rem`
-   `vw`
-   `vh`
-   `dvw`
-   `dvh`
-   `svh`
-   `lvh`
-   `ch`
-   `ex`
-   `fr`

Functions:

``` css
width: calc(100% - 2rem);
width: min(100%, 1200px);
font-size: clamp(1rem, 2vw, 2rem);
```

------------------------------------------------------------------------

# Part 22 --- CSS Selectors

Basic:

``` css
p {}
.class {}
#id {}
```

Combinators:

``` css
A B {}
A > B {}
A + B {}
A ~ B {}
```

Attribute selectors:

``` css
input[type="email"] {}
```

Pseudo-classes:

``` css
:hover
:focus
:focus-visible
:checked
:disabled
:nth-child()
:not()
:is()
:where()
:has()
```

Pseudo-elements:

``` css
::before
::after
::placeholder
::selection
```

------------------------------------------------------------------------

# Part 23 --- Cascade, Specificity and Inheritance

The cascade considers:

-   origin
-   importance
-   layers
-   specificity
-   source order

Specificity is conceptually compared through selector components.

Example:

``` css
button {
  color: red;
}

.primary {
  color: blue;
}
```

The class selector generally has higher specificity than the element
selector.

Learn:

-   inheritance
-   initial
-   inherit
-   unset
-   revert
-   `!important`
-   cascade layers

Modern architecture:

``` css
@layer reset, base, components, utilities;
```

------------------------------------------------------------------------

# Part 24 --- CSS Box Model

Every normal CSS box can involve:

``` text
content
padding
border
margin
```

Default sizing:

``` css
box-sizing: content-box;
```

Common production reset:

``` css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

Learn:

-   width
-   height
-   min/max
-   padding
-   border
-   margin
-   margin collapsing
-   overflow

------------------------------------------------------------------------

# Part 25 --- Display and Formatting Contexts

Important values:

-   block
-   inline
-   inline-block
-   flex
-   grid
-   none
-   contents
-   table
-   flow-root

Learn:

-   normal flow
-   block formatting context
-   inline formatting context
-   flex formatting context
-   grid formatting context

------------------------------------------------------------------------

# Part 26 --- Positioning and Stacking

Position:

``` css
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

Learn:

-   containing blocks
-   offsets
-   stacking contexts
-   `z-index`
-   sticky constraints
-   fixed positioning
-   transformed elements

A large `z-index` does not automatically place an element above every
other element because stacking contexts can isolate descendants.

------------------------------------------------------------------------

# Part 27 --- Colors, Backgrounds and Borders

Learn:

-   named colors
-   hex
-   RGB
-   HSL
-   modern color functions
-   alpha
-   gradients
-   background image
-   multiple backgrounds
-   border radius
-   border images
-   shadows
-   opacity

------------------------------------------------------------------------

# Part 28 --- Typography

Learn:

-   font families
-   font stacks
-   web fonts
-   `@font-face`
-   font weight
-   font style
-   line height
-   letter spacing
-   word spacing
-   text wrapping
-   text overflow
-   variable fonts
-   font loading
-   fallback fonts

Example:

``` css
body {
  font-family: system-ui, sans-serif;
  line-height: 1.5;
}
```

------------------------------------------------------------------------

# Part 29 --- Flexbox

Flexbox is mainly one-dimensional layout.

``` css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}
```

Learn:

-   main axis
-   cross axis
-   flex direction
-   wrapping
-   `flex-grow`
-   `flex-shrink`
-   `flex-basis`
-   alignment
-   ordering
-   gaps
-   intrinsic sizing

------------------------------------------------------------------------

# Part 30 --- CSS Grid

Grid is two-dimensional.

``` css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}
```

Learn:

-   explicit grid
-   implicit grid
-   tracks
-   lines
-   areas
-   `fr`
-   `minmax`
-   auto placement
-   alignment
-   subgrid

------------------------------------------------------------------------

# Part 31 --- Responsive Design

Responsive design adapts the UI to available space.

Core techniques:

-   fluid widths
-   flexible grids
-   media queries
-   container queries
-   responsive typography
-   responsive images
-   mobile-friendly controls
-   viewport units

Avoid designing only for specific device names. Design for content and
available space.

------------------------------------------------------------------------

# Part 32 --- Container Queries

Container queries allow components to respond to their container.

Concept:

``` css
.card-wrapper {
  container-type: inline-size;
}

@container (min-width: 500px) {
  .card {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
}
```

This enables component-level responsive behavior.

------------------------------------------------------------------------

# Part 33 --- Media Queries and User Preferences

Examples:

``` css
@media (prefers-color-scheme: dark) {}

@media (prefers-reduced-motion: reduce) {}

@media (hover: hover) {}

@media (pointer: coarse) {}
```

Learn:

-   viewport media features
-   print
-   dark mode
-   reduced motion
-   contrast preferences
-   input capabilities

------------------------------------------------------------------------

# Part 34 --- CSS Functions and Custom Properties

Custom property:

``` css
:root {
  --primary: #3366ff;
  --spacing: 1rem;
}

button {
  background: var(--primary);
  padding: var(--spacing);
}
```

Learn:

-   `var()`
-   `calc()`
-   `min()`
-   `max()`
-   `clamp()`
-   `minmax()`
-   environment variables
-   custom property inheritance

------------------------------------------------------------------------

# Part 35 --- CSS Transforms

``` css
.card {
  transform: translateY(-4px) scale(1.02);
}
```

Learn:

-   translate
-   scale
-   rotate
-   skew
-   transform origin
-   2D transforms
-   3D transforms
-   perspective
-   transform matrices

------------------------------------------------------------------------

# Part 36 --- CSS Transitions and Animations

Transition:

``` css
button {
  transition: transform 200ms ease;
}
```

Animation:

``` css
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
```

Learn:

-   keyframes
-   timing functions
-   delays
-   iteration
-   direction
-   fill mode
-   animation events
-   reduced motion
-   compositor-friendly animation

------------------------------------------------------------------------

# Part 37 --- Advanced CSS Layout

Learn:

-   intrinsic sizing
-   min-content
-   max-content
-   fit-content
-   aspect ratio
-   overflow
-   fragmentation
-   multicolumn layout
-   logical properties
-   writing modes
-   floats
-   shape outside
-   object fitting
-   replaced elements

Logical properties:

``` css
margin-inline: auto;
padding-block: 1rem;
```

------------------------------------------------------------------------

# Part 38 --- Modern CSS Features

Important areas:

-   cascade layers
-   `:has()`
-   `:is()`
-   `:where()`
-   container queries
-   subgrid
-   native nesting
-   modern color spaces
-   logical properties
-   scroll snapping
-   `content-visibility`
-   `contain`
-   `aspect-ratio`
-   popover styling
-   view-transition-related styling
-   scroll-driven animation concepts

Always check browser compatibility before relying on newer features in
broad-production environments.

------------------------------------------------------------------------

# Part 39 --- CSS Architecture

Common approaches:

-   BEM
-   utility CSS
-   component CSS
-   CSS Modules
-   design tokens
-   layered CSS
-   CSS-in-JS concepts
-   framework-specific styling

Good CSS architecture should control:

-   naming
-   specificity
-   reuse
-   theming
-   responsive behavior
-   component isolation
-   maintainability

------------------------------------------------------------------------

# Part 40 --- JavaScript Fundamentals

JavaScript is an ECMAScript language implemented by engines such as:

-   V8
-   SpiderMonkey
-   JavaScriptCore

Browser JavaScript additionally interacts with Web APIs.

Important distinction:

``` text
ECMAScript language
        +
JavaScript engine
        +
Browser Web APIs
        =
Browser JavaScript environment
```

`fetch`, `document`, `localStorage`, and `navigator` are browser APIs,
not ECMAScript language primitives.

------------------------------------------------------------------------

# Part 41 --- JavaScript Types and Values

Primitive types:

-   undefined
-   null
-   boolean
-   number
-   bigint
-   string
-   symbol

Objects are non-primitive values.

Important:

``` js
typeof null; // "object"
```

This is a historical language behavior.

Understand:

-   primitive values
-   object references
-   equality
-   coercion
-   truthiness
-   falsiness
-   `NaN`
-   `Infinity`
-   `-0`
-   BigInt

------------------------------------------------------------------------

# Part 42 --- Variables, Scope and Hoisting

``` js
let count = 0;
const name = "Deep";
```

Understand:

-   `var`
-   `let`
-   `const`
-   global scope
-   module scope
-   function scope
-   block scope
-   lexical environment
-   temporal dead zone
-   hoisting

Prefer `const` by default and `let` when reassignment is required.

------------------------------------------------------------------------

# Part 43 --- Operators and Expressions

Operators include:

-   arithmetic
-   comparison
-   logical
-   assignment
-   nullish coalescing
-   optional chaining
-   bitwise
-   unary
-   ternary
-   `typeof`
-   `instanceof`
-   `in`
-   `delete`
-   `new`

Examples:

``` js
const city = user?.address?.city ?? "Unknown";
```

------------------------------------------------------------------------

# Part 44 --- Control Flow

Learn:

-   `if`
-   `else`
-   `switch`
-   `for`
-   `while`
-   `do...while`
-   `for...of`
-   `for...in`
-   `break`
-   `continue`
-   labeled statements
-   conditional expressions

Modern pattern:

``` js
for (const item of items) {
  console.log(item);
}
```

------------------------------------------------------------------------

# Part 45 --- Functions

Forms:

``` js
function add(a, b) {
  return a + b;
}

const add = (a, b) => a + b;
```

Learn:

-   declarations
-   expressions
-   arrow functions
-   parameters
-   defaults
-   rest parameters
-   return values
-   higher-order functions
-   callbacks
-   recursion
-   pure functions
-   function objects

------------------------------------------------------------------------

# Part 46 --- Closures

A closure occurs when a function retains access to its lexical
environment after the surrounding function has returned.

``` js
function counter() {
  let value = 0;

  return () => ++value;
}

const next = counter();

next(); // 1
next(); // 2
```

Closures power:

-   private state
-   factories
-   callbacks
-   module patterns
-   event handlers

------------------------------------------------------------------------

# Part 47 --- Objects

``` js
const user = {
  name: "Ana",
  age: 30,
  greet() {
    return `Hello ${this.name}`;
  }
};
```

Learn:

-   properties
-   methods
-   computed properties
-   property descriptors
-   getters
-   setters
-   object creation
-   object copying
-   object equality
-   enumeration
-   reflection

Important APIs:

``` js
Object.keys()
Object.values()
Object.entries()
Object.assign()
Object.create()
Object.defineProperty()
Object.getOwnPropertyDescriptor()
Object.freeze()
Object.seal()
```

------------------------------------------------------------------------

# Part 48 --- Prototypes and Inheritance

JavaScript uses prototype-based inheritance.

Concept:

``` text
object
  ↓
prototype
  ↓
prototype's prototype
  ↓
null
```

Understand:

-   prototype chain
-   `Object.getPrototypeOf`
-   `Object.setPrototypeOf`
-   `Object.create`
-   property lookup
-   shadowing
-   inherited properties

------------------------------------------------------------------------

# Part 49 --- Classes and OOP

``` js
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hello ${this.name}`;
  }
}
```

Learn:

-   constructors
-   instance methods
-   static methods
-   private fields
-   getters/setters
-   inheritance
-   `super`
-   polymorphism
-   composition vs inheritance

Classes are syntax built on JavaScript's prototype model.

------------------------------------------------------------------------

# Part 50 --- `this`, Call, Apply and Bind

`this` depends on how a function is called.

``` js
const obj = {
  value: 10,
  get() {
    return this.value;
  }
};
```

Learn:

-   method calls
-   plain calls
-   constructor calls
-   explicit binding
-   arrow functions
-   `call`
-   `apply`
-   `bind`

------------------------------------------------------------------------

# Part 51 --- Arrays

Learn:

-   indexing
-   mutation
-   copying
-   iteration
-   searching
-   sorting
-   flattening

Core methods:

``` js
map
filter
reduce
find
findIndex
some
every
includes
flat
flatMap
slice
splice
concat
sort
toSorted
toReversed
toSpliced
```

Know which methods mutate and which return new arrays.

------------------------------------------------------------------------

# Part 52 --- Strings

Learn:

-   Unicode
-   UTF-16
-   code units
-   code points
-   normalization
-   template literals
-   searching
-   slicing
-   replacement
-   splitting
-   padding
-   case conversion

Example:

``` js
const message = `Hello ${name}`;
```

Do not assume JavaScript string length equals the number of
user-perceived characters.

------------------------------------------------------------------------

# Part 53 --- Map, Set and Weak Collections

`Map`:

``` js
const map = new Map();
map.set("id", 10);
```

`Set`:

``` js
const ids = new Set([1, 2, 2, 3]);
```

Learn:

-   Map
-   Set
-   WeakMap
-   WeakSet
-   identity
-   iteration
-   memory implications

------------------------------------------------------------------------

# Part 54 --- Destructuring, Spread and Rest

``` js
const { name, age } = user;

const [first, second] = items;

const copy = { ...user };
```

Important:

-   shallow copying
-   rest properties
-   rest parameters
-   iterable requirements
-   nested destructuring
-   default values

------------------------------------------------------------------------

# Part 55 --- Iterators and Generators

Iterator protocol:

``` js
{
  next() {
    return {
      value: 1,
      done: false
    };
  }
}
```

Generator:

``` js
function* numbers() {
  yield 1;
  yield 2;
}
```

Learn:

-   iterable protocol
-   iterator protocol
-   generators
-   async iterators
-   `for...of`
-   `for await...of`

------------------------------------------------------------------------

# Part 56 --- Symbols and Well-Known Symbols

Symbols create unique primitive identifiers.

``` js
const id = Symbol("id");
```

Important well-known symbols include concepts for:

-   iteration
-   async iteration
-   primitive conversion
-   instance checks
-   matching
-   species behavior

------------------------------------------------------------------------

# Part 57 --- Error Handling

``` js
try {
  riskyOperation();
} catch (error) {
  console.error(error);
} finally {
  cleanup();
}
```

Learn:

-   `throw`
-   Error
-   TypeError
-   RangeError
-   SyntaxError
-   custom errors
-   error causes
-   stack traces
-   async errors
-   global error handling

------------------------------------------------------------------------

# Part 58 --- Regular Expressions

Learn:

-   literals
-   character classes
-   groups
-   captures
-   quantifiers
-   anchors
-   alternation
-   lookahead
-   lookbehind
-   flags
-   Unicode mode
-   named groups

Example:

``` js
const match = /^(?<id>\d+)$/.exec("123");
```

Use regex carefully; avoid complex patterns that cause catastrophic
backtracking.

------------------------------------------------------------------------

# Part 59 --- Dates, Time and Intl

Learn:

-   Date
-   timestamps
-   UTC
-   time zones
-   ISO strings
-   parsing pitfalls
-   formatting
-   `Intl.DateTimeFormat`
-   `Intl.NumberFormat`
-   `Intl.Collator`
-   `Intl.RelativeTimeFormat`
-   localization

Also understand the modern **Temporal** direction and its date/time
model where supported or provided through appropriate tooling.

------------------------------------------------------------------------

# Part 60 --- Modules

ES modules:

``` js
export function add(a, b) {
  return a + b;
}
```

``` js
import { add } from "./math.js";
```

Learn:

-   named exports
-   default exports
-   import aliases
-   dynamic import
-   module scope
-   cyclic dependencies
-   module loading
-   module resolution
-   browser module scripts
-   import maps
-   bundler resolution

------------------------------------------------------------------------

# Part 61 --- Promises

A Promise represents eventual completion or failure of an asynchronous
operation.

``` js
fetch("/api/users")
  .then(response => response.json())
  .then(users => console.log(users))
  .catch(error => console.error(error));
```

States:

-   pending
-   fulfilled
-   rejected

Combinators:

``` js
Promise.all()
Promise.allSettled()
Promise.race()
Promise.any()
```

------------------------------------------------------------------------

# Part 62 --- Async/Await

``` js
async function loadUser() {
  const response = await fetch("/api/user");
  return response.json();
}
```

Learn:

-   async functions
-   await
-   sequential vs parallel operations
-   error handling
-   cancellation
-   async iteration

Parallel:

``` js
const [users, products] = await Promise.all([
  loadUsers(),
  loadProducts()
]);
```

------------------------------------------------------------------------

# Part 63 --- Event Loop and Concurrency

Browser JavaScript is generally single-threaded per main execution
context, but browsers provide concurrent facilities.

Concept:

``` text
Call Stack
    ↓
Web APIs / browser services
    ↓
Task queues
    ↓
Event Loop
    ↓
Call Stack

Microtasks
    ↓
processed at defined checkpoints
```

Learn:

-   tasks
-   microtasks
-   promise reactions
-   timers
-   rendering opportunities
-   event loop
-   long tasks
-   concurrency vs parallelism

------------------------------------------------------------------------

# Part 64 --- Memory Management

Learn:

-   reachability
-   garbage collection
-   retained references
-   closures
-   detached DOM
-   memory leaks
-   weak references
-   `WeakMap`
-   `WeakSet`
-   `WeakRef`
-   `FinalizationRegistry`

Common leak sources:

-   forgotten event listeners
-   timers
-   global collections
-   detached DOM
-   subscriptions
-   caches with unlimited growth

------------------------------------------------------------------------

# Part 65 --- DOM

The DOM represents an HTML/XML document as an object tree.

``` text
Document
 └── html
      ├── head
      └── body
           ├── header
           └── main
```

JavaScript can:

-   read nodes
-   create nodes
-   modify nodes
-   remove nodes
-   listen for events

------------------------------------------------------------------------

# Part 66 --- DOM Traversal and Selection

Common:

``` js
document.getElementById("app");

document.querySelector(".card");

document.querySelectorAll("button");
```

Traversal:

``` js
element.parentElement
element.children
element.firstElementChild
element.nextElementSibling
```

Learn:

-   Node vs Element
-   NodeList
-   HTMLCollection
-   live vs static collections
-   traversal
-   containment

------------------------------------------------------------------------

# Part 67 --- Creating and Updating HTML

``` js
const button = document.createElement("button");
button.textContent = "Save";

document.body.append(button);
```

Learn:

-   `createElement`
-   `append`
-   `prepend`
-   `before`
-   `after`
-   `remove`
-   `replaceWith`
-   `cloneNode`
-   `insertAdjacentHTML`
-   `innerHTML`
-   `outerHTML`
-   `textContent`

Security principle:

Prefer `textContent` when inserting untrusted text.

------------------------------------------------------------------------

# Part 68 --- Attributes, Properties and Classes

Attribute:

``` js
element.setAttribute("disabled", "");
```

Property:

``` js
input.disabled = true;
```

Class:

``` js
element.classList.add("active");
```

Learn the difference between:

-   HTML attributes
-   DOM properties
-   reflected attributes
-   boolean attributes
-   dataset

------------------------------------------------------------------------

# Part 69 --- CSSOM and Styling from JavaScript

Inline style:

``` js
element.style.color = "red";
```

Computed style:

``` js
getComputedStyle(element);
```

CSS custom property:

``` js
element.style.setProperty("--size", "20px");
```

Learn:

-   CSSStyleDeclaration
-   computed style
-   CSSOM
-   stylesheets
-   CSS rules
-   media queries
-   custom properties

------------------------------------------------------------------------

# Part 70 --- Events

Common event categories:

-   mouse
-   pointer
-   keyboard
-   input
-   form
-   focus
-   clipboard
-   drag/drop
-   touch
-   wheel
-   media
-   animation
-   transition
-   composition

Example:

``` js
button.addEventListener("click", handler);
```

------------------------------------------------------------------------

# Part 71 --- Event Propagation and Delegation

Event flow:

``` text
Capture
   ↓
Target
   ↓
Bubble
```

Example:

``` js
container.addEventListener("click", event => {
  if (event.target.matches(".delete")) {
    // handle
  }
});
```

This is event delegation.

Learn:

-   `target`
-   `currentTarget`
-   capture
-   bubble
-   `stopPropagation`
-   `stopImmediatePropagation`
-   `preventDefault`
-   passive listeners
-   once
-   abortable listeners

------------------------------------------------------------------------

# Part 72 --- Forms with JavaScript

Learn:

-   `submit`
-   `input`
-   `change`
-   focus events
-   validation
-   FormData
-   file upload
-   serialization
-   async submission
-   error display
-   accessibility
-   optimistic UI
-   server-side validation

Example:

``` js
form.addEventListener("submit", async event => {
  event.preventDefault();

  const data = new FormData(form);

  await fetch("/api/save", {
    method: "POST",
    body: data
  });
});
```

------------------------------------------------------------------------

# Part 73 --- Fetch and HTTP APIs

Basic:

``` js
const response = await fetch("/api/users");

if (!response.ok) {
  throw new Error(`HTTP ${response.status}`);
}

const data = await response.json();
```

Learn:

-   Request
-   Response
-   Headers
-   body streams
-   JSON
-   text
-   blobs
-   ArrayBuffer
-   credentials
-   CORS
-   caching
-   redirects
-   abort signals
-   upload/download
-   streaming

------------------------------------------------------------------------

# Part 74 --- XMLHttpRequest and Legacy AJAX

Understand XHR because legacy systems still use it.

Learn:

-   request lifecycle
-   ready states
-   status
-   response types
-   progress
-   abort
-   upload events
-   synchronous XHR limitations

Modern applications generally prefer Fetch.

------------------------------------------------------------------------

# Part 75 --- WebSockets

WebSockets provide bidirectional communication.

``` js
const socket = new WebSocket("wss://example.com/socket");

socket.onmessage = event => {
  console.log(event.data);
};
```

Learn:

-   connection lifecycle
-   messages
-   close
-   errors
-   ping/pong concepts
-   reconnect strategies
-   authentication
-   scaling
-   backpressure considerations

------------------------------------------------------------------------

# Part 76 --- Server-Sent Events

SSE provides server-to-client event streaming.

``` js
const source = new EventSource("/events");

source.onmessage = event => {
  console.log(event.data);
};
```

Use cases:

-   notifications
-   dashboards
-   progress updates
-   live feeds

------------------------------------------------------------------------

# Part 77 --- URL and URLSearchParams

``` js
const params = new URLSearchParams({
  page: "1",
  sort: "name"
});

console.log(params.toString());
```

Learn:

-   URL
-   URLSearchParams
-   encoding
-   query manipulation
-   origin
-   path
-   fragment
-   URL resolution

------------------------------------------------------------------------

# Part 78 --- Storage and Cookies

## localStorage

Persistent per-origin string storage.

``` js
localStorage.setItem("theme", "dark");
```

## sessionStorage

Storage scoped to a page session context.

## Cookies

Cookies can be sent with HTTP requests according to cookie rules.

Learn:

-   expiration
-   domain
-   path
-   Secure
-   HttpOnly
-   SameSite
-   partitioning concepts
-   size limitations
-   privacy considerations

Do not store sensitive authentication material in JavaScript-accessible
storage without understanding the XSS risk.

------------------------------------------------------------------------

# Part 79 --- IndexedDB

IndexedDB is an asynchronous browser database.

Learn:

-   database
-   object stores
-   keys
-   indexes
-   transactions
-   version upgrades
-   requests
-   cursors
-   structured clone
-   quotas
-   migrations

Useful for:

-   offline applications
-   large local datasets
-   caching structured data

------------------------------------------------------------------------

# Part 80 --- Cache API and Offline Storage

Service workers can use Cache Storage:

``` js
await caches.open("v1");
```

Learn:

-   Cache
-   CacheStorage
-   request/response caching
-   cache-first
-   network-first
-   stale-while-revalidate
-   cache invalidation
-   versioning

------------------------------------------------------------------------

# Part 81 --- File API

Learn:

-   File
-   Blob
-   FileReader
-   object URLs
-   file inputs
-   drag/drop files
-   uploads
-   streaming
-   file metadata

Example:

``` js
const file = input.files[0];
console.log(file.name, file.size, file.type);
```

------------------------------------------------------------------------

# Part 82 --- Drag and Drop

Learn:

-   drag events
-   drop events
-   `DataTransfer`
-   `DataTransferItem`
-   file drops
-   accessible alternatives
-   preventing unwanted browser behavior

------------------------------------------------------------------------

# Part 83 --- Clipboard

Learn:

-   Clipboard API
-   read text
-   write text
-   clipboard permissions
-   paste events
-   copy events
-   security restrictions

Example:

``` js
await navigator.clipboard.writeText("Copied");
```

------------------------------------------------------------------------

# Part 84 --- Notifications and Permissions

Learn:

-   Notifications API
-   permission states
-   user gestures
-   permission prompts
-   service worker notifications
-   notification actions
-   privacy considerations

Never assume a permission request will succeed.

------------------------------------------------------------------------

# Part 85 --- Geolocation

``` js
navigator.geolocation.getCurrentPosition(
  position => {
    console.log(position.coords.latitude);
  }
);
```

Learn:

-   permission
-   accuracy
-   timeout
-   watch position
-   privacy
-   secure contexts

------------------------------------------------------------------------

# Part 86 --- Media Devices and Recording

Learn:

``` js
navigator.mediaDevices.getUserMedia()
```

APIs/concepts:

-   camera
-   microphone
-   permissions
-   MediaStream
-   MediaRecorder
-   device enumeration
-   constraints
-   tracks
-   audio/video processing

------------------------------------------------------------------------

# Part 87 --- Canvas

Canvas provides script-driven raster drawing.

``` html
<canvas id="canvas" width="500" height="300"></canvas>
```

``` js
const ctx = canvas.getContext("2d");

ctx.fillRect(10, 10, 100, 50);
```

Learn:

-   paths
-   shapes
-   text
-   images
-   transforms
-   compositing
-   pixels
-   animation
-   high-DPI rendering
-   OffscreenCanvas concepts

------------------------------------------------------------------------

# Part 88 --- SVG

SVG is vector graphics integrated into the document.

Learn:

-   paths
-   shapes
-   text
-   viewBox
-   transforms
-   styling
-   SVG DOM
-   accessibility
-   animation
-   inline vs external SVG

------------------------------------------------------------------------

# Part 89 --- WebGL and GPU APIs

Learn concepts:

-   GPU pipeline
-   shaders
-   buffers
-   textures
-   WebGL contexts
-   coordinate systems
-   rendering loops

Also understand the direction of newer GPU APIs such as WebGPU.

These are advanced graphics topics rather than normal DOM UI APIs.

------------------------------------------------------------------------

# Part 90 --- Browser Observers

Important:

### MutationObserver

Observes DOM changes.

### IntersectionObserver

Observes visibility/intersection.

### ResizeObserver

Observes element size changes.

### PerformanceObserver

Observes performance entries.

These enable event-driven behavior without inefficient polling.

------------------------------------------------------------------------

# Part 91 --- Window, Document and Navigator

Important browser globals:

``` js
window
document
navigator
location
history
screen
```

Learn:

-   viewport dimensions
-   device information
-   online status
-   language
-   platform information
-   permissions
-   clipboard
-   media
-   storage
-   scheduling

------------------------------------------------------------------------

# Part 92 --- Location and History

Navigation:

``` js
location.href = "/dashboard";
```

History:

``` js
history.pushState(
  { page: 2 },
  "",
  "/products?page=2"
);
```

Learn:

-   pushState
-   replaceState
-   popstate
-   back/forward
-   URL state
-   navigation lifecycle
-   SPA routing concepts

------------------------------------------------------------------------

# Part 93 --- Timers, Animation Frames and Scheduling

Timers:

``` js
setTimeout(fn, 1000);
setInterval(fn, 1000);
```

Animation:

``` js
requestAnimationFrame(render);
```

Learn:

-   timers
-   cancellation
-   event loop ordering
-   animation frames
-   idle scheduling
-   scheduler concepts
-   avoiding main-thread blocking

------------------------------------------------------------------------

# Part 94 --- Page Lifecycle

Understand:

-   initial parsing
-   DOMContentLoaded
-   load
-   visibility changes
-   freeze/resume concepts
-   pagehide
-   pageshow
-   unload limitations
-   bfcache
-   navigation
-   back/forward cache

Avoid relying on `unload` for critical persistence logic.

------------------------------------------------------------------------

# Part 95 --- Rendering Pipeline

Conceptual pipeline:

``` text
HTML
 ↓
DOM

CSS
 ↓
CSSOM

DOM + CSSOM
 ↓
Render Tree
 ↓
Style
 ↓
Layout
 ↓
Paint
 ↓
Composite
 ↓
Display
```

JavaScript can trigger style/layout work.

Learn:

-   style recalculation
-   layout
-   paint
-   compositing
-   rasterization
-   GPU
-   rendering opportunities

------------------------------------------------------------------------

# Part 96 --- Loading Pipeline

Understand:

``` text
HTML download
    ↓
HTML parse
    ↓
resource discovery
    ↓
CSS / JS / images
    ↓
DOM + CSSOM
    ↓
render
```

Important:

-   parser blocking scripts
-   `defer`
-   `async`
-   module scripts
-   preload
-   preconnect
-   lazy loading
-   code splitting

------------------------------------------------------------------------

# Part 97 --- Web Performance

Major categories:

-   network performance
-   JavaScript execution
-   rendering
-   memory
-   images
-   fonts
-   CSS
-   DOM size
-   third-party scripts

Optimization techniques:

-   reduce JS
-   split bundles
-   lazy load
-   optimize images
-   cache static assets
-   avoid long tasks
-   minimize layout thrashing
-   virtualize large lists
-   use efficient selectors
-   defer noncritical work

------------------------------------------------------------------------

# Part 98 --- Core Web Vitals

Know the concepts and measurement of:

-   LCP
-   INP
-   CLS

Also understand supporting metrics such as:

-   TTFB
-   FCP
-   long tasks
-   resource timing

Performance is measured from real user behavior as well as lab testing.

------------------------------------------------------------------------

# Part 99 --- Browser Security Model

Security is based on multiple layers:

-   origin isolation
-   sandboxing
-   permissions
-   CSP
-   CORS
-   cookie controls
-   secure contexts
-   iframe restrictions
-   process isolation

Never assume client-side validation is sufficient for security.

------------------------------------------------------------------------

# Part 100 --- Same-Origin Policy

An origin is conceptually:

``` text
scheme + host + port
```

Example:

``` text
https://example.com
```

Cross-origin access is restricted by browser security rules.

Learn:

-   same-origin policy
-   origin comparison
-   opaque origins
-   sandboxed documents
-   cross-origin resource loading

------------------------------------------------------------------------

# Part 101 --- CORS

CORS controls whether browser JavaScript may access cross-origin
responses.

Learn:

-   simple requests
-   preflight
-   OPTIONS
-   `Access-Control-Allow-Origin`
-   methods
-   headers
-   credentials
-   origin reflection risks

CORS is a browser enforcement mechanism; it is not an authentication
system.

------------------------------------------------------------------------

# Part 102 --- CSP and Trusted Types

Content Security Policy can restrict executable content and resource
sources.

Learn:

-   script-src
-   style-src
-   connect-src
-   img-src
-   frame-src
-   object-src
-   nonce
-   hash
-   report-only

Trusted Types can help reduce DOM XSS sinks when deployed appropriately.

------------------------------------------------------------------------

# Part 103 --- XSS and DOM Security

XSS types:

-   reflected
-   stored
-   DOM-based

Dangerous sinks include inappropriate use of:

``` js
innerHTML
outerHTML
insertAdjacentHTML
eval
new Function
```

Prefer safe DOM APIs for untrusted data.

Example:

``` js
element.textContent = userInput;
```

------------------------------------------------------------------------

# Part 104 --- CSRF and Authentication

Learn:

-   session authentication
-   cookies
-   bearer tokens
-   CSRF
-   SameSite
-   anti-CSRF tokens
-   origin checks
-   authorization
-   refresh sessions
-   logout
-   token rotation

Authentication answers:

> Who are you?

Authorization answers:

> What are you allowed to do?

The frontend must not be the final authority for permissions.

------------------------------------------------------------------------

# Part 105 --- Cookies and Browser Security

Important attributes:

``` text
Secure
HttpOnly
SameSite
Domain
Path
Max-Age
Expires
```

Understand:

-   host-only cookies
-   domain cookies
-   session cookies
-   persistent cookies
-   cross-site behavior
-   third-party cookie restrictions
-   cookie partitioning/privacy mechanisms

------------------------------------------------------------------------

# Part 106 --- Iframes and postMessage

Cross-window messaging:

``` js
window.postMessage(message, targetOrigin);
```

Receiver:

``` js
window.addEventListener("message", event => {
  if (event.origin !== "https://trusted.example") return;

  // process message
});
```

Never trust message data merely because it came from a browser event.
Validate the sender origin and message structure.

------------------------------------------------------------------------

# Part 107 --- Web Workers

Workers run JavaScript away from the main UI thread.

``` js
const worker = new Worker("/worker.js");

worker.postMessage({ value: 10 });
```

Learn:

-   Worker
-   Dedicated Worker
-   messaging
-   structured clone
-   transferable objects
-   worker lifecycle
-   CPU-heavy workloads

Workers do not directly manipulate the normal page DOM.

------------------------------------------------------------------------

# Part 108 --- Service Workers

Service workers are event-driven workers that can intercept network
requests and support offline capabilities.

Concept:

``` text
Page
 ↓
Service Worker
 ↓
Network / Cache
```

Learn:

-   registration
-   installation
-   activation
-   fetch events
-   caching
-   updates
-   skip waiting concepts
-   clients
-   notifications
-   background features
-   offline strategies

------------------------------------------------------------------------

# Part 109 --- Shared Workers and Shared Memory

Advanced concepts:

-   SharedWorker
-   SharedArrayBuffer
-   Atomics
-   memory synchronization
-   cross-context communication

These require careful security and concurrency design.

------------------------------------------------------------------------

# Part 110 --- Web Components Deep Dive

A Web Component can combine:

``` text
HTML
CSS
JavaScript
```

into a reusable custom element.

Example concept:

``` js
class UserCard extends HTMLElement {
  connectedCallback() {
    this.textContent = "User";
  }
}

customElements.define("user-card", UserCard);
```

------------------------------------------------------------------------

# Part 111 --- Shadow DOM

Shadow DOM creates a DOM subtree with encapsulation.

Learn:

-   open vs closed shadow roots
-   style encapsulation
-   event retargeting
-   slots
-   shadow boundaries
-   CSS custom properties across boundaries
-   accessibility implications

------------------------------------------------------------------------

# Part 112 --- Custom Elements

Lifecycle callbacks include concepts such as:

-   constructor
-   connectedCallback
-   disconnectedCallback
-   adoptedCallback
-   attributeChangedCallback

Learn:

-   observed attributes
-   custom element naming
-   upgrade timing
-   component lifecycle
-   custom states

------------------------------------------------------------------------

# Part 113 --- Templates and Slots

Template:

``` html
<template id="card-template">
  <article>
    <slot name="title"></slot>
  </article>
</template>
```

Slots allow light DOM content to be projected into a component.

Learn:

-   template cloning
-   slot assignment
-   named slots
-   fallback content
-   slotchange
-   shadow DOM composition

------------------------------------------------------------------------

# Part 114 --- Progressive Web Apps

PWA architecture commonly uses:

``` text
Web App
 +
Web Manifest
 +
Service Worker
 +
HTTPS
 +
Offline/Install Experience
```

Learn:

-   manifest
-   icons
-   display modes
-   service workers
-   caching
-   offline UX
-   update strategies
-   installability concepts

------------------------------------------------------------------------

# Part 115 --- Accessibility Engineering

Advanced accessibility includes:

-   WCAG concepts
-   semantic HTML
-   ARIA
-   keyboard navigation
-   focus management
-   dialogs
-   menus
-   tabs
-   comboboxes
-   live regions
-   accessible forms
-   screen readers
-   reduced motion
-   high contrast
-   zoom
-   touch accessibility

Test using:

-   keyboard only
-   screen reader
-   browser accessibility tools
-   automated audits

------------------------------------------------------------------------

# Part 116 --- Browser DevTools

Master:

## Elements

-   DOM inspection
-   CSS inspection
-   computed styles
-   layout tools
-   accessibility

## Console

-   JavaScript
-   logging
-   errors
-   live expressions

## Network

-   requests
-   headers
-   payloads
-   timing
-   caching
-   cookies
-   WebSockets

## Sources

-   breakpoints
-   conditional breakpoints
-   async debugging
-   source maps

## Performance

-   recordings
-   long tasks
-   layout
-   paint
-   scripting

## Memory

-   heap snapshots
-   allocation analysis
-   detached DOM

## Application

-   storage
-   IndexedDB
-   cache
-   service workers
-   manifests

------------------------------------------------------------------------

# Part 117 --- Testing

Testing layers:

``` text
Unit
 ↓
Integration
 ↓
Component
 ↓
End-to-End
 ↓
Performance
 ↓
Accessibility
```

Learn:

-   assertions
-   mocks
-   spies
-   fixtures
-   browser environments
-   DOM testing
-   network mocking
-   visual regression
-   accessibility testing

------------------------------------------------------------------------

# Part 118 --- Browser Automation

Learn browser automation concepts:

-   navigation
-   element selection
-   clicks
-   keyboard
-   forms
-   screenshots
-   network interception
-   waiting
-   multiple pages
-   iframes
-   permissions
-   downloads

Tools commonly used in industry include browser automation frameworks
such as Playwright and WebDriver-based solutions.

------------------------------------------------------------------------

# Part 119 --- Type Safety and TypeScript Concepts

Even in a JavaScript-focused stack, understand:

-   static typing
-   interfaces
-   unions
-   intersections
-   generics
-   narrowing
-   structural typing
-   declaration files
-   JavaScript type checking

TypeScript adds a compile-time type system; it does not change the
browser runtime into a typed runtime.

------------------------------------------------------------------------

# Part 120 --- npm and Frontend Tooling

Learn:

-   package.json
-   dependencies
-   devDependencies
-   semantic versioning
-   lockfiles
-   npm scripts
-   package resolution
-   security auditing
-   monorepos
-   workspaces

------------------------------------------------------------------------

# Part 121 --- Bundlers and Build Pipelines

Understand:

``` text
Source
 ↓
Transform
 ↓
Bundle
 ↓
Optimize
 ↓
Hash
 ↓
Deploy
```

Learn:

-   bundling
-   tree shaking
-   minification
-   code splitting
-   dynamic imports
-   asset processing
-   CSS processing
-   chunking
-   cache busting

------------------------------------------------------------------------

# Part 122 --- Source Maps

Source maps connect production code back to original source.

Learn:

-   mappings
-   browser debugging
-   JavaScript source maps
-   CSS source maps
-   security/privacy implications of publishing source maps

------------------------------------------------------------------------

# Part 123 --- Linting and Formatting

Learn:

-   lint rules
-   formatting
-   code style
-   import ordering
-   unused variables
-   accessibility linting
-   CI checks
-   pre-commit validation

Automated quality checks should run consistently in development and CI.

------------------------------------------------------------------------

# Part 124 --- Frontend Architecture

A scalable frontend can be separated conceptually:

``` text
Presentation
    ↓
Components
    ↓
State / Application Logic
    ↓
Domain Logic
    ↓
API / Infrastructure
```

Learn:

-   separation of concerns
-   dependency direction
-   feature modules
-   shared infrastructure
-   domain boundaries
-   component boundaries

------------------------------------------------------------------------

# Part 125 --- State Management

Types of state:

-   local UI state
-   form state
-   server state
-   URL state
-   session state
-   global application state
-   cached data

Avoid putting everything into one global store.

Choose state location based on ownership and lifecycle.

------------------------------------------------------------------------

# Part 126 --- Component Architecture

A component should have:

-   clear inputs
-   clear outputs/events
-   predictable state
-   accessible markup
-   isolated styling
-   testable behavior

Learn:

-   composition
-   props/attributes
-   events
-   slots
-   controlled/uncontrolled patterns
-   reusable primitives
-   design systems

------------------------------------------------------------------------

# Part 127 --- API Integration Architecture

Build a consistent API layer.

Concept:

``` text
Component
   ↓
Application Service
   ↓
API Client
   ↓
Fetch
   ↓
Backend
```

Handle:

-   loading
-   success
-   empty state
-   errors
-   retries
-   cancellation
-   caching
-   authorization
-   stale data

------------------------------------------------------------------------

# Part 128 --- Authentication and Authorization

Frontend responsibilities include:

-   displaying authentication state
-   sending credentials correctly
-   handling expiration
-   redirecting
-   protecting UI routes

Backend responsibilities include:

-   authenticating
-   authorizing
-   validating permissions
-   enforcing access control

Never rely on hidden frontend buttons as authorization.

------------------------------------------------------------------------

# Part 129 --- Real-Time Applications

Architectures:

-   WebSocket
-   SSE
-   polling
-   long polling

Learn:

-   reconnect
-   heartbeat
-   message ordering
-   duplicate handling
-   idempotency
-   connection state
-   backoff
-   server scaling

------------------------------------------------------------------------

# Part 130 --- Offline-First Applications

Learn:

-   service worker
-   Cache API
-   IndexedDB
-   sync queues
-   optimistic updates
-   conflict resolution
-   retry
-   stale data
-   offline UI

Offline applications need explicit data consistency rules.

------------------------------------------------------------------------

# Part 131 --- CSS + JavaScript Integration

JavaScript can control:

-   classes
-   inline styles
-   CSS variables
-   animations
-   media queries
-   computed styles

Preferred:

``` js
element.classList.toggle("open");
```

rather than constructing large inline style strings.

Use CSS for presentation and JavaScript for state/behavior.

------------------------------------------------------------------------

# Part 132 --- HTML + JavaScript Integration

Typical:

``` html
<button id="save">Save</button>
```

``` js
const save = document.querySelector("#save");

save.addEventListener("click", saveData);
```

Learn:

-   script loading
-   DOM readiness
-   modules
-   data attributes
-   event handlers
-   progressive enhancement
-   custom elements

------------------------------------------------------------------------

# Part 133 --- HTML + CSS Integration

Ways CSS enters HTML:

``` html
<link rel="stylesheet" href="app.css">
```

``` html
<style>
  body { margin: 0; }
</style>
```

Inline:

``` html
<div style="display:none"></div>
```

For maintainability, external/component styles are generally preferable
to excessive inline styles.

------------------------------------------------------------------------

# Part 134 --- Browser Compatibility

Learn:

-   standards
-   feature detection
-   compatibility tables
-   progressive enhancement
-   graceful degradation
-   polyfills
-   transpilation
-   vendor prefixes
-   baseline concepts

Prefer capability detection over browser-name detection.

------------------------------------------------------------------------

# Part 135 --- Progressive Enhancement

Start with working HTML.

Then add:

``` text
HTML
 ↓
CSS
 ↓
JavaScript enhancements
 ↓
Advanced browser capabilities
```

A good application should degrade gracefully when optional capabilities
are unavailable.

------------------------------------------------------------------------

# Part 136 --- Security Headers

Understand:

-   Content-Security-Policy
-   Strict-Transport-Security
-   X-Content-Type-Options
-   Referrer-Policy
-   Permissions-Policy
-   frame-ancestors
-   Cross-Origin-Opener-Policy
-   Cross-Origin-Resource-Policy
-   Cross-Origin-Embedder-Policy

Headers must be configured based on actual application requirements.

------------------------------------------------------------------------

# Part 137 --- Performance Architecture

Think at multiple levels:

``` text
Network
 ↓
HTML
 ↓
CSS
 ↓
JavaScript
 ↓
DOM
 ↓
Rendering
 ↓
Interaction
```

Performance architecture includes:

-   server response time
-   caching
-   CDN
-   compression
-   resource prioritization
-   code splitting
-   image optimization
-   lazy loading
-   rendering efficiency
-   memory management

------------------------------------------------------------------------

# Part 138 --- Error Monitoring and Observability

Learn:

-   console errors
-   uncaught exceptions
-   unhandled promise rejections
-   resource failures
-   network errors
-   performance telemetry
-   user context
-   breadcrumbs
-   source maps
-   privacy-aware logging

Do not send secrets or sensitive user data into logs.

------------------------------------------------------------------------

# Part 139 --- Production Deployment

Understand:

``` text
Source
 ↓
Build
 ↓
Artifacts
 ↓
CDN/Web Server
 ↓
Browser
```

Learn:

-   HTTPS
-   CDN
-   caching headers
-   immutable assets
-   compression
-   deployment strategies
-   rollback
-   environment configuration
-   monitoring
-   security headers

------------------------------------------------------------------------

# Part 140 --- Frontend Code Quality

Principles:

-   readable code
-   small functions
-   explicit contracts
-   predictable state
-   semantic HTML
-   maintainable CSS
-   accessible UI
-   error handling
-   tests
-   documentation
-   consistent tooling

------------------------------------------------------------------------

# Part 141 --- Common Anti-Patterns

Avoid:

-   giant components
-   global mutable state everywhere
-   excessive DOM manipulation
-   unnecessary re-renders
-   huge JS bundles
-   deeply nested CSS selectors
-   excessive `!important`
-   browser sniffing
-   insecure `innerHTML`
-   storing secrets in frontend code
-   client-only authorization
-   memory leaks
-   polling when observers/events are appropriate
-   blocking the main thread

------------------------------------------------------------------------

# Part 142 --- Practical Projects

Build progressively:

## Project 1 --- Semantic Website

Use:

-   HTML
-   semantic elements
-   CSS
-   responsive layout
-   accessibility

## Project 2 --- Form Application

Use:

-   HTML forms
-   validation
-   JavaScript
-   Fetch
-   error handling

## Project 3 --- Dashboard

Use:

-   CSS Grid
-   responsive components
-   API integration
-   charts
-   loading states

## Project 4 --- SPA

Use:

-   modules
-   routing
-   state
-   API layer
-   authentication

## Project 5 --- Offline Application

Use:

-   service worker
-   Cache API
-   IndexedDB
-   offline UX

## Project 6 --- Real-Time Dashboard

Use:

-   WebSocket/SSE
-   reconnect
-   state synchronization
-   performance optimization

## Project 7 --- Design System

Build:

-   buttons
-   inputs
-   modal
-   dropdown
-   tabs
-   tooltip
-   form controls
-   accessibility
-   tokens
-   Web Components

## Project 8 --- Production Web Application

Combine:

-   semantic HTML
-   advanced CSS
-   JavaScript
-   API integration
-   authentication
-   security
-   testing
-   performance
-   accessibility
-   observability
-   deployment

------------------------------------------------------------------------

# Part 143 --- Professional Checklists

## HTML Checklist

-   [ ] Semantic structure
-   [ ] Valid document structure
-   [ ] Correct heading hierarchy
-   [ ] Accessible forms
-   [ ] Correct labels
-   [ ] Image alternatives
-   [ ] Responsive images
-   [ ] Metadata
-   [ ] SEO basics
-   [ ] Structured data where appropriate
-   [ ] Keyboard accessibility

## CSS Checklist

-   [ ] Understand cascade
-   [ ] Control specificity
-   [ ] Use responsive layout
-   [ ] Flexbox
-   [ ] Grid
-   [ ] Container queries
-   [ ] Responsive typography
-   [ ] Logical properties
-   [ ] Reduced motion
-   [ ] Maintainable architecture

## JavaScript Checklist

-   [ ] Types
-   [ ] Scope
-   [ ] Closures
-   [ ] Objects
-   [ ] Prototypes
-   [ ] Classes
-   [ ] Arrays
-   [ ] Modules
-   [ ] Promises
-   [ ] Async/await
-   [ ] Event loop
-   [ ] Error handling
-   [ ] Memory management

## Browser Checklist

-   [ ] DOM
-   [ ] Events
-   [ ] Fetch
-   [ ] Storage
-   [ ] IndexedDB
-   [ ] Workers
-   [ ] Service workers
-   [ ] WebSockets
-   [ ] Security model
-   [ ] Rendering
-   [ ] Performance
-   [ ] DevTools

------------------------------------------------------------------------

# Part 144 --- Final Mastery Path

## Level 1 --- Foundations

Master:

``` text
HTML
CSS
JavaScript syntax
DOM basics
Events
HTTP basics
```

## Level 2 --- Frontend Developer

Master:

``` text
Responsive CSS
Forms
Fetch
Async JavaScript
Modules
Component architecture
Accessibility
Testing
```

## Level 3 --- Advanced Frontend Engineer

Master:

``` text
Browser internals
Event loop
Rendering
Performance
Security
Workers
Service workers
IndexedDB
Web Components
Advanced CSS
```

## Level 4 --- Professional

Master:

``` text
Architecture
State management
API design integration
Authentication
Real-time systems
Offline systems
Observability
CI/CD
Production deployment
```

## Level 5 --- Web Platform Specialist

Master:

``` text
DOM
CSSOM
HTML parsing
CSS cascade
Rendering pipeline
Event loop
Browser security
Origin model
CORS
CSP
Workers
Service workers
Web Components
Storage
Media APIs
Graphics
Performance APIs
Accessibility tree
Browser DevTools
Standards and compatibility
```

------------------------------------------------------------------------

# Final Mental Model

The complete web platform can be understood as:

``` text
                    INTERNET
                       │
                    HTTP/HTTPS
                       │
                    BROWSER
                       │
       ┌───────────────┼────────────────┐
       │               │                │
      HTML            CSS          JavaScript
       │               │                │
       ↓               ↓                ↓
      DOM             CSSOM          JS Runtime
       └───────────────┼────────────────┘
                       │
                 Browser Web APIs
                       │
       ┌───────────────┼────────────────────┐
       │               │                    │
    Network          Storage             Media
       │               │                    │
   Fetch/WS/SSE   IndexedDB/Cache      Audio/Video
       │               │                    │
       ├───────────────┼────────────────────┤
       │
    Workers / Service Workers
       │
    Security / Permissions
       │
    Rendering Pipeline
       │
    Layout → Paint → Composite
       │
      SCREEN
```

## The Most Important Concept

Do not learn HTML, CSS, and JavaScript as three completely separate
subjects.

Learn the **relationships**:

``` text
HTML
  → creates DOM

CSS
  → creates CSS rules/CSSOM
  → styles DOM

JavaScript
  → reads/changes DOM
  → reads/changes styles
  → responds to events
  → communicates with servers
  → uses browser APIs

Browser
  → executes JavaScript
  → parses HTML
  → calculates styles
  → performs layout
  → paints
  → composites
  → enforces security
  → manages storage/network/device APIs
```

That integrated mental model is the foundation for becoming a senior
frontend engineer and understanding the web platform rather than merely
memorizing framework APIs.
