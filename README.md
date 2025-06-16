### **PART – A**

**Answer any six questions (6x2=12)**


**1. a) What is the use of `cellpadding` and `cellspacing` attributes in `<table>` element?**

The `cellpadding` and `cellspacing` are attributes of the `<table>` element used to control spacing.

* **`cellpadding`**: This attribute specifies the space, in pixels, between the content of a table cell and the cell's border.
* **`cellspacing`**: This attribute specifies the space, in pixels, between adjacent table cells and between the cells and the table border.

**Note**: Both attributes are deprecated in HTML5. The modern and recommended approach is to use the CSS `padding` and `border-spacing` properties.

---

**1. b) What are the uses of `===` and `!==` operators of JavaScript?**

The `===` and `!==` operators in JavaScript are used for strict comparison.

* **`===` (Strict Equality)**: This operator returns `true` if two operands are equal in **value** and of the same **data type**, without performing any type coercion.
    * Example: `5 === 5` is `true`, but `5 === '5'` is `false`.

* **`!==` (Strict Inequality)**: This operator returns `true` if the two operands are not equal in value or are not of the same data type.
    * Example: `5 !== '5'` is `true`.

---

**1. c) Expand CSS. What is the use of CSS?**

**CSS** stands for **Cascading Style Sheets**.

**Use of CSS**: CSS is a stylesheet language used to describe the presentation and styling of a document written in a markup language like HTML. Its primary purpose is to separate the document's content (HTML) from its presentation (style), allowing for more control over layout, colors, fonts, and overall visual appearance.

---

**1. d) What are the values can be used for transition timing function?**

The `transition-timing-function` property in CSS specifies the speed curve of a transition effect. The common values are:

* `ease`: The default value; specifies a slow start, then fast, then end slowly.
* `linear`: Specifies a transition with the same speed from start to end.
* `ease-in`: Specifies a slow start.
* `ease-out`: Specifies a slow end.
* `ease-in-out`: Specifies a transition with a slow start and a slow end.
* `cubic-bezier(n,n,n,n)`: Allows you to define your own timing function.

---

**1. e) What are the advantages of SVG `<tspan>` element?**

The `<tspan>` element is used inside an SVG `<text>` element and provides several advantages:

1.  **Fine-Grained Styling**: It allows different styling (like `fill`, `stroke`, `font-size`) to be applied to different parts of a single text string.
2.  **Precise Positioning**: It allows specific substrings to be repositioned using attributes like `x`, `y`, `dx` (relative horizontal shift), and `dy` (relative vertical shift), without affecting the rest of the text.

---

**1. f) What is SVG Viewbox attribute? List the SVG elements with which Viewbox attribute can be used.**

The **`viewBox`** attribute in SVG defines the position and dimension of a user coordinate system for an SVG image. It allows the SVG to scale to fit its container while preserving its aspect ratio. The attribute takes four values: `min-x`, `min-y`, `width`, and `height`.

The `viewBox` attribute can be used with the following SVG elements:
* `<svg>`
* `<symbol>`
* `<marker>`
* `<pattern>`
* `<image>`

---

**1. g) Write the javascript code to create canvas drawing context.**

To create a canvas drawing context, you first need to get a reference to the `<canvas>` element from the DOM, and then call its `getContext()` method.

```javascript
// 1. Get the canvas element from the HTML document
const canvasElement = document.getElementById('myCanvas');

// 2. Get the 2D rendering context
const ctx = canvasElement.getContext('2d');
```

---

**1. h) List the parameters of the canvas fillRect() method with their purpose.**

The `fillRect(x, y, width, height)` method draws a filled rectangle. It takes four parameters:

1.  **`x`**: The x-axis coordinate of the top-left corner of the rectangle's starting point.
2.  **`y`**: The y-axis coordinate of the top-left corner of the rectangle's starting point.
3.  **`width`**: The width of the rectangle in pixels.
4.  **`height`**: The height of the rectangle in pixels.

***

### **PART – B**

### **Unit – I**

**2. a) What is the use of `<OL>` tag? Explain with attributes.** (4 Marks)

The `<ol>` tag in HTML is used to define an **ordered list**. This is a list where each item is numbered, and the order of the items is meaningful. By default, list items are marked with numbers (1, 2, 3...).

The behavior of the `<ol>` tag can be modified using its attributes:

1.  **`type`**: This attribute specifies the kind of marker to use for the list items.
    * `'1'`: Default value. Items are numbered with decimal numbers (1, 2, 3...).
    * `'A'`: Items are numbered with uppercase letters (A, B, C...).
    * `'a'`: Items are numbered with lowercase letters (a, b, c...).
    * `'I'`: Items are numbered with uppercase Roman numerals (I, II, III...).
    * `'i'`: Items are numbered with lowercase Roman numerals (i, ii, iii...).

2.  **`start`**: This attribute specifies the starting number for the list. It must be an integer.
    * Example: `start="5"` will begin the list with the number 5.

3.  **`reversed`**: This is a boolean attribute. If present, it specifies that the list order should be descending (e.g., 3, 2, 1).

**Example:**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Ordered List Example</title>
</head>
<body>
    <h4>List with lowercase letters, starting from 'c'</h4>
    <ol type="a" start="3">
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
    </ol>

    <h4>Reversed list</h4>
    <ol reversed>
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
    </ol>
</body>
</html>
```

---

**2. b) Explain any 4 `<input>` tags with their element specific attributes.** (4 Marks)

The `<input>` tag is used to create interactive controls for web-based forms. Here are four different input types with their specific attributes:

**1. Input Type `text`**
   Used for a single-line text input field.
   * **`maxlength`**: Specifies the maximum number of characters allowed in the field.
   * **`placeholder`**: Provides a short hint that describes the expected value of the input field.
   * **`pattern`**: Specifies a regular expression that the input's value must match.
   * **Example**: `<input type="text" placeholder="Enter your name" maxlength="50">`

**2. Input Type `number`**
   Used for input fields that should contain a numerical value.
   * **`min`**: Specifies the minimum allowed value.
   * **`max`**: Specifies the maximum allowed value.
   * **`step`**: Specifies the legal number intervals (e.g., `step="2"` allows 0, 2, 4...).
   * **Example**: `<input type="number" min="1" max="100" step="1">`

**3. Input Type `range`**
   Used for a control that lets the user specify a numeric value within a given range; it is displayed as a slider.
   * **`min`**: Specifies the minimum value of the range.
   * **`max`**: Specifies the maximum value of the range.
   * **`step`**: Specifies the granularity of the value.
   * **Example**: `<input type="range" min="0" max="10" step="1">`

**4. Input Type `checkbox`**
   Used for a checkbox, which allows the user to select zero or more options from a set.
   * **`checked`**: A boolean attribute that, if present, specifies that the checkbox should be pre-selected when the page loads.
   * **`value`**: The value that is sent to the server when the form is submitted if the checkbox is checked.
   * **Example**: `<input type="checkbox" name="vehicle" value="Car" checked> I have a car`

---

**2. c) Explain `addEventListener()` method with example.** (4 Marks)

The `addEventListener()` method is the modern, standard way to register an event handler for a specific HTML element. It allows you to attach a function that will be executed whenever a specified event (like a click or mouseover) occurs on that element. You can add multiple event handlers to a single element without overwriting existing ones.

**Syntax:**
`element.addEventListener(event, function, useCapture);`

* **`event`**: A string representing the event type to listen for (e.g., `'click'`, `'mouseover'`, `'keydown'`).
* **`function`**: The function or object to be called when the event occurs.
* **`useCapture`** (optional): A boolean value that specifies the event propagation phase. `false` (default) uses the bubbling phase, while `true` uses the capturing phase.

**Example:**
This example shows how to change the text of a paragraph when a button is clicked using `addEventListener()`.

```html
<!DOCTYPE html>
<html>
<head>
    <title>addEventListener Example</title>
</head>
<body>

    <button id="myButton">Click Me</button>
    <p id="myParagraph">Hello World!</p>

    <script>
        // Get references to the HTML elements
        const button = document.getElementById('myButton');
        const paragraph = document.getElementById('myParagraph');

        // Define the function to run on the event
        function changeText() {
            paragraph.textContent = 'The button was clicked!';
        }

        // Add an event listener to the button
        // It will call the changeText function when a 'click' event occurs
        button.addEventListener('click', changeText);
    </script>

</body>
</html>
```

---

**3. a) What is the use of `<a>` tag? Explain the use of `href`, `target` and `name` attributes.** (4 Marks)

The `<a>` tag, known as the **anchor tag**, is a fundamental HTML element used to create hyperlinks. These links can point to other web pages, files, locations within the same page, or other URLs.

The behavior of the anchor tag is controlled by its attributes:

1.  **`href` (Hypertext Reference)**: This is the most important attribute of the `<a>` tag. It specifies the URL (Uniform Resource Locator) or destination of the link. The value can be an absolute URL (e.g., `https://www.google.com`) or a relative URL (e.g., `/about.html`).

2.  **`target`**: This attribute specifies where to open the linked document.
    * **`_self`**: (Default) Opens the document in the same window/tab as it was clicked.
    * **`_blank`**: Opens the document in a new window or tab.
    * **`_parent`**: Opens the document in the parent frameset.
    * **`_top`**: Opens the document in the full body of the window.

3.  **`name`**: This attribute was used in older versions of HTML (HTML4) to create a named anchor within a page. This named anchor could then be used as the destination for another link, allowing users to jump to specific sections of a document.
    * **Note**: The `name` attribute is **obsolete in HTML5**. The modern and correct way to create an in-page anchor is to use the **`id`** attribute on any element.

**Example:**
```html
<a href="https://www.wikipedia.org/" target="_blank">Visit Wikipedia</a>

<a href="#section2">Go to Section 2</a>

<h2 id="section2">This is Section 2</h2>
```

---

**3. b) Briefly describe `confirm()` and `alert()` methods.** (4 Marks)

The `alert()` and `confirm()` methods are part of the `window` object in JavaScript. They are used to create simple modal dialog boxes to interact with the user.

**1. `alert()` method**
The `alert()` method displays a dialog box with a specified message and an "OK" button. It is used to give information to the user that they must acknowledge. The script execution is paused until the user clicks "OK". It does not return any value.

**Syntax:**
`alert("message");`

**Example:**
```javascript
alert("Your form has been submitted successfully!");
// The code will pause here until the user clicks OK.
console.log("Alert box was closed.");
```

**2. `confirm()` method**
The `confirm()` method displays a dialog box with a specified message, an "OK" button, and a "Cancel" button. It is used to ask the user a yes/no question.
* If the user clicks "OK", the method returns `true`.
* If the user clicks "Cancel", the method returns `false`.

**Syntax:**
`let result = confirm("message");`

**Example:**
```javascript
let userChoice = confirm("Are you sure you want to delete this item?");

if (userChoice) {
  console.log("User chose to delete."); // This runs if user clicks OK
} else {
  console.log("User canceled the deletion."); // This runs if user clicks Cancel
}
```

---

**3. c) Write a note on JavaScript with its features.** (4 Marks)

**JavaScript (JS)** is a high-level, dynamic, and interpreted (or just-in-time compiled) programming language. It is one of the core technologies of the World Wide Web, alongside HTML and CSS. Originally developed for client-side scripting to make web pages interactive, its use has expanded to server-side development (Node.js), mobile apps, and more.

**Key Features of JavaScript:**

* **Client-Side Scripting**: Its primary role is to run in the user's web browser, enabling dynamic behavior like form validation, DOM manipulation, animations, and handling user events without needing to communicate with the server.
* **Asynchronous Behavior**: JavaScript supports asynchronous operations through features like Callbacks, Promises, and `async/await`. This allows long-running tasks (like fetching data from a server) to be performed without freezing the user interface.
* **Dynamic Typing**: It is a dynamically typed language, meaning variable types are determined at runtime, not compile time. This provides flexibility but requires careful handling. `let x = 5; x = "hello";` is valid.
* **Platform Independent**: JavaScript code can run on any platform that has a JavaScript engine (typically a web browser), making it highly portable.
* **Large Ecosystem**: It has a vast ecosystem of libraries (like jQuery, React) and frameworks (like Angular, Vue.js) that simplify and accelerate development.
* **Event-Driven**: JavaScript is designed to respond to user actions and system events, such as clicks, mouse movements, and key presses, making it ideal for building interactive applications.

### **Unit – II**

**4. a) Explain different ways of using style sheets in HTML5.** (4 Marks)

There are three primary ways to apply CSS (style sheets) to an HTML5 document. They differ in scope and best practices.

**1. Inline Styles**
   Inline styles are applied directly to a single HTML element using the `style` attribute. This method has the highest specificity but is generally considered bad practice for anything other than quick testing or very specific dynamic styling, as it mixes content with presentation and is hard to maintain.

   **Example:**
   ```html
   <p style="color: blue; font-size: 16px;">This paragraph is styled with inline CSS.</p>
   ```

**2. Internal (or Embedded) Style Sheets**
   Internal styles are defined within the `<style>` tag, which is placed inside the `<head>` section of an HTML document. These styles apply only to the current HTML page. This is useful for single-page styling or for styles that are unique to one specific page.

   **Example:**
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>Internal CSS</title>
       <style>
           body {
               background-color: #f0f0f0;
           }
           p {
               color: green;
           }
       </style>
   </head>
   <body>
       <p>This paragraph is styled by the internal style sheet.</p>
   </body>
   </html>
   ```

**3. External Style Sheets**
   External styles are defined in a separate `.css` file. This file is then linked to the HTML document using the `<link>` tag inside the `<head>` section. This is the **most recommended** method because it completely separates structure (HTML) from presentation (CSS), allows for reusing the same stylesheet across multiple pages, and makes maintenance much easier.

   **HTML file (`index.html`):**
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>External CSS</title>
       <link rel="stylesheet" href="styles.css">
   </head>
   <body>
       <h1>This heading is styled by an external file.</h1>
   </body>
   </html>
   ```

   **CSS file (`styles.css`):**
   ```css
   h1 {
       color: navy;
       text-align: center;
   }
   ```
---
**4. b) Explain all the animation related properties.** (4 Marks)

CSS animations allow for the gradual transition of an element from one style configuration to another. This is achieved using the `@keyframes` at-rule and several animation properties.

First, you define an animation using `@keyframes`:
```css
@keyframes slide-in {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}
```
Then, you apply it to an element using the following properties:

* **`animation-name`**: Specifies the name of the `@keyframes` rule to apply.
    * Example: `animation-name: slide-in;`

* **`animation-duration`**: Defines the length of time an animation cycle takes to complete.
    * Example: `animation-duration: 2s;` (2 seconds)

* **`animation-timing-function`**: Describes the speed curve of the animation (e.g., `linear`, `ease`, `ease-in-out`).
    * Example: `animation-timing-function: ease;`

* **`animation-delay`**: Specifies a delay before the animation starts.
    * Example: `animation-delay: 1s;`

* **`animation-iteration-count`**: Defines how many times the animation cycle should be repeated. Can be a number or `infinite`.
    * Example: `animation-iteration-count: infinite;`

* **`animation-direction`**: Specifies whether the animation should be played forwards, backwards, or in alternate cycles.
    * Values: `normal`, `reverse`, `alternate`, `alternate-reverse`.
    * Example: `animation-direction: alternate;`

* **`animation-fill-mode`**: Sets the styles for the element when the animation is not playing (i.e., before it starts or after it ends).
    * Values: `none`, `forwards`, `backwards`, `both`.
    * Example: `animation-fill-mode: forwards;` (retains the style of the last keyframe)

* **`animation-play-state`**: Allows for pausing and resuming the animation.
    * Values: `running` (default), `paused`.
    * Example: `animation-play-state: paused;`

* **`animation` (Shorthand)**: A shorthand property to set all the animation properties in one declaration.
    * Example: `animation: slide-in 2s ease 1s infinite alternate forwards;`

---

**4. c) Explain `clear` property of CSS3 with all its options.** (4 Marks)

The `clear` property in CSS is used to control the behavior of elements adjacent to floating elements. When an element has a `float` property (e.g., `float: left;`), subsequent elements in the markup will wrap around it. The `clear` property is applied to these subsequent elements to prevent them from wrapping and instead push them below the floated element.

The `clear` property can have the following values:

* **`none`**: This is the default value. It allows the element to be positioned next to floating elements on both sides.

* **`left`**: Pushes the element down to be below any preceding elements that are floated to the left. The top margin of the cleared element will be below the bottom margin of the left-floating element.

* **`right`**: Pushes the element down to be below any preceding elements that are floated to the right.

* **`both`**: This is the most commonly used value. It pushes the element down to be below all preceding floated elements, whether they are floated left or right.

* **`inherit`**: The element inherits the `clear` value from its parent element.

**Example:**
Without `clear`, the paragraph would wrap around the floated image. With `clear: left;`, it is forced below the image.

```html
<style>
    .floated-image {
        float: left;
        width: 100px;
        height: 100px;
        margin-right: 15px;
    }
    .cleared-paragraph {
        clear: left; /* Could also be 'both' */
    }
</style>

<img src="image.jpg" class="floated-image">
<p class="cleared-paragraph">
    This paragraph has the 'clear' property applied, so it will start below the floated image instead of wrapping around it.
</p>
```
---
**5. a) Explain `overflow` property of CSS3 with all of its options.** (4 Marks)

The `overflow` property in CSS is used to control what happens to content that is too large to fit into an element's designated area (its content box).

The `overflow` property has the following main values:

* **`visible`**: This is the default value. If content overflows the element's box, it is not clipped and will render outside the element's borders. This can cause the content to overlap with other elements on the page.

* **`hidden`**: Any content that overflows the element's box is clipped and becomes invisible. There are no scrollbars, so the user cannot access the hidden content.

* **`scroll`**: The content is clipped, but the browser displays scrollbars (both horizontal and vertical) to allow the user to see the rest of the content. Scrollbars are shown regardless of whether the content actually overflows or not.

* **`auto`**: This value is similar to `scroll`, but it is more intelligent. Scrollbars are only added if the content actually overflows. This is often the preferred choice for creating scrollable areas as it avoids unnecessary scrollbars.

**Example:**
```html
<style>
    .box {
        width: 200px;
        height: 100px;
        border: 1px solid black;
        overflow: auto; /* Try changing this to visible, hidden, or scroll */
    }
</style>

<div class="box">
    This is a lot of text inside a small container.
    The overflow property will determine how this excess content is handled.
    Using 'auto' will add a scrollbar only when needed.
</div>
```

---

**5. b) Explain all the possible values for `animation-fill-mode` property.** (4 Marks)

The `animation-fill-mode` CSS property specifies how a CSS animation should apply styles to its target element outside of its execution time (i.e., before the animation begins and after it ends).

Here are the four possible values:

1.  **`none`** (Default):
    The animation will not apply any styles to the element before or after it is executing. Once the animation finishes, the element will revert back to its original styles, as if the animation never happened.

2.  **`forwards`**:
    After the animation ends (i.e., it has completed all its iterations), the element will retain the style values set by the last keyframe (the `100%` or `to` keyframe). It will not revert to its original state.

3.  **`backwards`**:
    Before the animation starts (during the `animation-delay` period), the element will immediately adopt the style values set by the first keyframe (the `0%` or `from` keyframe). Once the animation ends, it reverts to its original state (unless combined with `forwards`).

4.  **`both`**:
    This value applies the rules for both `forwards` and `backwards`. The animation's styles will be applied before it begins (as with `backwards`) and will be retained after it ends (as with `forwards`).

**Example Scenario:**
Imagine an animation that moves an element from `left: 0px` to `left: 100px` with a 2-second delay.

* `none`: The element stays at its original position for 2s, moves, and then snaps back to the original position.
* `forwards`: The element stays at its original position for 2s, moves, and then **stays at `left: 100px`**.
* `backwards`: The element **snaps to `left: 0px` immediately**, waits 2s, moves, and then snaps back to its original position.
* `both`: The element **snaps to `left: 0px` immediately**, waits 2s, moves, and then **stays at `left: 100px`**.

---

**5. c) Explain the pseudo-classes used to style link.** (4 Marks)

Pseudo-classes are used in CSS to define a special state of an element. For styling links (`<a>` tags), there are four main pseudo-classes that correspond to the different states a link can be in.

It is recommended to define them in the **LVHA order** (`:link`, `:visited`, `:hover`, `:active`) to ensure they work correctly due to CSS specificity rules.

1.  **`:link`**: This pseudo-class selects and styles links that are unvisited. It targets `<a>` elements that have an `href` attribute but have not yet been clicked by the user.
    * `a:link { color: blue; }`

2.  **`:visited`**: This pseudo-class selects and styles links that the user has already visited. For privacy reasons, browsers limit the styles that can be changed on a visited link (typically just `color`, `background-color`, `border-color`).
    * `a:visited { color: purple; }`

3.  **`:hover`**: This pseudo-class selects and styles a link when the user's mouse pointer is hovering over it. This provides visual feedback to the user.
    * `a:hover { color: red; text-decoration: underline; }`

4.  **`:active`**: This pseudo-class selects and styles a link during the moment it is being activated (i.e., when it is being clicked).
    * `a:active { color: orange; }`

**Example CSS Block:**
```css
/* LVHA Order */

/* Unvisited link */
a:link {
  color: #007bff;
}

/* Visited link */
a:visited {
  color: #6a0dad;
}

/* Mouse over link */
a:hover {
  color: #ff4500;
  text-decoration: none;
}

/* Selected link */
a:active {
  color: #ff0000;
}
```

### **Unit – III**

**6. a) Explain SVG drop shadow effect.** (4 Marks)

In SVG, a drop shadow effect is not a simple attribute but is created using **SVG filters**. The primary filter primitive used for this effect is **`<feDropShadow>`**.

The process involves these steps:
1.  Define a filter within a `<defs>` (definitions) block using the `<filter>` element. This filter is given a unique `id`.
2.  Inside the `<filter>`, place the `<feDropShadow>` element.
3.  Apply the filter to an SVG shape (like `<rect>`, `<circle>`, or `<text>`) using the `filter` attribute, referencing the filter's `id`.

The `<feDropShadow>` element has several attributes to control the shadow's appearance:
* **`dx`**: The horizontal offset of the shadow.
* **`dy`**: The vertical offset of the shadow.
* **`stdDeviation`**: The standard deviation for the blur operation. A larger number creates a more blurry shadow.
* **`flood-color`**: The color of the shadow.
* **`flood-opacity`**: The transparency of the shadow.

**Example:**
This code creates a blue rectangle with a semi-transparent black drop shadow.
```xml
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <filter id="drop-shadow-filter" x="-20%" y="-20%" width="140%" height="140%">
      <feDropShadow dx="4" dy="4" stdDeviation="3" flood-color="#000" flood-opacity="0.5" />
    </filter>
  </defs>

  <rect x="20" y="20" width="100" height="100" fill="cornflowerblue"
        filter="url(#drop-shadow-filter)" />
</svg>
```

---
**6. b) Explain all the variations of SVG `rotate()` function with its parameters.** (4 Marks)

The `rotate()` function is a transformation in SVG used to rotate an element. It is applied using the `transform` attribute. There are two variations of the `rotate()` function.

**1. Rotation around the Origin `rotate(<a>)`**
This variation takes a single parameter:
* **`<a>`**: The angle of rotation in degrees.

When only the angle is provided, the element is rotated around the origin of the current user coordinate system, which is the point `(0, 0)`.

**Example:** A rectangle is rotated 45 degrees around the top-left corner of the SVG canvas.
```xml
<svg width="150" height="150">
  <rect x="20" y="20" width="80" height="40" fill="#ccc"/>
  <rect x="20" y="20" width="80" height="40" fill="red"
        transform="rotate(45)" />
</svg>
```

**2. Rotation around a Specific Point `rotate(<a, cx, cy>)`**
This variation takes three parameters:
* **`<a>`**: The angle of rotation in degrees.
* **`cx`**: The x-coordinate of the center of rotation.
* **`cy`**: The y-coordinate of the center of rotation.

This is the more common and useful variation, as it allows you to rotate an element around its own center or any other arbitrary point.

**Example:** A rectangle is rotated 45 degrees around its own center point `(60, 40)`.
```xml
<svg width="150" height="150">
  <rect x="20" y="20" width="80" height="40" fill="blue"
        transform="rotate(45, 60, 40)" />
  <circle cx="60" cy="40" r="3" fill="white" />
</svg>
```
---
**6. c) Mention the rules of SVG color specification.** (4 Marks)

SVG uses the same color syntax as CSS. Colors in SVG are primarily applied using the `fill` (interior color) and `stroke` (outline color) attributes. The rules for specifying color values are as follows:

1.  **Named Colors**: A set of predefined color names are supported (e.g., `red`, `blue`, `green`, `black`). This is the most readable but least flexible method.
    * `fill="red"`

2.  **Hexadecimal Notation**: This is one of the most common methods. It represents colors in an RGB format.
    * **6-digit hex**: `#RRGGBB` (e.g., `#ff0000` for red).
    * **3-digit hex**: `#RGB` (e.g., `#f00` for red). This is a shorthand where each digit is duplicated.
    * `stroke="#0000ff"`

3.  **RGB / RGBA Notation**: Colors are specified as a mix of Red, Green, and Blue.
    * **`rgb(r, g, b)`**: Each value is an integer from 0 to 255.
        * `fill="rgb(255, 0, 0)"`
    * **`rgba(r, g, b, a)`**: Adds an alpha channel (`a`) for opacity, where `a` is a value from 0.0 (fully transparent) to 1.0 (fully opaque).
        * `fill="rgba(255, 0, 0, 0.5)"`

4.  **HSL / HSLA Notation**: Colors are specified by Hue, Saturation, and Lightness.
    * **`hsl(h, s, l)`**: Hue is an angle (0-360), saturation and lightness are percentages (0%-100%).
        * `fill="hsl(120, 100%, 50%)"` (lime green)
    * **`hsla(h, s, l, a)`**: Adds an alpha channel for opacity.
        * `fill="hsla(120, 100%, 50%, 0.5)"`

5.  **Special Keywords**:
    * **`transparent`**: Represents a fully transparent color.
    * **`currentColor`**: A variable keyword that resolves to the value of the CSS `color` property of the element. This is useful for making SVG icons inherit the text color.

---
**7. a) Explain all the variations of SVG `translate()` function with its parameters.** (4 Marks)

The `translate()` function is an SVG transformation used to move an element from one place to another without rotating or scaling it. It is applied using the `transform` attribute. There are two variations.

**1. Horizontal Translation `translate(<tx>)`**
This variation takes a single parameter:
* **`<tx>`**: The distance to move the element along the x-axis.

If only one value is provided, the translation along the y-axis (`ty`) is assumed to be `0`.

**Example:** A rectangle is moved 50 units to the right.
```xml
<svg width="200" height="100">
  <rect x="10" y="10" width="80" height="50" fill="#ccc" />
  <rect x="10" y="10" width="80" height="50" fill="green"
        transform="translate(50)" />
</svg>
```

**2. Horizontal and Vertical Translation `translate(<tx, ty>)`**
This variation takes two parameters:
* **`<tx>`**: The distance to move the element along the x-axis.
* **`<ty>`**: The distance to move the element along the y-axis.

This is the standard form, allowing movement in any direction on the 2D plane.

**Example:** A rectangle is moved 50 units to the right and 30 units down.
```xml
<svg width="200" height="100">
  <rect x="10" y="10" width="80" height="50" fill="#ccc" />
  <rect x="10" y="10" width="80" height="50" fill="purple"
        transform="translate(50, 30)" />
</svg>
```
---
**7. b) List and explain any four SVG color codes.** (4 Marks)

SVG supports various color code formats, similar to CSS. Here are four common types explained:

**1. Named Color**
   * **Description**: This is the simplest format, using predefined, case-insensitive names for common colors. There are over 140 standard color names.
   * **Syntax**: `colorname`
   * **Example**: `fill="blue"`, `stroke="gold"`
   * **Use Case**: Good for readability and for standard, non-specific colors.

**2. Hexadecimal Color Code**
   * **Description**: This format represents colors using base-16 numbers. It defines the Red, Green, and Blue components of the color. It can be written in a 3-digit or 6-digit shorthand.
   * **Syntax**: `#RRGGBB` or `#RGB`
   * **Example**: `fill="#FF0000"` (6-digit for red) or `fill="#F00"` (3-digit shorthand for red).
   * **Use Case**: The most widely used format on the web due to its conciseness and wide range of colors ($16^6$ possibilities).

**3. RGB Color Model (`rgb()`)**
   * **Description**: This format defines a color by specifying the intensity of its Red, Green, and Blue components. Each component is an integer value between 0 (none of the color) and 255 (full intensity).
   * **Syntax**: `rgb(red, green, blue)`
   * **Example**: `fill="rgb(0, 0, 255)"` for pure blue.
   * **Use Case**: Useful when colors are derived from calculations or when you need a more explicit representation than hex.

**4. RGBA Color Model (`rgba()`)**
   * **Description**: This is an extension of the RGB model that includes an "alpha" channel for opacity. The alpha value ranges from 0.0 (fully transparent) to 1.0 (fully opaque).
   * **Syntax**: `rgba(red, green, blue, alpha)`
   * **Example**: `fill="rgba(0, 0, 255, 0.5)"` defines a 50% transparent blue color.
   * **Use Case**: Essential for creating semi-transparent shapes, overlays, and effects where the background should be partially visible.

---
**7. c) Explain SVG Gaussian blur effect.** (4 Marks)

A Gaussian blur is an SVG filter effect that blurs an image or shape by applying a Gaussian function, resulting in a smooth, "hazy" blur. It is created using the **`<feGaussianBlur>`** filter primitive.

The process is similar to creating a drop shadow:
1.  Define a `<filter>` element with a unique `id` inside a `<defs>` block.
2.  Inside the filter, use the `<feGaussianBlur>` primitive.
3.  Apply the filter to an SVG element using the `filter` attribute with `url(#filter-id)`.

The key attribute for `<feGaussianBlur>` is:
* **`stdDeviation`**: This attribute defines the amount of blur. A value of 0 results in no blur. Larger values create more blur. It can take one number (for equal blur in x and y directions) or two numbers (for independent `blur-x` and `blur-y`).

**Example:**
This code creates text and applies a Gaussian blur to it.
```xml
<svg width="400" height="150" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <filter id="gaussian-blur-filter">
      <feGaussianBlur in="SourceGraphic" stdDeviation="4" />
    </filter>
  </defs>

  <text x="20" y="50" font-family="Verdana" font-size="45">Clear Text</text>

  <text x="20" y="110" font-family="Verdana" font-size="45"
        filter="url(#gaussian-blur-filter)">Blurred Text</text>
</svg>
```
The `in="SourceGraphic"` attribute tells the filter to apply the blur to the original element's graphics.

### **Unit – IV**

**8. a) Explain `setInterval()`, `setTimeout()`, `requestAnimationFrame()` methods with their parameters.** (6 Marks)

These three JavaScript methods are used to schedule the execution of code at a later time, but they have different use cases, particularly for animations.

**1. `setTimeout(function, delay, [param1, param2, ...])`**
   * **Purpose**: Executes a function or a piece of code **once** after a specified delay has passed.
   * **Parameters**:
        * `function`: The function to be executed.
        * `delay`: The time, in milliseconds (1000 ms = 1 second), to wait before executing the code.
        * `[param1, param2, ...]` (Optional): Additional arguments to pass to the function.
   * **Return Value**: It returns a numeric ID, which can be used with `clearTimeout(id)` to cancel the execution before it happens.
   * **Use Case**: Delaying an action, like showing a popup after 5 seconds or hiding a notification after it appears.

**2. `setInterval(function, delay, [param1, param2, ...])`**
   * **Purpose**: Executes a function or a piece of code **repeatedly**, with a fixed time delay between each call.
   * **Parameters**:
        * `function`: The function to be executed repeatedly.
        * `delay`: The interval, in milliseconds, between each execution.
        * `[param1, param2, ...]` (Optional): Additional arguments to pass to the function.
   * **Return Value**: It returns a numeric ID, which can be used with `clearInterval(id)` to stop the repeated executions.
   * **Use Case**: Creating a clock that updates every second, polling a server for updates, or running simple, non-performance-critical animations.

**3. `requestAnimationFrame(callback)`**
   * **Purpose**: Tells the browser that you wish to perform an animation and requests that the browser call a specified function to update an animation right before the next repaint.
   * **Parameters**:
        * `callback`: The function to call when it's time to update your animation for the next repaint. This function is passed one argument: a high-resolution timestamp.
   * **Return Value**: It returns an ID that can be used with `cancelAnimationFrame(id)` to cancel the callback request.
   * **Key Advantages over `setTimeout`/`setInterval` for Animations**:
        * **Efficiency**: The browser can optimize animations, leading to smoother performance. It syncs with the browser's refresh rate (typically 60fps).
        * **Power Saving**: Animations in inactive tabs are paused automatically, saving CPU, GPU, and battery life.
        * **Avoids Stuttering**: It prevents animations from running faster or slower than the screen can display, which can happen with `setInterval`.

**Conclusion**: For any kind of visual animation in the browser, **`requestAnimationFrame` is the modern and highly recommended approach**, while `setTimeout` and `setInterval` are better suited for general-purpose timing events.

---

**8. b) Explain `quadraticCurveTo()` and `bezierCurveTo()` methods of canvas with proper example.** (6 Marks)

Both `quadraticCurveTo()` and `bezierCurveTo()` are methods of the 2D canvas rendering context used to draw Bézier curves. They are used after setting a starting point with `moveTo()`.

**1. `quadraticCurveTo(cp1x, cp1y, x, y)`**
   * **Purpose**: Draws a quadratic Bézier curve. This type of curve is defined by a start point, an end point, and **one control point**. The curve starts at the current pen position and ends at `(x, y)`, bending towards the single control point `(cp1x, cp1y)`.
   * **Parameters**:
        * `cp1x`: The x-coordinate of the control point.
        * `cp1y`: The y-coordinate of the control point.
        * `x`: The x-coordinate of the end point of the curve.
        * `y`: The y-coordinate of the end point of the curve.

**Example for `quadraticCurveTo()`:**
```html
<canvas id="quadCanvas" width="300" height="150" style="border:1px solid #000;"></canvas>
<script>
    const canvas1 = document.getElementById('quadCanvas');
    const ctx1 = canvas1.getContext('2d');

    // Define points
    const start = { x: 50, y: 100 };
    const cp1 = { x: 150, y: 10 }; // Control point
    const end = { x: 250, y: 100 };

    // Draw the curve
    ctx1.beginPath();
    ctx1.moveTo(start.x, start.y);
    ctx1.quadraticCurveTo(cp1.x, cp1.y, end.x, end.y);
    ctx1.strokeStyle = 'blue';
    ctx1.lineWidth = 3;
    ctx1.stroke();

    // Visualize control point (optional)
    ctx1.fillStyle = 'red';
    ctx1.fillRect(cp1.x - 3, cp1.y - 3, 6, 6);
</script>
```

**2. `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)`**
   * **Purpose**: Draws a cubic Bézier curve. This type of curve is more complex and flexible, defined by a start point, an end point, and **two control points**.
   * **Parameters**:
        * `cp1x`: The x-coordinate of the first control point.
        * `cp1y`: The y-coordinate of the first control point.
        * `cp2x`: The x-coordinate of the second control point.
        * `cp2y`: The y-coordinate of the second control point.
        * `x`: The x-coordinate of the end point.
        * `y`: The y-coordinate of the end point.

**Example for `bezierCurveTo()`:**
```html
<canvas id="bezierCanvas" width="300" height="150" style="border:1px solid #000;"></canvas>
<script>
    const canvas2 = document.getElementById('bezierCanvas');
    const ctx2 = canvas2.getContext('2d');

    // Define points
    const start = { x: 50, y: 75 };
    const cp1 = { x: 100, y: 10 };  // First control point
    const cp2 = { x: 200, y: 140 }; // Second control point
    const end = { x: 250, y: 75 };

    // Draw the curve
    ctx2.beginPath();
    ctx2.moveTo(start.x, start.y);
    ctx2.bezierCurveTo(cp1.x, cp1.y, cp2.x, cp2.y, end.x, end.y);
    ctx2.strokeStyle = 'green';
    ctx2.lineWidth = 3;
    ctx2.stroke();

    // Visualize control points (optional)
    ctx2.fillStyle = 'red';
    ctx2.fillRect(cp1.x - 3, cp1.y - 3, 6, 6);
    ctx2.fillRect(cp2.x - 3, cp2.y - 3, 6, 6);
</script>
```
---
**9. a) Explain how to create Radial gradient in canvas with example.** (4 Marks)

A radial gradient in the HTML5 Canvas API creates a gradient pattern that radiates outwards from a central point. It is defined by two circles: a start circle and an end circle.

The process involves three main steps:
1.  **Create a Gradient Object**: Use the `createRadialGradient(x0, y0, r0, x1, y1, r1)` method of the 2D context.
    * `x0`, `y0`, `r0`: The x-coordinate, y-coordinate, and radius of the **start circle**.
    * `x1`, `y1`, `r1`: The x-coordinate, y-coordinate, and radius of the **end circle**.

2.  **Add Color Stops**: Use the `addColorStop(offset, color)` method on the newly created gradient object.
    * `offset`: A number between 0.0 (the start of the gradient) and 1.0 (the end).
    * `color`: The CSS color to use at that offset. You must add at least two color stops.

3.  **Apply and Draw**: Assign the gradient object to the `fillStyle` or `strokeStyle` property and then draw a shape (e.g., a rectangle) which will be filled or stroked with the gradient.

**Example:**
This code creates a radial gradient that transitions from yellow (center) to red to dark blue (outer edge) and fills a rectangle with it.
```html
<canvas id="myCanvas" width="300" height="200" style="border:1px solid #000;"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');

    // 1. Create the radial gradient object
    // Start circle: center(100, 100), radius 20
    // End circle:   center(120, 120), radius 100
    const radialGradient = ctx.createRadialGradient(100, 100, 20, 120, 120, 100);

    // 2. Add color stops
    radialGradient.addColorStop(0, 'yellow');      // Start color
    radialGradient.addColorStop(0.5, 'red');       // Middle color
    radialGradient.addColorStop(1, 'darkblue');    // End color

    // 3. Apply the gradient to the fill style
    ctx.fillStyle = radialGradient;

    // Draw a rectangle to be filled with the gradient
    ctx.fillRect(10, 10, 280, 180);
</script>
```
---
**9. b) List and explain all the Canvas shadow properties.** (4 Marks)

The HTML5 Canvas 2D API provides four properties to add drop shadows to shapes, text, or images drawn on the canvas. These properties must be set **before** the drawing operation is performed.

1.  **`shadowColor`**:
    * **Explanation**: This property sets the color of the shadow. The value can be any valid CSS color string (e.g., named color, hex, `rgb()`, `rgba()`). Using a semi-transparent `rgba()` color is common for a more realistic shadow.
    * **Default**: `rgba(0, 0, 0, 0)` (fully transparent black).
    * **Example**: `ctx.shadowColor = 'rgba(0, 0, 0, 0.5)';`

2.  **`shadowOffsetX`**:
    * **Explanation**: This property specifies the horizontal offset of the shadow from the shape, in pixels. A positive value shifts the shadow to the right, and a negative value shifts it to the left.
    * **Default**: `0`.
    * **Example**: `ctx.shadowOffsetX = 5;`

3.  **`shadowOffsetY`**:
    * **Explanation**: This property specifies the vertical offset of the shadow from the shape, in pixels. A positive value shifts the shadow downwards, and a negative value shifts it upwards.
    * **Default**: `0`.
    * **Example**: `ctx.shadowOffsetY = 5;`

4.  **`shadowBlur`**:
    * **Explanation**: This property specifies the amount of blur to apply to the shadow. It uses a Gaussian blur effect. A value of `0` means no blur (a sharp shadow), and larger values create a more blurred, softer shadow.
    * **Default**: `0`.
    * **Example**: `ctx.shadowBlur = 10;`

**Code Snippet Example:**
```javascript
const ctx = canvas.getContext('2d');

// Set shadow properties
ctx.shadowColor = 'black';
ctx.shadowBlur = 8;
ctx.shadowOffsetX = 4;
ctx.shadowOffsetY = 4;

// All subsequent drawings will have this shadow
ctx.fillStyle = 'cornflowerblue';
ctx.fillRect(50, 50, 150, 75);
```

---

**9. c) Explain `arc()` and `arcTo()` methods of canvas.** (4 Marks)

Both `arc()` and `arcTo()` are used to draw arcs on a canvas, but they are defined by different parameters and are used for different purposes.

**1. `arc(x, y, radius, startAngle, endAngle, [anticlockwise])`**
   * **Purpose**: This method is used to draw a circular arc or a complete circle. It is defined by a center point, a radius, and start/end angles.
   * **Parameters**:
        * `x`, `y`: The coordinates of the center of the circle.
        * `radius`: The radius of the circle.
        * `startAngle`, `endAngle`: The starting and ending angles of the arc, measured in **radians** (not degrees). 0 radians is at the 3 o'clock position.
        * `anticlockwise` (Optional): A boolean value. If `true`, the arc is drawn counter-clockwise; otherwise, it is drawn clockwise (default).
   * **Use Case**: Drawing circles, semi-circles, or pie chart segments.

**Example (`arc()`):**
```javascript
// Draws a semi-circle
ctx.beginPath();
ctx.arc(150, 75, 50, 0, Math.PI, false); // Math.PI is 180 degrees
ctx.stroke();
```

**2. `arcTo(x1, y1, x2, y2, radius)`**
   * **Purpose**: This method draws an arc with a given radius that fits between two tangent lines. It is primarily used to create **rounded corners**. The arc is connected to the current pen position by a straight line.
   * **Parameters**:
        * `x1`, `y1`: The coordinates of the first control point (the corner where the two tangent lines would meet).
        * `x2`, `y2`: The coordinates of the second control point (the end point of the second tangent line).
        * `radius`: The radius of the arc.
   * **How it works**: It draws a line from the current point to the start of the arc, and then the arc itself. The arc is tangent to the line from `(current_point)` to `(x1, y1)` and the line from `(x1, y1)` to `(x2, y2)`.
   * **Use Case**: Drawing shapes with rounded corners, like a rounded rectangle.

**Example (`arcTo()`):**
```javascript
// Draws a path with a single rounded corner
ctx.beginPath();
ctx.moveTo(20, 20);         // Start point
ctx.lineTo(120, 20);        // Line to first control point's x
ctx.arcTo(170, 20, 170, 70, 20); // Create rounded corner with radius 20
ctx.lineTo(170, 120);       // Continue the path
ctx.stroke();
```

